# Cookie Cloud
> Get cookie through Tampermonkey, use cookie anywhere.


Get all Cookies even HttpOnly Cookies.

## INSTALL
`pip install cookie-cloud`

## USAGE

### 1. Generate Tampermonkey script

```
$ cc_generate
Generated .cookie_cloud.json file successed.
You can move it to HOME.
Edit it!

$ vim .cookie_cloud.json
{
    "github_user": "twb",
    "github_repo": "cookie",
    "github_token": "XXXX",
    "sites": [
        "github.com"
    ]
}

$ cc_generate
Generate GYC.js file successed.
Copy that to your Tampermonkey!
```

- github_user: save cookies's repo owner 
- github_repo: save cookies's repo name
- github_token: github token
- sites: get cookie sites

### 2. Enable Tampermonkey script

Add [Tampermonkey](https://www.tampermonkey.net/) to your browser, then create Tampermonkey script and parse `GYC.js` content, last enable it.

### 3. Open one of your sites in your browser
The Tampermonkey script while create repo and log opearations in your console.

### 4. Use it anaywhere
> Read config from `.cookie_cloud.json` or `~/.cookie_cloud.json`

Example:

```Python
>>> from cookie_cloud.util import get_cookie
>>> cookie = get_cookie('github.com', update=False, raw=False)
```
Argument:
- update
  - `True`: get cookies by request
  - `False`: load cookies from '/tmp/cookies.json' or 'C:\temp\cookies.json'

- raw:
  - `True`: json type cookie, same as issue comment body
  - `False`: string type cookie, can be used by `requests.get(url, headers={"Cookie"=cookie})`.

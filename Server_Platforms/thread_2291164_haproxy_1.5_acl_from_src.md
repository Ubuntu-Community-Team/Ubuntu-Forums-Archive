---
title: "haproxy 1.5 acl from src"
date: 2015-08-18
forum: Server Platforms
---

### Post by badbunny2 on 2015-08-18
I'm currently on haproxy 1.5 and want to set up some acls checking if a cookie is set and if hosts are coming from an internal subnet.
redirect if no cookie is set works just fine. But skip the redirection for hosts which are from an internal IP seems never to match.

```
frontent application
bind 192.168.50.100
acl is_root -i /
redirect prefix http://intranet.example.com/sub/page/index.htm if is_root
acl is_intranet url_reg ^\/sub/page/intranet*
acl is_old_intranet url_reg ^\/sub/old/intranet*
acl is_internal src 192.168.50.0/24
acl is_cookie-sso hdr_reg(cookie) exampleSSO=.+
redirect location http://intranet.example.com/404.html if is_old_intranet #working
redirect location http://sso.example.com/Login.aspx?RedirectUrl=http://intranet.example.com if !is_cookie_sso is_intranet !is_old_intranet !is_internal #working but still redirects for hosts from 192.168.50.0/24 network
use backend application
```

what could I change in this config, to never redirect internal hosts to sso.example.com?

---


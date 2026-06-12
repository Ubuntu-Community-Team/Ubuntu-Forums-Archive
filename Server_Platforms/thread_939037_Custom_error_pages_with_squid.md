---
title: "Custom error pages with squid"
date: 2008-10-05
forum: Server Platforms
---

### Post by Proot on 2008-10-05
Hi All

I've setup squid (2.6-18 stable) on a base install of Ubuntu 8.04 server, however I'm having troubles getting custom error pages to work.

Part of my squid.conf file is shown
```

acl bad url_regex "/etc/squid/squid-block.acl"
#deny_info ERR_BLOCKED_WORKTIME bad
http_access deny bad

```
With this in the config it works fine, the site in the squid-block.acl file is blocked and the default access denied error is shown. However, if I uncomment the second line I can't browse to any pages.
```

#deny_info ERR_BLOCKED_WORKTIME bad

```
The file ERR_BLOCKED_WORKTIME is in the directory /usr/local/share/squid/errors/English and has only plain text in it, no html.

**Can anyone shed any light on this?**

I've attached my full config, minus comments, using the command 
```
egrep -v '(^[ \t]*#|^[ \t]*$)' /etc/squid/squid.conf

```

---


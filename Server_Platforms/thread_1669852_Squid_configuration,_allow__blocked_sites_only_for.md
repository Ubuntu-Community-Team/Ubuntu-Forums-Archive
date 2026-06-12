---
title: "Squid configuration, allow  blocked sites only for 2 users"
date: 2011-01-18
forum: Server Platforms
---

### Post by Zitan on 2011-01-18
My Squid is working. But I do not know how to unblock a proxy for two users on my network. My  configuration
```

acl work src 192.168.16.0/24
acl sites dstdomain "/etc/squid/sites.acl"
acl files urlpath_regex "/etc/squid/files.acl"
acl boss src 192.168.16.12
acl it_user src 192.168.16.5
http_access deny files
http_access deny sites
http_access allow files it_user
http_access allow files boss
http_access allow sites it_user
http_access allow sites boss
http_access allow work

```

How to enable blocked sites and files for boss and it_user?

---

### Post by SeijiSensei on 2011-01-18
Remove the "files" and "sites" from the "boss" and "it_user" rules and just use:

```

acl work src 192.168.16.0/24
acl sites dstdomain "/etc/squid/sites.acl"
acl files urlpath_regex "/etc/squid/files.acl"
acl boss src 192.168.16.12
acl it_user src 192.168.16.5
http_access allow it_user
http_access allow boss
http_access deny files
http_access deny sites
http_access allow work

```
Note that I've put the "allow" rules first.  In general, you want to put all the whitelist rules above the blacklist ones.  Otherwise the blacklist rules will take precedence.

---

### Post by Zitan on 2011-01-19
Everything is working now, thank you.

---


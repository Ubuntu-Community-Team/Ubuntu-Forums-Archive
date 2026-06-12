---
title: "MySQL charset related errors"
date: 2006-02-16
forum: Server Platforms
---

### Post by Turnip on 2006-02-16
Hi,

I am running mysql-server-4.1 and get a lot of the following errors popping up in my Apache error logs:

```
Character set '#33' is not a compiled character set and is not specified in the '/usr/share/libmysqlclient/charsets/Index' file
File '/usr/share/libmysqlclient/charsets/?.conf' not found (Errcode: 2)
```

For what it's worth I'm using character-set-server=utf8 in my configuration file. This doesn't cause me too much problem at home but at work I have set up a PureFTPD server which authenticates using MySQL. When I try to login to it I get these errors returned as the response and cannot login at all. So that is more of a problem. If anybody has any ideas I'd much appreciate it. For a start I don't know where the reference to /usr/share/libmysqlclient/* is coming from as that directory does not exist.

Thanks

---


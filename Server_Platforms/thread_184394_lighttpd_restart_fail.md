---
title: "lighttpd restart fail"
date: 2006-05-29
forum: Server Platforms
---

### Post by utopyr on 2006-05-29
I've started trying lighttpd this weekend, since a package I want to use, [Leonardo]("http://leonardo.pyworks.org/") , seems easier to configure the way I want with that instead of apache2. However, after I've edited the configuration file for lightppd, and I try to restart it with
```
sudo /etc/init.d/lightppd restart
``` 
or any of the variations available, such as stop, start, or force-reload, I get a note saying it's failed.

I installed from the Dapper repositories; the version is 
```
lighttpd-1.4.11 (ssl) - a light and fast webserver
Build-Date: May 11 2006 00:31:57

```

I've checked the error logs, but nothing shows up there.

---


---
title: "Access problem with Apache on 14.04"
date: 2014-10-29
forum: Server Platforms
---

### Post by cearlp on 2014-10-29
After an initial install of 14.04, and going through the steps of installing a LAMP stack (which seemed to succeed) trying to access localhost as the URL in Firefox fails with a Forbidden error. Apache/2.4.7 doesn't have permission to access / on this server.
Are there some permissions I need to change on certain directories?

---

### Post by cariboo on 2014-10-29
Is apache running?

```
ps ax | grep apache2
```

---

### Post by cearlp on 2014-10-29
Yes, after changing the Default Root in the .conf file to /var/www instead of /var/www/html since I had a lot of my own .html files there I did a apache2 restart.

---


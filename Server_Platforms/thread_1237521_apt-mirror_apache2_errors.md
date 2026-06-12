---
title: "apt-mirror apache2 errors"
date: 2009-08-11
forum: Server Platforms
---

### Post by awreneau on 2009-08-11
Recently setup an apt-mirror for Jaunty and I successfully download packages to be installed on test box.

Reviewing log files on apt-mirror server I found the following in /var/log/apache2/error.log

> File does not exist: /var/www/ubuntu/dists/jaunty/restricted/i18n

Not much to indicate why. From what I've seen i18n is all about internationalisation, which, in this case is irrelevant and can safely be ignored.

Would like someone to offer explanation if possible. If in fact it's not required is there a way to disable this from being required/searched for by apt-get?  I like clean error.logs :)

---


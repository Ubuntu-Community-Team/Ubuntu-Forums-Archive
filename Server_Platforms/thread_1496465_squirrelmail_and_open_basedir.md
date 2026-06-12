---
title: "squirrelmail and open_basedir"
date: 2010-05-29
forum: Server Platforms
---

### Post by pht3k on 2010-05-29
hi,
since my latest apt-get update and upgrade, i have an error when trying to connect to squirrelmail and some pages from my webserver.
here's the error message from squirrelmail:
```

Warning: require_once() [function.require-once]: open_basedir restriction in effect. File(../functions/global.php) is not within the allowed path(s): (.) in /usr/share/squirrelmail/src/login.php on line 25

Warning: require_once(../functions/global.php) [function.require-once]: failed to open stream: Operation not permitted in /usr/share/squirrelmail/src/login.php on line 25

Fatal error: require_once() [function.require]: Failed opening required '../functions/global.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/squirrelmail/src/login.php on line 25

```
i looked at php.ini and open_basedir is commented. so i dont understand what is going on. any idea?
thanks,
pht3k

---

### Post by pht3k on 2010-05-31
anyone?

---


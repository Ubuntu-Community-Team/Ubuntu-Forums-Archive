---
title: "torrentflux"
date: 2010-04-03
forum: Server Platforms
---

### Post by austclint on 2010-04-03
Have installed torrentflux on a ubuntu 9.10 server, everying seemed to install fine but when i bring it up on the web page ([http://192.168.1.7/torrentflux/](http://192.168.1.7/torrentflux/)) I get the```

Warning: include_once(/etc/torrentflux/config-db.php) [function.include-once]: failed to open stream: Permission denied in /usr/share/torrentflux/www/config.php on line 35

Warning: include_once() [function.include]: Failed opening '/etc/torrentflux/config-db.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/torrentflux/www/config.php on line 35

Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /usr/share/torrentflux/www/config.php:35) in /usr/share/torrentflux/www/functions.php on line 27

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /usr/share/torrentflux/www/config.php:35) in /usr/share/torrentflux/www/functions.php on line 27

ADONewConnection: Unable to load database driver ''

Fatal error: Call to a member function Connect() on a non-object in /usr/share/torrentflux/www/db.php on line 13
```

I have tried changing the permisson, but no luck

---

### Post by austclint on 2010-04-03
sorry, error on my behalf, did chd 777, instead of 744

---


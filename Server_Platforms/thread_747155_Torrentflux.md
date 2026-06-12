---
title: "Torrentflux"
date: 2008-04-06
forum: Server Platforms
---

### Post by chrisbish on 2008-04-06
im trying to set up torrent flux but i get this error


> Warning: mysql_connect() [function.mysql-connect]: Lost connection to MySQL server at 'reading initial communication packet', system error: 111 in /var/www/torrents/adodb/drivers/adodb-mysql.inc.php on line 355


Database error: Lost connection to MySQL server at 'reading initial communication packet', system error: 111

Always check your database variables in the config.php file.


---

### Post by chrisbish on 2008-04-07
i fixed this in the end

---


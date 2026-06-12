---
title: "secure apache"
date: 2006-11-08
forum: Server Platforms
---

### Post by bunnynuts on 2006-11-08
Running 6.06 Default Lamp server

While viewing my access.log in apache2 I came across the following:

"GET /phpmyadmin/main.php HTTP/1.1" 401 476 "-" "-"
"GET /PMA/main.php HTTP/1.1" 401 476 "-" "-"
"GET /mysql/main.php HTTP/1.1" 401 476 "-" "-"
"GET /admin/main.php HTTP/1.1" 401 476 "-" "-"
"GET /db/main.php HTTP/1.1" 401 476 "-" "-"
"GET /dbadmin/main.php HTTP/1.1" 401 476 "-" "-"
"GET /web/phpMyAdmin/main.php HTTP/1.1" 401 476 "-" "-"
"GET /admin/pma/main.php HTTP/1.1" 401 476 "-" "-"
"GET /admin/phpmyadmin/main.php HTTP/1.1" 401 476 "-" "-"
"GET /admin/mysql/main.php HTTP/1.1" 401 476 "-" "-"
"GET /phpmyadmin2/main.php HTTP/1.1" 401 476 "-" "-"
"GET /mysqladmin/main.php HTTP/1.1" 401 476 "-" "-"
"GET /mysql-admin/main.php HTTP/1.1" 401 476 "-" "-"
"GET /main.php HTTP/1.1" 401 476 "-" "-"
"GET /phpMyAdmin-2.5.6/main.php HTTP/1.1" 401 476 "-" "-"
"GET /phpMyAdmin-2.5.4/main.php HTTP/1.1" 401 476 "-" "-"
"GET /phpMyAdmin-2.5.1/main.php HTTP/1.1" 401 476 "-" "-"
"GET /phpMyAdmin-2.2.3/main.php HTTP/1.1" 401 476 "-" "-"
"GET /phpMyAdmin-2.2.6/main.php HTTP/1.1" 401 476 "-" "-"
"GET /myadmin/main.php HTTP/1.1" 401 476 "-" "-"
"GET /phpMyAdmin-2.6.0/main.php HTTP/1.1" 401 476 "-" "-"
"GET /phpMyAdmin-2.6.0-pl1/main.php HTTP/1.1" 401 476 "-" "-"
"GET /phpMyAdmin-2.6.3-pl1/main.php HTTP/1.1" 401 476 "-" "-"
"GET /phpMyAdmin-2.6.3/main.php HTTP/1.1" 401 476 "-" "-"
"GET /phpMyAdmin-2.6.3-rc1/main.php HTTP/1.1" 401 476 "-" "-"
"GET /phpMyAdmin-2.6.2-rc1/main.php HTTP/1.1" 401 476 "-" "-"

All originating from the same IP.

I've had the single attempt to get in such as:

"POST /_vti_bin/_vti_aut/author.dll HTTP/1.1" 401 476 "-" "core-project/1.0"

This obviously didn't work, but I haven't run into more than that.

I've already taken the following steps: iptables only allow certain IPs to access MySQL, and I've installed mod_security, with a default configuration that I haven't fully investigated yet. I upgrade/update from the repositories often.

What else is advisable to secure my web server? Are there certain rules in mod_sec that I should ensure are enabled? 
The phpMyAdmin part has me worried as I don't know much about that.

Also, how might I ban an IP from making so many attempts? I am teaching myself iptables (oh so slowly) and believe that is the preferred route, but what would the rule look like?

Thank you for your help

---

### Post by MJN on 2006-11-08
As the user agent signifies (along with the ordered list of access requests) it is the work of the so-called 'pmafind' bot.

If you're running up-to-date services, and use strong passwords, then the 'attacks' should be nothing to worry about.

Mathew

---


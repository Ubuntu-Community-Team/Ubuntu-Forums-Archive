---
title: "[SOLVED] usn-2254-1 php fpm permission changes to 0660 + nginx = 502 bad gateway"
date: 2014-06-23
forum: Security
---

### Post by SMANN on 2014-06-23
Todays PHP security patches [USN-2254-1]("http://www.ubuntu.com/usn/usn-2254-1/") contain updates for [CVE-2014-0185]("http://people.canonical.com/~ubuntu-security/cve/2014/CVE-2014-0185.html")  which changes unix socket permissions from 0666 to 0660.  I'm running 12.04 w/ nginx 1.19 + php5-fpm on a socket located at /var/run/php5-fpm.sock.  After applying this patch any calls to my php stuff will result in 502 Bad Gateway errors.  

During install I used the new configuration file (/etc/php5/fpm/pool.d/www.conf) and then manually updated it to point to my socket with listen = /var/run/php5-fpm.sock.  A diff of this file shows the only changes being the language regarding the permissions now being set to 0660 rather than 0666.  Restarting php5-fpm shows the socket in /var/run with permissions 0660 yet any calls to php result in 502 errors.  If I override the default and set the socket permissions back to 0666 w/ listen.mode = 0666 everything works again.

Looking for advice on how to make nginx+php5-fpm work correctly w/ the socket permissions set to 0660 or any suggestions on what is causing this to break.

---

### Post by SMANN on 2014-06-23
Solved.  In /etc/php5/fpm/pool.d/www.conf the new default config is:

;listen.owner = www-data
;listen.group = www-data
;listen.mode = 0660

Previously I had just uncommented listen.mode = 0660.  When that didn't work I set it to listen.mode = 0666 and that did work.  I eventually tried uncommenting all three lines and for whatever reason that works fine. In short, previously [www.conf]("http://www.conf") didn't seem to require that owner and group be uncommented but after this patch it seems all three lines listen.owner, listen.group and listen.mode need to be uncommented for the socket to run as 0660.

---


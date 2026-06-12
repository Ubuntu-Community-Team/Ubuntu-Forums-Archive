---
title: "Munin error 403"
date: 2015-01-06
forum: Server Platforms
---

### Post by luca26 on 2015-01-06
hello everyone,
I have a server with ubuntu 14:04, I installed munin, but when I type ServerIP/munin (from my pc) gives me 403 error ... I tried google with possible solutions (using apache 2.4) and following this page [http://stackoverflow.com/questions/9127802/munin-server-with-apache-you-dont-have-permission-to-access-munin-on-this-se](http://stackoverflow.com/questions/9127802/munin-server-with-apache-you-dont-have-permission-to-access-munin-on-this-se) I made the changes recommended ...


but it keeps giving me error 403 ... how do I fix?
thanks a lot
Sorry for my bad english!
Luca

PS: error.log:
AH01630: client denied by server configuration: /var/cache/munin/www/

---

### Post by luca26 on 2015-01-06
SOLVED

edit file /etc/munin/apache24.conf 

and

edit line Require

with

Require all granted

---


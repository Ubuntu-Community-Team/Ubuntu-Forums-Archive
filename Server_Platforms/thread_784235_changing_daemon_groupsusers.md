---
title: "changing daemon groups/users"
date: 2008-05-06
forum: Server Platforms
---

### Post by baggus on 2008-05-06
Hi all,

I have this situation where i have to delete files created by the apache user (www-data) through my ftp server PureFTPd (the mysql one, installed according to [this]("http://www.howtoforge.com/virtual-hosting-with-pureftpd-and-mysql-ubuntu-7.10") tutorial).

I throught the best way for me to be able to do this would be to make either the ftp server run as www-data or the web server to run as ftpuser.

Thing is, i have looked everywhere without being able to find anything usefull on this. :confused:

Maybe there is someone here who is prepared to lend me a hand?

(no i am not planning to just chmod 666 -R /var/www/ :P)

Many thanks in advance!

---

### Post by baggus on 2008-05-06
oh and if you know for sure that this isn't going to work, please tell me aswell, that would save me alot of time and effort

---


---
title: "php-apc not working &quot;uptime 0 minutes&quot;"
date: 2010-12-20
forum: Server Platforms
---

### Post by dlublink on 2010-12-20
I am running Ubuntu server 10.04 LTS ( tested both on 32bit and 64bit processor ).

I installed php-apc, but it always says "uptime 0 minutes". I looked at about 50 different pages on google and did not find an answer.

Why is the "uptime" always at 0 minutes? I suspected apparmor, so I disabled it ( /etc/init.d/apparmor stop ) and checked the logs ( no mention of PHP other than refusal to see cpu in proc ).

What is stopping APC from working properly? I see it in phpinfo(). 

THanks,
David

---

### Post by dlublink on 2010-12-20
Turns out that I need to use fastcgi in my lighttpd for php-apc to work.

---


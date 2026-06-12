---
title: "php4 problem"
date: 2006-02-15
forum: Server Platforms
---

### Post by hmunoz on 2006-02-15
I am having this error
Subject: Cron <root@mail> /usr/bin/php4 -q -c /etc/php4/syscpcron /var/www/syscp/scripts/cronscript.php
X-Cron-Env: <PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <LOGNAME=root>
Message-Id: <20060215143001.7FC0E20EFE3@mail.domain.com>
Date: Wed, 15 Feb 2006 10:30:01 -0400 (AST)

/bin/sh: /usr/bin/php4: No such file or directory


I dont have php4 on /usr/bin/ 
I was running the same script on Debian and it was working fine

Could someone help me????????

thanks

---

### Post by grinchy on 2006-02-15
find out where your php binary is

locate php | less

---

### Post by hmunoz on 2006-02-15
Thanks for reply grinchy
thats my problem I cant found php4 bin
Im looking for the php bin on my ubuntu 5.10 and I cant found it

---


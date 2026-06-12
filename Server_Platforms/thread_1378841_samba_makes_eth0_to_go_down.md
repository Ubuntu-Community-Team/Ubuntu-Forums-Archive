---
title: "samba makes eth0 to go down"
date: 2010-01-11
forum: Server Platforms
---

### Post by maximitron on 2010-01-11
Hello everybody!!

First of all, this is my 1st post in this forum.

I'm using ubuntu 9.10 x86 server edition and I switched to Ubuntu from Debian. The only problem I have now relates my Samba server. 

I installed Samba v 3.4.0 and suddently my network connection (eth0) goes down. I have never seen that before. This issue only happens when samba is running.

Configs and logs can be supplied as needed.
Thanks!!

---

### Post by cariboo on 2010-01-11
Is there anything in /var/log/samba, that may indicate a problem?

---

### Post by maximitron on 2010-01-11
Mhmmm, there's a bunch of logs on /var/log/samba xD

drwx------ 5 root    4096 2010-01-10 14:16 cores
-rw-r--r-- 1 root    5860 2010-01-11 11:31 log.0.0.0.0
-rw-r--r-- 1 root       0 2010-01-11 19:42 log.alpha
-rw-r--r-- 1 root  194066 2010-01-11 22:58 log.delta
-rw-r--r-- 1 root       0 2010-01-10 14:27 log.172.28.0.4
-rw-r--r-- 1 root   32630 2010-01-11 22:26 log.gamma
-rw-r--r-- 1 root   12820 2010-01-11 22:26 log.kappa
-rw-r--r-- 1 root    2175 2010-01-11 10:50 log.localhost
-rw-r--r-- 1 root   26385 2010-01-11 22:57 log.smbd
-rw-r--r-- 1 root     230 2010-01-10 15:23 log.wb-ALPHA
-rw-r--r-- 1 root    1380 2010-01-11 22:10 log.wb-BUILTIN
-rw-r--r-- 1 root    9555 2010-01-11 22:24 log.wb-HIGHFSB
-rw-r--r-- 1 root   18577 2010-01-11 22:24 log.winbindd
-rw-r--r-- 1 root       0 2010-01-10 14:49 log.winbindd-dc-connect
-rw-r--r-- 1 root  493326 2010-01-11 22:57 log.winbindd-idmap
-rw-r--r-- 1 root 1025401 2010-01-11 05:39 log.winbindd-idmap.old

I'm looking my logs too.

---

### Post by maximitron on 2010-01-12
I found the problem: it was a h/w problem. I figured out that the system stopped to work completely

Thanks anyway

---


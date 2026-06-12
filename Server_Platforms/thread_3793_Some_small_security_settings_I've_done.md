---
title: "Some small security settings I've done"
date: 2004-11-09
forum: Server Platforms
---

### Post by ubuntu_demon on 2004-11-09
Hi,

I've done some small security settings I think are important to do.

sudo find / -type f -perm 6000 -ls

finds programs that have the s bit set. I discoverd a lot of games had this bit set. I removed the s bit from them.

I have two ext3 partitions for ubuntu : / and /home
I set /home to : defaults,nosuid,nodev in /etc/fstab

chattr +i /bin/login (chattr -i /bin/login if there is an security update for it)

chmod 751 /var/log /etc/logrotate.d
chmod 640 /etc/syslog.conf /etc/logrotate.conf
chmod 640 /var/log/*.log

chmod -s /bin/at (users can use crontab)

What do you guys think ?

---

### Post by ubuntu_demon on 2004-11-12
*bump*

---

### Post by ubuntu_demon on 2004-11-16
I got the email :

/etc/cron.weekly/sysklogd:
ln: creating hard link `/var/log//messages.0' to `/var/log/messages': Operation
+not permitted
Error hardlinking /var/log/messages to /var/log//messages.0
run-parts: /etc/cron.weekly/sysklogd exited with return code 8


===

I've decided it's not worth the trouble to do these minor secuirty settings :

chmod 751 /var/log /etc/logrotate.d
chmod 640 /etc/syslog.conf /etc/logrotate.conf
chmod 640 /var/log/*.log

---


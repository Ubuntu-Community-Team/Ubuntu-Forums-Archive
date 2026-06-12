---
title: "Bind Permission error in zones files"
date: 2008-05-10
forum: Server Platforms
---

### Post by MAO on 2008-05-10
Hi i've got some problems with bind Zones Files:

root@sw:/# tail -f /var/log/daemon.log
May 10 20:05:51 sw named[4705]: command channel listening on ::1#953
[COLOR="Red"]May 10 20:05:51 sw named[4705]: could not open entropy source /dev/random: permission denied[/COLOR]
May 10 20:05:51 sw named[4705]: using pre-chroot entropy source /dev/random
May 10 20:05:51 sw named[4705]: zone 0.in-addr.arpa/IN: loaded serial 1
May 10 20:05:51 sw named[4705]: zone 127.in-addr.arpa/IN: loaded serial 1
[COLOR="#ff0000"]May 10 20:05:51 sw named[4705]: zone 22.29.217.in-addr.arpa/IN: loading from master file /etc/bind/zones/rev.22.29.217.in-addr.arpa failed: permission denied[/COLOR]
May 10 20:05:51 sw named[4705]: zone 255.in-addr.arpa/IN: loaded serial 1
[COLOR="#ff0000"]May 10 20:05:51 sw named[4705]: zone software.kg/IN: loading from master file /etc/bind/zones/software.kg.db failed: permission denied[/COLOR]
May 10 20:05:51 sw named[4705]: zone localhost/IN: loaded serial 2
May 10 20:05:51 sw named[4705]: running

____________________________________

root@sw:/# ls -la /var/lib/named/etc/bind/zones
total 16
drwxr-sr-x 2 bind bind 4096 2008-05-10 19:45 .
drwxr-sr-x 3 bind bind 4096 2008-05-10 19:47 ..
-rwxrwxrwx 1 bind bind 260 2008-05-10 19:45 rev.22.29.217.in-addr.arpa
-rwxrwxrwx 1 bind bind 651 2008-05-10 19:54 software.kg.db

Plz Help me !!!

---

### Post by MAO on 2008-05-10
Server ubuntu 8.04 bind configurations takes from howtoforge.org manual!

---

### Post by MAO on 2008-05-11
someone plz help !!!

---


---
title: "ubuntu server partition"
date: 2009-05-20
forum: Server Platforms
---

### Post by salim.madni on 2009-05-20
dear gurus

i install a fresh ubuntu 8.10 server. during this

i give 3 partition to made

/ swap partition
/ root partition
/var/opt/axigen

but after installation when i check i found extra partition are there by default, what could be wrong. is there something additional or missing i have done

see results below

test@ksa1:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              23G  647M   22G   3% /
tmpfs                 504M     0  504M   0% /lib/init/rw
varrun                504M  272K  504M   1% /var/run
varlock               504M     0  504M   0% /var/lock
udev                  504M  2.8M  502M   1% /dev
tmpfs                 504M     0  504M   0% /dev/shm
/dev/sda3              46G  180M   44G   1% /var/opt/test

regards
salim

---

### Post by BadBoy4Live on 2009-05-20
The extra partition that where created a nessecary for the system to run optimal. these are made on every clean installation.

Greetz,
Badboy4live

---

### Post by salim.madni on 2009-05-22
any specfic reason for this

since we used slacware,centos,redhat,fedora...but they never do it.

kindly can some one provide docmuentation,articles,tutorial links.

what are pros and crons and system create automaticaly these partitions

i do have seen first time

kind regards
salim

---

### Post by nandemonai on 2009-05-22
They're just virtual partitions for stuff like tmp and udev. Nothing to worry about. They're not 'real' partitions on your hard disk.

---


---
title: "&quot;No space left on device&quot; in a almost empty ext3 partition"
date: 2008-04-04
forum: Server Platforms
---

### Post by AleSanchez on 2008-04-04
Hi everyone, this is my first post. 
I'm having this problem in two different installations of Ubuntu 6.06.2 LTS x86_64 (fully updated) in two exact hardware servers.

This is my df -h:

```

root@mail:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              38G  770M   35G   3% /
varrun               1004M   84K 1004M   1% /var/run
varlock              1004M  4,0K 1004M   1% /var/lock
udev                 1004M   68K 1004M   1% /dev
devshm               1004M     0 1004M   0% /dev/shm
/dev/sda3              74G  3,9G   67G   6% /var
/dev/sdb1             294G  1,1G  278G   1% /media/hd

```
The partition that gives me the error is /dev/sda1, in any random circumstances. Postfix, Apache, or even trying to upgrade via aptitude can give me the error. 

If I delete some files from the partition, the error stops. 

So, I think this is not really a matter of space. Maybe it's a matter of the quantity of files that are stored in the partition. 

Sounds it coherent? 


Regards, 
Alejandro.

---

### Post by dendrobates on 2008-04-04
could you be running out if inodes?

What does 'df -i' show.

It would be unusual, but possible if you had billions of very small files in the partition for some reason.

---

### Post by AleSanchez on 2008-04-05
I think you're right, look:

```

Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1              38272   34545    3727   91% /
varrun                256934      42  256892    1% /var/run
varlock               256934       4  256930    1% /var/lock
udev                  256934     826  256108    1% /dev
devshm                256934       1  256933    1% /dev/shm
/dev/sda3              75392    3314   72078    5% /var
/dev/sdb1            39075840   50388 39025452    1% /media/hd

```


¿How can I fix this?
Thanks.

---

### Post by zackboarman on 2008-04-05
to the best of my knowledge, the number of inodes are set when the partiton was made, which sence it's root, that was at install time, and if you used the alternative cd to install it, once you get to the partitoning stage, there's 4 modes to chose from that controls the number of inodes present, depending upon what you chose. but I don't know of any way to change it, other than reformating the partiton. but then again, there might be.

But if you reformate it, then back everything up & from a live cd type:

mkfs.ext3 -N (number of inodes you want) /dev/sda1

then mount that partiton & copy all the files back.

hopes this helps out any.

---


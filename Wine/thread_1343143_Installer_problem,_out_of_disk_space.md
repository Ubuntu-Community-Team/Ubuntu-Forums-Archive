---
title: "Installer problem, out of disk space"
date: 2009-12-01
forum: Wine
---

### Post by Koraq on 2009-12-01
I have been trying to install a few old games, and none seem work. the problem, the latest time when I tried to install Deathtrap Dungeon, was that it looks like I'm running out of disk space. I have plenty of disk.

When I start the installer and choose where to install I choose C or Z or any other disk. The installer tell me how much space is needed, and how much is available and I have plenty of space. Then when the three classic InstallShield meters show up they indicate that I have very little disk space left. The installer starts copying and quite soon it stops with the message:

An error occured during the move data process:-117 

Google don't give anything useful when searching on that message.

Why do I run out of space??

Ubuntu version:
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty

wine version:
1.0.1-0ubuntu6, latest package

```

ls -l .wine
total 512
drwxr-xr-x 2 ante ante   4096 2009-12-01 13:18 dosdevices/
drwxr-xr-x 4 ante ante   4096 2009-12-01 13:18 drive_c/
-rw-r--r-- 1 ante ante 467518 2009-12-01 13:21 system.reg
-rw-r--r-- 1 ante ante   2346 2009-12-01 13:19 userdef.reg
-rw-r--r-- 1 ante ante  33924 2009-12-01 13:20 user.reg

```

```

ls -l .wine/dosdevices/
total 0
lrwxrwxrwx 1 ante ante 10 2009-12-01 13:18 c: -> ../drive_c/
lrwxrwxrwx 1 ante ante  1 2009-12-01 13:18 d: -> //
lrwxrwxrwx 1 ante ante 21 2009-12-01 13:18 z: -> /home/ante/Spel/Wine//

```

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             139G   98G   35G  75% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  284K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  164K  1.9G   1% /dev
tmpfs                 1.9G   12K  1.9G   1% /dev/shm
lrm                   1.9G  2.5M  1.9G   1% /lib/modules/2.6.28-16-generic/volatile
/dev/loop3            242M  242M     0 100% /mnt
```

---

### Post by Koraq on 2009-12-02
bump

---

### Post by Koraq on 2009-12-04
nobody?

---

### Post by 8Kuula on 2009-12-04
For starters, update Wine to 1.1.33 version (latest development version atm.), that 1.0.1 stable is so so so old.

---

### Post by Koraq on 2009-12-09
But, I have the wine package updated to the latest there is. How do I find a package for that development version?

---

### Post by anaconda on 2009-12-09
[https://edge.launchpad.net/+help/soyuz/ppa-sources-list.html](https://edge.launchpad.net/+help/soyuz/ppa-sources-list.html)
[https://edge.launchpad.net/~ubuntu-wine/+archive/ppa](https://edge.launchpad.net/~ubuntu-wine/+archive/ppa)

Just add the wine repository, and then you can update wine to the newest version...

---

### Post by Koraq on 2009-12-09
I upgraded and I still get the same error.

---


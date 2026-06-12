---
title: "Incorrect disk space"
date: 2010-01-07
forum: Wine
---

### Post by DrSeptapus on 2010-01-07
I am trying to install Fallout under wine in Ubuntu 9.10. initially i had tried it with 1.1.27 because that was what i was using for Fallout 2. I have the option of going with a small, medium, large, or HUMONGOUS install. Naturally i want to go with the HUMONGOUS install for faster loading and the fact i don't need to mount the iso everytime i play, problem is that it requires about 600 MB of space and apparently i only 200 MB of free space when in actuality i have about 130 GB. I tried 1.1.35 which got a platinum rating and the only thing that changed was that it said i had a different amount of space free (same issue with 1.0.1, different free disk space). I uninstalled wine deleted the .wine directory and reinstalled. Same problem. 

df -h showed me

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             356G  207G  131G  62% /
udev                  2.0G  276K  2.0G   1% /dev
none                  2.0G  272K  2.0G   1% /dev/shm
none                  2.0G  196K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
none                  356G  207G  131G  62% /var/lib/ureadahead/debugfs
/dev/loop0            630M  630M     0 100% /mnt


```
Is there anything i can do? Any help will be appreciated.

---

### Post by gsmanners on 2010-01-08
Did you set setup.exe for Fallout to run as Windows 98 in winecfg?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=43](http://appdb.winehq.org/objectManager.php?sClass=version&iId=43)

---

### Post by DrSeptapus on 2010-01-08
I did. It did not solve the problem.

---

### Post by gsmanners on 2010-01-09
From Googling around, it looks like a lot of Windows users are getting the same error. So, I'm guessing a Windows solution would probably work as well.

[QUOTE=bigshurup]...

If the game complains that you need at least 20MB of free disk space, go to the installation folder, find the FALLOUT.CFG file, open it with your Notepad and find the line free_space=20480 and change the value to 0 (zerro). Save and exit.[/QUOTE]

---


---
title: "disk full, Bus error, Input/Output error"
date: 2010-04-07
forum: Server Platforms
---

### Post by johndoe20081026 on 2010-04-07
Hi everyone,
 I think that now I'm really in trouble and would aprotiate every help.
 Today I tried to reach the homepage of our site stored on an Ubuntu Server (9.04) (in Amazon EC2) and realized it cannot be reached. I logged in using ssh, it worked. After a while I realized the problem is caused by the disk is full:

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             10321208   9794896      2024 100% /
tmpfs                   879648         0    879648   0% /lib/init/rw
varrun                  879648        92    879556   1% /var/run
varlock                 879648         0    879648   0% /var/lock
udev                    879648      2512    877136   1% /dev
tmpfs                   879648         0    879648   0% /dev/shm
/dev/sda2            153899044    192092 145889328   1% /mnt

Of course I tried to free up some disk space but no luck:
$ rm *.xml
Bus error
$ rm -f *.xml
Bus error
$ sudo rm -f *.xml
Bus error

I tried to move these files to another partition, still no luck:

$ mv *.xml /mnt/
Bus error 

Other thing I tried is remounting sda1 to somewhere else, no luck again:

$ sudo mount /dev/sda1 /mnt/mnt
sudo: unable to execute /bin/mount: Input/output error

Most of the commands resuts "Bus error" or "Input/Output error", but some of the commands doesn't return anything (man, top).
I must find a way to delete some files without rebooting the computer. (Because of this computer is in Amazon EC2 , if I reboot it, everything will be lost that is not in the image.)
If I really have to restart the computer, then I need to find a way to backup my mysql db's and some files before restarting.
Thank you in advance!

---

### Post by johndoe20081026 on 2010-04-08
Things are even worse now:
I cannot sudo, I get the usual Input/Output error.

It seems that both /dev/sda1 and /dev/sda2 are mounted as read-only...

Any idea?

---

### Post by deracled on 2010-04-08
Can you post the output of **mount** ?

Doros

---

### Post by johndoe20081026 on 2010-04-08
Hi Doros,
 Thank you for your interest. Unfortunatelly mount gives me the same error with any parameters:

$ mount
-bash: /bin/mount: Input/output error

---

### Post by Cracauer on 2010-04-08
This isn't caused by a full disk. Some kind of hardware trouble is going on.

Try `dmesg`. If that can't read it's own binary, you gotta reboot and hope that /var/log/messages has something useful from before the reboot.

---


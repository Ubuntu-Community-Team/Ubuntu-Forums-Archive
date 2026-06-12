---
title: "Gazelle Performance: Several problems (Feisty + others)"
date: 2007-04-20
forum: System76 Support
---

### Post by rmaus on 2007-04-20
I have been talking with some of the support guys through email, and I figured I would bring the problem to the forums as well, in case anybody else had similar problems and (hopefully) fixes.

1.  Sound problems [FIXED]
Make sure after you upgrade Feisty to re-enable your S76 repos, and get the latest driver.  Thanks support!
  
Problem 2:
Whenever I try to access my optical drive, I get "Cannot mount volume: /dev/scd0 doesn't exist".  I looked through the /dev/ folder, and there are no devices that match any sort of CD drive (scd*, cdrom*, etc).   S76 support said that this was due to the fact that I had a bad drive, so they sent me a new one (thank you, by the way, for the quick replies and fix).  This unfortunately didn't solve the problem, the drive still won't mount because /dev/scd0 still doesn't exist.

The contents of my /etc/fstab are as follows:
```
# /etc/fstab: static file system information.
#
# file system&amp;amp        mount point&amp;amp      type           options          dump         pass
proc	/proc	proc	defaults	0	0
# /dev/sda1
/dev/sda1	/	ext3	defaults,errors=remount-ro	0	1
# /dev/sda5
/dev/sda5	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto	0	0
```

System76 support has been fantastic so far, thank you in advance for your time.

---

### Post by crichell on 2007-04-20
Hi rmaus,

Our repository was probably disabled during the upgrade.  Take a look here:

[http://knowledge76.com/index.php/FeistyUpgrade](http://knowledge76.com/index.php/FeistyUpgrade)

And check that it is enabled.  After enabling try installing again:

```
sudo apt-get install system76-driver
```

Afterward installation go to System > Administration > System76 Driver and click Install on the drivers tab.  Thanks to folks quickly notifying us of the sound problem we released a new driver last night fixing the issue.

I check further into your CD-Rom problem as well.

---

### Post by crichell on 2007-04-20
Can you post the output of:

```
ls /media/
```

---

### Post by rmaus on 2007-04-20
With a data CD in the drive I get this from "ls -Rl /media"
```
rmaus@ubuntu:~$ ls -Rl /media
/media:
total 4
lrwxrwxrwx 1 root root    6 2007-03-14 22:47 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-01-11 16:39 cdrom0

/media/cdrom0:
total 0

```

just ls /media/ returns:
```
rmaus@ubuntu:~$ ls /media
cdrom  cdrom0

```


Regarding the System76 drivers, you were right, I forgot that the upgrade disables the repos.  I now have the most recent driver and sound is working properly, thank you.

---


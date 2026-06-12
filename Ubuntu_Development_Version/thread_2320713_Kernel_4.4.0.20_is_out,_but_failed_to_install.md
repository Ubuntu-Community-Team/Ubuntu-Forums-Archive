---
title: "Kernel 4.4.0.20 is out, but failed to install"
date: 2016-04-16
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2016-04-16
I got a message from update manager (frozen) saying* wait for apt-get to exit*.  Didn’t have anything open.  Close it, re-open it and then Kernel 4.4.0.20 did not load properly.  Not shown in Grub menu?  Shown in Synaptic, but not install.
 
 
 On last night updates, there was a message on reboot saying that Flashplugin needs an upgrade.  Internet was not open and I did not get that update.
 
 
 4.4.0.19 + 4.6-rc3
 
 
 Commit Log for Sat Apr 16 14:05:09 2016
 
 
 Upgraded the following packages:
 libdevmapper1.02.1 (2:1.02.110-1ubuntu9) to 2:1.02.110-1ubuntu10
 linux-headers-generic (4.4.0.19.20) to 4.4.0.20.21
 linux-libc-dev (4.4.0-19.35) to 4.4.0-20.36
 openssh-client (1:7.2p2-3) to 1:7.2p2-4
 
 
 Installed the following packages:
 linux-headers-4.4.0-20 (4.4.0-20.36)
 linux-headers-4.4.0-20-generic (4.4.0-20.36)

---

### Post by MikeMecanic on 2016-04-16
# deb cdrom:[Ubuntu-Kylin 16.04 LTS _Xenial Xerus_ - Beta amd64 (20160414)]/ xenial main multiverse restricted universe
 
 
 On last night updates there was another message about Grub, I rarely get that one.  Must say that I never know what to do with that Grub pop-up (stops the update process) where there are 5 or 6 options to deal with.  Always keep it the way it is (default option), something like keep actual configuration.
 
 
 I’m waiting for a confirmation before trying manual upgrade in Synaptic.  Removing 4.4.0.19 and run update manager didn’t change anything.  For the rest, I’m not sure at 100% but I think I didn’t see linux-image 4.4.0.20 in Synaptic terminal during the updates?

---

### Post by grahammechanical on 2016-04-16
For me. today's update brought in kernel 4.4.0-20 without any problems. It also updated Grub but as I have a default Grub config I was not asked if I wanted to keep a modified config.

> graham@sdb7-Dev:~$ uname -a
Linux sdb7-Dev 4.4.0-20-generic #36-Ubuntu SMP Fri Apr 15 20:49:38 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Regards

---

### Post by MikeMecanic on 2016-04-16
Thanks for replying.
 
 
 I just made a manual installation in Synaptic.  It’s the first time I’m getting an issue like this one.   Kylin runs like a Swiss clock on Kernel 4.6-rc3, no bug at all except this ‘’momentary’’ one.

  	 	 	 	   
```
xx@kylin:~$ uname -r

 4.4.0-20-generic

```

---


---
title: "virtualbox-5.1 suspend problem"
date: 2016-11-07
forum: Virtualisation
---

### Post by alberto.stefanelli on 2016-11-07
Hello everybody,

my laptop does not correctly resume after sleep (ubuntu 16.10). The cause of the problem seems to be virtualbox. Indeed, before installing it everything worked fine and if i remove it the suspend starts to work again (btw /var/log/syslog does not provide any valuable info). This problem affects both 5.1.6 and 5.1.8 versions and seems related to the vbox modules. This post [https://ubuntuforums.org/showthread.php?t=1810091](https://ubuntuforums.org/showthread.php?t=1810091) provides a solution but it is outdated cause now ubuntu uses systemd.  

Can someone help me in understanding how i can fix this problem?

Many thanks

---

### Post by ajgreeny on 2016-11-07
Just to clarify your situation, are you trying to suspend your host with one or more VMs running in VBox-5.1.8, or is it simply installing the VBox package that stops suspend from working?

---

### Post by alberto.stefanelli on 2016-11-08
the latter, installing vbox broke the suspend of the host

---

### Post by ajgreeny on 2016-11-09
It could be worth trying VBox version 5.0.28, the latest of the 5.0 series which did solve some of my problems with 5.1 when I first tried it.

I am now back on 5.1.8, however, with no problems, so maybe this is some 16.10 specific incompatibility or, more likely, it might be related to your specific hardware combination..

---

### Post by alberto.stefanelli on 2016-11-10
Problem still presents with 5.0.28 version. does someone know how to unload kernel module form command line?

---

### Post by ajgreeny on 2016-11-12
If you run command ```
lsmod | grep vbox
``` you should see something like this.
```
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci
```
and could, if you really must, remove the problem module with **modprobe -r** but this is something I have never done, nor needed to, so I can't tell you any more about this.

Don't forget that without the module you will be unable to use any of your VMs as I do not believe they will run without it.

---


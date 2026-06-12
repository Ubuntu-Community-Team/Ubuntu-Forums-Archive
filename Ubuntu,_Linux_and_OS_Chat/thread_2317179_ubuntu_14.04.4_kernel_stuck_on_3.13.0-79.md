---
title: "ubuntu 14.04.4 kernel stuck on 3.13.0-79"
date: 2016-03-14
forum: Ubuntu, Linux and OS Chat
---

### Post by matrooswolf on 2016-03-14
Hi,

I have Ubuntu 14.04.4, update regularly, but I just checked my kernel with uname -r and it is still on 3.13.0-79. Why doesn’t my kernel upgrade to newer versions? There are a lot available. Even 4.2.

Can I safely install 4.2 with synaptics?

Anybody have any advice?

---

### Post by kc1di on 2016-03-14
Ubuntu LTS does not upgrade the kernel beyond upgrades in the kernel that it was originally released with very often.  It takes a very conservative approach to kernel upgrades.
[This wiki]("https://wiki.ubuntu.com/Kernel/Support") may explain it better 

you can upgrade the kernel if you like , just don't delete the old one until your sure everything works ok with the new one. 
good luck

---

### Post by Bucky Ball on 2016-03-14
The LTS is designed for stability, not to be the latest on the block. You can add whatever you like to it, the latest version of whatever, but there are no guarantees things will remain stable, particularly as your install becomes more of a hybrid and no longer what would be considered a 'vanilla' LTS install. 

In other words, you can safely install it using Synaptic but that doesn't mean everything will be fine when you boot from it. No matter. Just boot back to one of the older kernels if it's not (-79).

Just throwing that in. I have used newer kernels in the past in LTS releases, but only as it was the only way to get a new piece of hardware going. Unless you have a specific reason or are in this for a little experimentation and learning, I'd stay where you are. If you just want the 'latest', install 16.04 LTS on another partition and play with that. That is on the 4 kernel and will be officially released in early April. 



Good luck.

---

### Post by ajgreeny on 2016-03-14
As the point versions of the version are released the kernel and the xorg version is updated if, and only if, you install new with, for example, the iso image of Ubuntu 14.04.4.  Normal updates will not update either the kernel or xorg version.

It is possible to update to the equivalent of the newer kernel and xorg 14.04.4 version by upgrading the hardware-enablement but I have never done it nor needed to, so can not give you a personal recommendation about this.

However, my final comment has to be "If it ain't broke, don't fix it"; sometimes newer is not necessarily better.
If you want to know more have a read through all the info at [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) and you will see how you can go forward.

---

### Post by matrooswolf on 2016-03-14
Thank you all for your replies. I'll stick with the 3.13 for now. I will probably upgrade to 16.04 anyway, so that's not far away.
Thanks again.

---

### Post by kansasnoob on 2016-03-14
[B]Please ignore this, I was [full of baloney]("http://ubuntuforums.org/showthread.php?t=2317179&page=2&p=13455349#post13455349")!
[/B]
Just BTW that kernel is actually from trusty-proposed, so it has not passed all internal testing :(

The current original Trusty kernel is now up to:

```
lance@lance-desktop:~$ uname -r
3.13.0-76-generic

```

You may get lucky applying updates from the proposed repos but sooner or later it'll get ya'! That's why they've moved proposed to a new developer section of software sources in Xenial:

[http://ubuntuforums.org/showthread.php?t=2316479](http://ubuntuforums.org/showthread.php?t=2316479)

The intended use for proposed updates is SRU testing:

[https://wiki.ubuntu.com/QATeam/PerformingSRUVerification](https://wiki.ubuntu.com/QATeam/PerformingSRUVerification)

---

### Post by grahammechanical on 2016-03-14
Ask yourself, what does the -79 mean in that kernel name (Linux 3.13.0-79) mean?

kansasnoob is on 3.13.0-76. You are on 3.13.0-79. That 3.13 series kernel is getting security fixes. We are getting what was promised. No more but neither no less.

Regards.

---

### Post by ajgreeny on 2016-03-14
@kansasnoob.
I do not think the 3.13.0-79 kernel is from proposed; I don't have proposed enabled, never have, and the 3.13.0-79 kernel arrived with my updates on March 3rd, 11 days ago.

@matrooswolf
No need to worry about that; just make sure you don't have the proposed repos enabled unless you are aware of potential problems and prepared to fix breakages that may happen.

EDIT:
I have just updated my 14.04.4 Xubuntu (no hardware stack updates) and the 3.13.0-83 kernel has just arrived today.  This still without the proposed repos enabled.

---

### Post by vasa1 on 2016-03-14
> **ajgreeny said:**
> ...
EDIT:
I have just updated my 14.04.4 Xubuntu (no hardware stack updates) and the 3.13.0-83 kernel has just arrived today.  This still without the proposed repos enabled.
Thanks, updating now.

OP, you may want to try 16.04 as a live USB before leaving 14.04 behind just to make sure everything will still work :)

---

### Post by deadflowr on 2016-03-14
> **kansasnoob said:**
> Just BTW that kernel is actually from trusty-proposed, so it has not passed all internal testing :(

The current original Trusty kernel is now up to:

```
lance@lance-desktop:~$ uname -r
3.13.0-76-generic

```

You may get lucky applying updates from the proposed repos but sooner or later it'll get ya'! That's why they've moved proposed to a new developer section of software sources in Xenial:

[http://ubuntuforums.org/showthread.php?t=2316479](http://ubuntuforums.org/showthread.php?t=2316479)

The intended use for proposed updates is SRU testing:

[https://wiki.ubuntu.com/QATeam/PerformingSRUVerification](https://wiki.ubuntu.com/QATeam/PerformingSRUVerification)


Upgrade your kernel.
3.13.0-79 is the latest and includes bug fixes:
[http://www.ubuntu.com/usn/usn-2907-1/](http://www.ubuntu.com/usn/usn-2907-1/)

Edit: I have not looked for updates today, as I am on xenial atm.

---

### Post by vasa1 on 2016-03-14
> **deadflowr said:**
> Upgrade your kernel.
3.13.0-79 is the latest and includes bug fixes:
[http://www.ubuntu.com/usn/usn-2907-1/](http://www.ubuntu.com/usn/usn-2907-1/)

Edit: I have not looked for updates today, as I am on xenial atm.
This is what I saw after reading ajgreeny's post
```
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.13.0-83 linux-headers-3.13.0-83-generic
  linux-image-3.13.0-83-generic linux-image-extra-3.13.0-83-generic
The following packages will be upgraded:
  libgraphite2-3 linux-generic linux-headers-generic linux-image-generic
4 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 61.6 MB of archives.
After this operation, 272 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
```I don't have *proposed* enabled.

---

### Post by kansasnoob on 2016-03-14
> **ajgreeny said:**
> @kansasnoob.
I do not think the 3.13.0-79 kernel is from proposed; I don't have proposed enabled, never have, and the 3.13.0-79 kernel arrived with my updates on March 3rd, 11 days ago.

@matrooswolf
No need to worry about that; just make sure you don't have the proposed repos enabled unless you are aware of potential problems and prepared to fix breakages that may happen.

EDIT:
I have just updated my 14.04.4 Xubuntu (no hardware stack updates) and the 3.13.0-83 kernel has just arrived today.  This still without the proposed repos enabled.

Yikes, you're right! At some point performing tests I inadvertently removed the 'linux-generic' meta-package so I was not getting kernel updates as I should have been :redface:

---

### Post by ajgreeny on 2016-03-15
> **kansasnoob said:**
> Yikes, you're right! At some point performing tests I inadvertently removed the 'linux-generic' meta-package so I was not getting kernel updates as I should have been :redface:
Ah!  Been there; done that, amongst other daft things.

---


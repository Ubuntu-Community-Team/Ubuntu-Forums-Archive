---
title: "Virtualbox 4.2.12, Ubuntu 13.04 as host and windows 7 as client causing kernel panics"
date: 2013-04-26
forum: Virtualisation
---

### Post by verbedr on 2013-04-26
Hi,
I just upgraded my distro to Ubuntu 13.04 and my Virtualbox is throwing randomly kernel panic's. I got a suspicion that it has something to do with the wifi adapter. But can't confirm. 

Is this the correct place to post this kind of issues? And if so what more information do I need to publish? Are there other people having this problem?

Regards
Dries
ps the reason why I'm working with VB 4.2 is because the version that comes with Ubuntu 13.04 also caused these kernel panic's.

---

### Post by gwm on 2013-04-28
Hi,
I too am having problems.
I figure that possibly there is some incompatibility in the configuration files. To handle that, I moved the .vdi file to another folder and deleted the Vitrualbox VMs directory that used to contain it.

Next I went looking for a release on the Oracle website. They don't have a 13.04 version. That means we are trying to make the older one work with an unsupported kernel. To recompile the kernel, we need the correct header files and they don't exist . . . etc.

Next I went to the Ubuntu Software Center and installed their version of VirtualBox. As I understand it, this is the OSE version (which I guess probably means something like Open Source Edition) - I read somewhere in the forums that Oracle don't support it.

I started this version and created a new virtual machine without a hard drive. This recreated the directory that I had earlier deleted and I moved the .vdi file into it. Finally, under the settings for my new virtual machine, I added an exisiting hard drive and pointed it to the .vdi file.

Now it all is well in the jungle!!

:guitar:

---

### Post by verbedr on 2013-04-29
Hi,
I just want to inform everybody that I found the culprit module and got the problem resolved (read  ... it doesn't happen any more).

I had a proprietary wifi driver (broadcom 802.11 Linux STA) which of course was not updated with the new kernel headers that came with the ubuntu 13.04.  The solution was updating the driver by following [these steps]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

So mental reminder don't forget to update your proprietary drivers when there is a kernel update ...

Regards
Dries

---

### Post by verbedr on 2013-05-06
Hi me again ... in the end updating the driver didn't not solve my situation. I just had it removed and this seems to work. Now I'm using the b43 driver and not the wl driver ...

Regards
Dries

---


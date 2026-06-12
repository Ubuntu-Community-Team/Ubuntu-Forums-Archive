---
title: "Ubuntu 13.10 Desktop guest, problems with Guest Additions (not beta)"
date: 2013-10-17
forum: Virtualisation
---

### Post by daniel-glasser on 2013-10-17
Host: Virtual box 4.2.18 on Windows 7 64 bit (quad processor, 16GB RAM)  (sorry, this is my workstation at work, and IT doesn't let us have Linux on the desktop hardware, hence my using Virtualbox)
Guest: Ubuntu 13.10 64 bit (x86_64), 2 cpus, 4GB RAM, Guest Additions 4.2.18_88780

I've got a virtual machine with Ubuntu 13.04 x86_64 running nicely.  When the software updater in the virtual machine offered to upgrade it to 13.10, I exited the VM, made a clone, tested the clone (all networking, Guest Additions, etc., working just as the original had), then let the updater upgrade the "system" to 13.10.  On reboot, the GAs didn't work, but I'm used to that; I removed and re-installed the guest additions using the ISO that comes with Virtualbox, and rebooted again.  The video was not working properly and any attempt to access "/media/sf_share" would hang.  I did some looking around on line and found the advice to install this from the repository (bad advice, BTW, since it installed 4.2.16, which isn't compatible with 4.2.18, but I digress).  This didn't improve things.  I re-installed with the 4.2.18 ISO from VirtualBox, and this time the video seems to work, but the hang still occurs when trying to access the share folder.

When I run the original VM that still has 13.04, everything is fine.

I found some forum threads from the Beta period on 13.10, all of which say "of course it doesn't work, it's a beta"; well, this is not the beta, it's the release.

While writing this, I discovered that Oracle has released 4.3 of VirtualBox -- The app's "check for updates" claims no update is available; I may try updating to that and see what happens, but there is definitely an incompatibility between the VirtualBox Guest Additions version 4.2.18 and Ubuntu 13.10.

I'd appreciate any advice for a fix for this without having to update VirtualBox on the lab machines that are not on the network (and I can't change anything that's in the load-set while we're doing verification -- the VM is not part of the loadset, but Virtualbox is.)

Thanks,
    Filker0

---

### Post by JKyleOKC on 2013-10-18
> **daniel-glasser said:**
> any attempt to access "/media/sf_share" would hang.

...

there is definitely an incompatibility between the VirtualBox Guest Additions version 4.2.18 and Ubuntu 13.10.FWIW, I'm seeing this same hang when attempting to access shared folders. My host (running vbox 4.2.18) is 12.04.3 Xubuntu 32-bit, and the guest is also Xubuntu 32-bit; first attempt was an update from 13.04 to 13.10 using the Live CD, and I later did an absolutely clean install of 13.10 to a newely created VM, with the same result: attempting to open a shared folder causes the file manager to hang in what appears to be an infinite loop, with the (virtual) CPU pegged at 100%.

---

### Post by afz12 on 2013-10-18
I have the same problem with 13.10 full release on win 8 as a host. However I have little experience runing Linux on windows but running windows on Linux has always worked well. I also note that USB support is absent. Is there at least a way to at least make USB support work?

Otherwise Ubuntu 12.10 seems extremely stable both as a VM and native on another notebook. 12.04 and earlier version always showed error messages for no reason but these have not shown up on Ubuntu 12.10. So perhaps we win on the swings but loose on the slides?:(

---

### Post by DbhTPnx on 2013-10-19
Virtualbox 4.3 has been released - this issue is resolved for Ubuntu 13.10. Virtualbox's "check for updates" doesn't indicate the availability of the 4.3 upgrade, but you can download it as the latest stable release from the download page.

---

### Post by yoga2 on 2013-10-24
Hi,
I saw an old discussion about this: But that one is for the case the host is XP and the guest is Ubuntu. They said that XP has to express the DNS hense the visit for shared folder is slow.

By the way I am suffering this problem too.I tried to modify the host file in ubuntu while it seemed not working.  I have a Mac OS and a Ubuntu 13.10 64 bits.as guest.

---

### Post by dolphintweety on 2013-10-30
I got the same problem with accessing shared Virtualbox folders. I thought it was permission problems. I read through this forum and followed the advice on updating Virtualbox and its guest-additions.iso. Virtualbox didn't notify me about an update. Thanks to all for helping out. Virtualbox 4.3  solved the problem for me too. :D





"Abondoned Windows at home but it follows me elsewhere :mad:"

---

### Post by jwangzju on 2013-11-15
I tried to upgrade to VB 4.3 and it works.

---


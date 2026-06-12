---
title: "[Galago ultrapro] Blutooth not working after 14.10 upgrade"
date: 2014-10-26
forum: System76 Support
---

### Post by Nicolas_Ehrhardt on 2014-10-26
Hi,

Blutooth won't work after upgrade to Ubuntu 14.10 on Galago Ultrapro.
It is impossible to activate it after several reboots. I am wondering how many of us are affected?

> 
> $ dmesg | grep Blu                                                           
[    6.884069] Bluetooth: Core ver 2.19
[    6.884083] Bluetooth: HCI device and connection manager initialized
[    6.884089] Bluetooth: HCI socket layer initialized
[    6.884091] Bluetooth: L2CAP socket layer initialized
[    6.884100] Bluetooth: SCO socket layer initialized
[    6.889226] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.889229] Bluetooth: BNEP filters: protocol multicast
[    6.889233] Bluetooth: BNEP socket layer initialized
[    6.893291] Bluetooth: RFCOMM TTY layer initialized
[    6.893298] Bluetooth: RFCOMM socket layer initialized
[    6.893302] Bluetooth: RFCOMM ver 1.11
[   10.960839] Bluetooth: Error in firmware loading err = -110,len = 448, size = 4096
[   10.960846] Bluetooth: Loading patch file failed


It seems to be related to the latest linux kernel ([https://bbs.archlinux.org/viewtopic.php?id=183038](https://bbs.archlinux.org/viewtopic.php?id=183038)). But not sure at all...
I was thinking of trying the patch proposed in the above forum, but I'd like to wait from feedback of knowledgable people :D.

Don't hesitate to ask me for any log.

Thanks!
-Nicolas

---

### Post by MoebusNet on 2014-10-26
Bluetooth seems to have been an ongoing issue since about 12.10. It depends on what function you are trying to achieve. For example, bluetooth headsets for 14.10 were working properly last time I checked. [https://bugs.launchpad.net/ubuntu/+bug/1283003](https://bugs.launchpad.net/ubuntu/+bug/1283003) Transferring files via Bluetooth is still nonfunctional as far as I know. [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1284308](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1284308)

---

### Post by Nicolas_Ehrhardt on 2014-10-28
I am trying to connect to my Bose SoundLink Mini (Portable Bluetooth speaker).
I never had any issue to connect to it on 14.04.

---

### Post by Nicolas_Ehrhardt on 2014-10-30
The issue was solved with the latest kernel.
Surprisingly, I had to shutdown (no reset) my computer for a few minutes for the bluetooth to work again.

---

### Post by noahy2 on 2014-11-01
> **Nicolas_Ehrhardt said:**
> The issue was solved with the latest kernel.
Surprisingly, I had to shutdown (no reset) my computer for a few minutes for the bluetooth to work again.

Thanks, same problem here. It wasn't a new kernel that solved it for me... I upgraded and Bluetooth wasn't working. I then upgraded the System76 drivers as per their guide here:

 [http://knowledge76.com/index.php/Version_Upgrade](http://knowledge76.com/index.php/Version_Upgrade)

Upgrade, reboot, still not working. Then I found your post. Shutdown, turn on, Bluetooth working. Maybe it was the upgraded driver?

---

### Post by Nicolas_Ehrhardt on 2014-11-02
It's pretty unclear to me what solved it. 
I read a thread in a forum of another distro (Arch, I think) advising to shutdown the laptop completely.
It was related to a bug in the kernel. 

So I am still not sure if this is due to the System76 drivers or the kernel since I upgraded the drivers before using my bluetooth again.

---


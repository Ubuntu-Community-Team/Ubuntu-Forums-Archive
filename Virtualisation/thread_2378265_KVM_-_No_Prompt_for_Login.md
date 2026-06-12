---
title: "KVM - No Prompt for Login"
date: 2017-11-21
forum: Virtualisation
---

### Post by yetanotheruser2 on 2017-11-21
> **SuprScotte said:**
> *BUMP*


I've posted this thread over on Proxmox's forums, and they believe it's more related too Ubuntu. Anyone experience this type of issue, or have any recommend tips I could follow?
Hello. Currently I have the same problem and only with Ubuntu 16.04. I has installed ubuntu from [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/installer-amd64/current/images/netboot/mini.iso).
Guest OS (Ubuntu 16.04) reacheable via ssh but noVNC can't connet to VM - black screen. In the proxmox logs I see: [COLOR=#000000][FONT=tahoma]TASK ERROR: connection timed out[/FONT][/COLOR]

---

### Post by QIII on 2017-11-21
Moved to its own post from [this thread]("https://ubuntuforums.org/showthread.php?t=2373278").

Hello!

Please do not hijack the threads of other users.  Everyone here deserves individual attention and trying to solve more than one person's issue in the same thread leads to confusion.  While your symptoms may be similar, the underlying cause may be quite different.

Cheers!

---

### Post by KillerKelvUK on 2017-11-22
This is an old bug in the mini's, see here [https://ubuntuforums.org/showthread.php?t=1836985](https://ubuntuforums.org/showthread.php?t=1836985)

---

### Post by yetanotheruser2 on 2017-11-23
> **KillerKelvUK said:**
> This is an old bug in the mini's, see here [https://ubuntuforums.org/showthread.php?t=1836985](https://ubuntuforums.org/showthread.php?t=1836985)
Hello. Thanks for reply. I was try to solve this issue with 


> (1) Edit /etc/grub.d/10_linux (e.g. "sudo nano -w /etc/grub.d/10_linux") and comment out the line containing "vt.handoff", or change the number from 7 to some lower number. (I tried it both ways; they both worked.)
(2) Run "sudo update-grub" to apply the new configuration.
(3) Reboot. A usable virtual terminal with a login prompt comes up automatically.


But it doesn't help. Also in /etc/grub.d/10_linux (Ubuntu 16.04 - mini):
vt.handoff = 1 already set...


I installed ubuntu 14.04 mini and it work fine, so I think VNC issue affected only Ubuntu 16.04

---

### Post by KillerKelvUK on 2017-11-23
What hypervisor are you using?

---


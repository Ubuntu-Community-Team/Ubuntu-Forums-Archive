---
title: "Ubuntu on virutalbox - strange screen with colors after boot."
date: 2016-10-25
forum: Virtualisation
---

### Post by lukasz021 on 2016-10-25
Hi,

I wanted to test Ubuntu on my VirtualBox so I decided to try a liveCD version. I have Windows7 64bit. On VirtualBox I set a machine for Ubuntu 16.04.1 (-desktop-i386), so with 32 bit.
I also set in the machine to boot from ISO file of Ubuntu, so that it can act as a LiveCD. With this I don't have to install Ubuntu. 
Here is where the problem starts. When I ran the machine when Ubuntu is loading i get this screen (image below): 

[IMG]http://t1.cba.pl/linux/ubutnu32-error.JPG[/IMG]



I tried to run the same Ubuntu ISO file on an old computer with Windows XP (32 bit) inside VirtualBox and got the same result. 

My question is what could be the cause?

Thanks for any help.
Luke

---

### Post by slickymaster on 2016-10-25
*Thread moved to **Virtualisation**.*

---

### Post by ajgreeny on 2016-10-25
Did you check the iso file you have against the hashes shown at [https://help.ubuntu.com/community/UbuntuHashes?](https://help.ubuntu.com/community/UbuntuHashes?)

What is the spec of the host machine for your Ubuntu guest, and what resources did you allow for it in the virtual disk setup procedure?

Also what is the spec of the old XP machine?  That may not be powerful enough to run Ubuntu which needs reasonably powerful 3D graphics acceleration to be able to run the Unity desktop properly.

---

### Post by lukasz021 on 2016-10-27
Ok, the problem got solved. I used "ubuntu-14.04.5-desktop-i386" version and it worked. Thanks for answer anyway.

---


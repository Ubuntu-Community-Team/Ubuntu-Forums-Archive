---
title: "Automatic Upgrades doubt"
date: 2013-09-09
forum: Server Platforms
---

### Post by Marcos_Cano on 2013-09-09
hello im currently running ubuntu 12.04 server, and i find my self now in doubt.

i actually want to disable automatic updates /upgrades from happening because im running  3.5.0-37-generic , that's the kernel that has third party modules installed on, i don't want to go to a newer kernel because that will mean that ill have to compile the modules again and again for each kernel.

however i still want to achieve security and important updates. (unattended-upgrades i guess).

is there any way to enable automatic security /and/or important updates without upgrading the kernel?

thanks in advance
PD:so far i've found modifying /etc/apt/apt.conf.d  10periodic , 50unattended-upgrades & 20auto-upgrades.. and yes the kernel isn't updating any more but i'm afraid that i'm missing security updates..

---

### Post by CharlesA on 2013-09-11
You could pin/hold the kernel, but if you are using third party modules, why aren't you setting them up in [DKMS]("https://help.ubuntu.com/community/DKMS")?

---


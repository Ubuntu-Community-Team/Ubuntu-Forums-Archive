---
title: "VirtualBox Networking. How to set it up right?"
date: 2008-12-31
forum: Virtualisation
---

### Post by Kdar on 2008-12-31
I have wireless connection. "Auto eth0"

What is correct way to get network correctly in VirtualBox (I am trying to run windows XP there now).

Right now I am using

Attached to: Host Interface
Host Interface: wlan0

But.. On this site..
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
This guy is writing about some bridges.. I tried to do what he write about.. but got kind of lost.

---

### Post by Dedoimedo on 2009-01-01
Hello,

Bridging is not needed. You can use NAT. Under Settings for the particular virtual machine, set Networking to NAT and use wlan0.

Boot the virtual machine and see what happens.

Dedoimedo

---


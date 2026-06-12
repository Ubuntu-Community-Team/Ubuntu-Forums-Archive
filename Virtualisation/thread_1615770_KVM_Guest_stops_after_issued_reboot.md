---
title: "KVM Guest stops after issued reboot"
date: 2010-11-07
forum: Virtualisation
---

### Post by Zeratul021 on 2010-11-07
Hi all,

I have a problem with Ubuntu installed on my guest machine. When I issue reboot the machine stops and needs to be launched from host machine using virsh start {vmname}. Has anyone encountered this? Host machine is 64b Debian Squeeze and Guest is 64b 10.10.

It may correspond to this [https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/219326](https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/219326).

Regards,

Marek

---

### Post by gdahlm on 2010-11-13
please post the output from 

virsh dumpxml guestname

where guestname is the name of your VM

---


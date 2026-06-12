---
title: "KQemu not compiled - bug in package?"
date: 2010-03-01
forum: Virtualisation
---

### Post by SysterNeoX on 2010-03-01
Hi all!

Tonight i was trying to get kernel acceleration worked with qemu.
So i installed qemu package and kqemu-common from the ubuntu repos.

And now: 
Kqemu module is loaded, i can see it loaded from lsmod. Also device /dev/kqemu is created properly.

However, when i start qemu and type in qemu monitor command "info kqemu" i get: "kqemu support: not compiled". Also, when i try to find some parameters related to kqemu in qemu's help, i get nothing:

[PHP]byku@SysterPC:~/MyMachines/Windows_XP$ qemu --help | grep kq
byku@SysterPC:~/MyMachines/Windows_XP$ ^C
[/PHP]
Maybe it's a bug in qemu package? It means packager forgotten to turn on kqemu support during compiling qemu?

PS: I've got ubuntu 9.10 32-bit running on 32-bit processor

---

### Post by kiranmurari on 2010-03-02
Hi,
   
You need to have proper user permissions on /dev/kqemu.
```
$ sudo chmod 666 /dev/kqemu
``` Also start your virtual machine with the "-kernel-kqemu" option.
```
$ qemu -m 256 -hda myVM.img -boot c -kernel-kqemu
``` Once you are on the qemu-monitor, "info kqemu" should give the following output:
```
(qemu) info kqemu
kqemu support: enabled for user and kernel code.
```If you are not using the "-kernel-kqemu" option, then kqemu support will only be enabled for user code.
```
$ qemu -m 256 -hda myVM.img -boot c
``````
(qemu) info kqemu
kqemu support: enabled for user.
```     Hope this helps.

---

### Post by protag.hiro on 2010-03-02
I just had the same problem. Searching found this entry in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/426497](https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/426497)
which states that kqemu support was removed upstream and therefore won't be available in the default package.

Looks like we are both out of luck.

---


---
title: "None ot the 4.2 kernels can access internet using a Realtek RTL8111/8168/8411 nic"
date: 2015-09-14
forum: Ubuntu Development Version
---

### Post by xeizoo on 2015-09-14
All other kernels up to and including 4.1.7 works fine, I have reported the bug at bugzilla but have yet to see any solution to the problem. Googling the issue it looks like it has affected others, was some threads on Archlinux about the issue. Arch users looks to solve it by compiling in another dkms-driver for Realtek, its not as easy with Ubuntu as it is not that common to compile your own kernel with specific patches being a Ubuntu user. Arch users compiles most everything. I did compile a personal kernel, but then got hit by the need to patch it for Nvidia as well  arrggh ...

The bug:
[https://bugzilla.kernel.org/show_bug.cgi?id=104411](https://bugzilla.kernel.org/show_bug.cgi?id=104411)

---

### Post by dino99 on 2015-09-14
Having sent a report on bugzilla is nice; but you should also open one on launchpad as you seems not have tested the vanilla kernel. You need to know if its only an ubuntu kernel issue.

---

### Post by xeizoo on 2015-09-15
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1495852](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1495852)

Done too!

---

### Post by dino99 on 2015-09-15
it might help the kernel team if you copy the Arch link with the dkms patch

---

### Post by kagashe on 2015-09-15
I have this card and it is working well on Ubuntu 15.10 Kernel 4.2. I have commented on Launchpad and replying here.

```
$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu Wily Werewolf (development branch)"
Linux Lenovo-G50-45 4.2.0-7-generic #7-Ubuntu SMP Tue Sep 1 16:43:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

```
$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
	Kernel driver in use: rtl8723be
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:3812]
	Kernel driver in use: r8169

```

I generally use wifi but now running on Ethernet.

I can give more information as required.

Kamalakar

---

### Post by dino99 on 2015-09-15
#5
so it might be related to the installed packages from gnome3 ppa; working with 4.1.7 but not with the newest. Maybe the OP should downgrade these packages, to see if that solve the problem.

---

### Post by xeizoo on 2015-09-15
> **kagashe said:**
> I have this card and it is working well on Ubuntu 15.10 Kernel 4.2. I have commented on Launchpad and replying here.

```
$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu Wily Werewolf (development branch)"
Linux Lenovo-G50-45 4.2.0-7-generic #7-Ubuntu SMP Tue Sep 1 16:43:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

```
$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3812]
    Kernel driver in use: r8169

```

I generally use wifi but now running on Ethernet.

I can give more information as required.

Kamalakar

Thanks! That was healthy information that got me experimenting, first I tested todays daily live iso and it DID have internet using 4.2.0-7! Sadly, it wasn't possible to install since Ubiquity is severely broken at the moment. Then I tried purging all from gnome3 team, it didnt help though so I had to go the long way and install 15.04 vanilla(which has a broken grub-install btw, maybe why it isnt recommended on the homepage). I had to do extensive grub repair and finally got 15.04 installed, and then upgraded all the way to todays 15.10, which HAS internet using the 4.2.0-10.11 kernel which is now the latest version in the repos.

It means solved, but not really why, possibly Gnome3 was the culprit, but no proof for it.

---

### Post by kagashe on 2015-09-15
I installed using following command:
```
sudo -H bash -c 'ubiquity gtk_ui'
```
Kamalakar

---

### Post by dino99 on 2015-09-16
Its time to also close your opened report ;)

---

### Post by xeizoo on 2015-09-16
> **dino99 said:**
> Its time to also close your opened report ;)

In launchpad? Yes, but I cant find the button for it ;)

I changed status to "fix released" though, suggesting a fresh distro install is "the fix"

---

### Post by xeizoo on 2015-09-16
> **kagashe said:**
> I installed using following command:
```
sudo -H bash -c 'ubiquity gtk_ui'
```
Kamalakar

Thanks, useful command, I will try it the next time Ubiquity is borked  :)

---


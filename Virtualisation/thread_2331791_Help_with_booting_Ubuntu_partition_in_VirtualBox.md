---
title: "Help with booting Ubuntu partition in VirtualBox"
date: 2016-07-25
forum: Virtualisation
---

### Post by TestTestington on 2016-07-25
I have a notebook which I duel boot Windows 10 and Ubuntu 16.04, and I want to boot my Ubuntu partition in VirtualBox on Windows host. I did a lot of Googling, but I am stuck.

So I've created the ubuntu_parititon.vmdk file which points to my physical disk and ubuntu partition but when I boot up the VM I get "FATAL: No bootable medium found! System halted." I found one guide that suggest making a grub iso to boot off, but I can't follow the steps because it refers to a i386-pc dir and I only have x86_64-efi dirs.

I am quite clueless when it comes to EFI and Linux, and Grub so would really appreciate some help.

---

### Post by deepakdeshp on 2016-07-27
Here is a step by step guide.
[https://www.unixmen.com/install-ubuntu-14-04-3-lts-virtualbox/](https://www.unixmen.com/install-ubuntu-14-04-3-lts-virtualbox/)

---

### Post by MAFoElffen on 2016-07-27
Please go into more detail into what you are trying to do, because it sounds like you are trying to mix apples and oranges.

In a dual boot, a hypervisor, such as VirtualBox is not used. In a type 2 hypervisor, you do-not do physical disk as a system disk. Do you have me wondering what you are trying to accomplish.

---


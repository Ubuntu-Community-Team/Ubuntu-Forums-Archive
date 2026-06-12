---
title: "Booting Ubuntu 9.10-Xen kernel"
date: 2009-12-18
forum: Virtualisation
---

### Post by shadowers on 2009-12-18
I have installed the Xen kernel for Ubuntu, and when I try to boot it, it says "You must load the kernel first."  What do I do?

---

### Post by falconindy on 2009-12-18
You should read up on how hypervisors work. You'll need one.

[http://en.wikipedia.org/wiki/Hypervisor](http://en.wikipedia.org/wiki/Hypervisor)

---

### Post by shadowers on 2009-12-18
I'm fairly sure I already have the hypervisor installed.

---

### Post by falconindy on 2009-12-18
Then you need to boot that, not the xen kernel itself.

---

### Post by shadowers on 2009-12-18
Okay, I just looked to make sure the Hypervisor is installed and it is.  So how would I boot it?

---

### Post by falconindy on 2009-12-18
There should be a boot image included somewhere in the install that needs to be given an entry in GRUB. You're on your own here, because I use a more civilian VM method (and I certainly don't use Grub2).

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

---

### Post by shadowers on 2009-12-18
Alright, thanks for the help.  I do have the entry already, so now to figure why it wouldn't boot it...

---

### Post by weisunding on 2010-03-10
Add the bold line to your /boot/grub/grub.cfg

multiboot /boot/xen-xx.gz
module /boot/vmlinuz-xen-xxx
**module /boot/initrd.img-xxxx**

---

### Post by blieb on 2010-03-15
Where did you get the xen kernel? it is not in the packages, only the hypervisor is?

---

### Post by blieb on 2010-03-15
Oops nevermind, I see it is possible to steal the kernel from debian. I hope they will add in ubuntu 10.4 (LTS) the xen kernels again. :(

---


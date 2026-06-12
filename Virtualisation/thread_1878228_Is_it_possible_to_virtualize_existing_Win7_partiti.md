---
title: "Is it possible to virtualize existing Win7 partition into an VM in 11.10?"
date: 2011-11-09
forum: Virtualisation
---

### Post by martialartist81 on 2011-11-09
This is a huge, wide-ranging question, and I realize that.  However, after some initial searching and digging, I'm curious to find out what others recommend (if it's possible).

Here's what I'd like to do, be able to take my existing Win7, turn it into a VM (whichever tool you'd recommend to use in Ubuntu 11.10) and access/use it within running 11.10 on my Laptop.  Both 11.10 and the Win7 partition in question run on my ASUS laptop (for work).  I want to be able to stay native into Linux but be able to run everything I have to run for work (which unfortunately, requires me in Win7).

Like I said, I realize this is a huge/sweeping possibility in responses, but I'd like to see what others are recommending I do/try to get this to work (again, if possible).

Thanks all!

---

### Post by Zeta-K on 2011-11-09
Didn't read much into it, but might help:
[http://www.softpanorama.org/VM/conversion_of_harddrive_partition_into_virtual.shtml](http://www.softpanorama.org/VM/conversion_of_harddrive_partition_into_virtual.shtml)

---

### Post by haqking on 2011-11-09
Use [clonezilla]("www.clonezilla.org") to take clone of your existing drive/partition.

Then create a VM and clone it back into the VM.

That way you have a backup in the image, and also a running copy in your VM for testing.

It is fairly straight forward to achieve.

Peace

---

### Post by martialartist81 on 2011-11-09
Brilliant!  Thanks lads!

---

### Post by teeks99 on 2011-11-10
It *should* be possible (with kvm/libvirt) without having to resort to cloning your partition.

I use virt-manager to create a new VM, then specify the partition that I want to use (/dev/sda3) or possibly just the drive (/dev/sda).  If you do use just the drive, then you need to be sure to select windows at the grub menu, if it goes ahead and boots the system you already have running you're filesystem will probably  become read-only on you, as filesystems don't like being mounted twice.  

That said, I haven't had any luck actually starting windows like this (I can start another instance of ubuntu just fine). I believe my problem is some windows drivers, as when I get part of the way through the boot-process I get a blue screen.  With luck you're windows install might be more robust than mine and it would work without issue.

---

### Post by Sightes on 2011-11-12
well yesterday i tried that , but :( wont work , i use vmware for virtualize an a real partition with w7 , but when load , the windows say something related with drivers problems and sistem problems :/

---


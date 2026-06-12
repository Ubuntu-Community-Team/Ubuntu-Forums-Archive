---
title: "How to make an Emergency boot disk or CD"
date: 2011-06-17
forum: Server Platforms
---

### Post by leegold on 2011-06-17
Hi,

I have Ubuntu Server 10.04 LTS. Is there a way to make an emergengy boot CD or even floppy disk? BTW, I will install a separate boot partition on the server.

I need a way if the boot mechanism gets hosed I can still boot into the system. I just lost a bootable system with some madness having to do with LVM2. I had a separate non LVM /boot and it still happened to me. I NEVER want this to happen again.

Adding to the confusion is grub vs. grub2 - I never really know if what is recommended to do is obsolete or not. I assume an upgraded 10.04 will use Grub2(?)

I don't want a live disk how-to. I want to learn how to make an emergeny boot disk that's configured to boot my existing system - there are many confusing obfuscated web sites when I search for how.

Could someone link me to a clear, consise way to do this?

Thanks,

Lee G.

---

### Post by ruffEdgz on 2011-06-17
Well, if you system is 'broken', how can an emergency disk boot up your system when its broken?

Whenever a server of mine has LVM problems, grub problems, etc... I do keep a Live CD handy so I can always boot into that, mount my server hard drive (if I can) and fix what I need from there.

One thing you can do is set your timeout for GRUB to 10 seconds, and when you are at your GRUB menu, change your kernel parameters so you boot into 'single' user mode and boot into your system as root.

Does anyone else do emergencies differently or more efficiently as I would like to know if my way of doing this is outdated ;)

---

### Post by ajgreeny on 2011-06-17
It may be worth having a cd (or floppy if you really want) with supergrub on it.  That should allow you to boot to a system that is not broken, but where for some reason grub has become corrupt.

However it should also be possible to restore grub with a ubuntu live CD, even if you are using a server edition, so it is worth having one of those available as well.  make sure you have the right live CD version as grub has changed with ubuntu versions.

---

### Post by Lars Noodén on 2011-06-18
The live Ubuntu CD should do it.  There are also live admin distros like [Finnix](http://www.finnix.org/) with lots of utilities.

---


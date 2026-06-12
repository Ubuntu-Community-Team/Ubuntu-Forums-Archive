---
title: "can I clone a Windows VM disk into a real partition"
date: 2010-03-25
forum: Virtualisation
---

### Post by st_john_smith on 2010-03-25
I have a nicely preconfigured VM disk image (Windows XP) that I would like to clone onto a real physical partition to use it for dual booting my machine.

I found lots of discussion threads on doing the other way: from a partition to a vm disk, but I need to really boot from the resulting disk.

Obviously, just copying the files does not work - I guess, windows needs some magical stuff...

One more thing that might make it harder: the vm disk is larger than the physical drive. 
I tried to use partimage, but this does not work on different sized target disk.
(and yes, the partition is large enough to actually hold all the files from the vm disk)

I am on Ubuntu 9.10 with VMWare Workstation 6.5.

Anyone ever did that?

---

### Post by codfather on 2010-03-25
Have a look here, but v2p is the principal you are after.

[http://www.vmware.com/support/v2p/index.html]("http://www.vmware.com/support/v2p/index.html")

Nick

---

### Post by altometer on 2010-03-25
you can compact the vdi or .img but it won't do you any good. It screws up windows when you change the HD size.

I would be glad to be proven wrong.

While it is possible,*use a utility from Hiren's boot cd 10.2* the Virtual file needs to be the same size, or smaller than the physical disc for it to work correctly.

-N

---

### Post by vel_tins on 2010-04-13
I am also interested in this theme.
But the links, provided above, are very old and outdated.
What I have:
Windows 7 Image running in VMWARE 7 (about 15 GB size)
Ubuntu 9.10 with **legacy Grub1 not Grub 2** in MBR
An empty partition (hd0,1) with 50 GB size.
Next step: mounting the VMware Image under Karmic (with Vmware)
The,n I think I can copy (rsync) or clone using partimage Win 7 onto this empty partition. (hd0,2)
Then put the Partition into menu.lst.
Could this work?
I did the same with an Ubuntu VM Image, and this worked without any problems.
But I think, maybe Windows 7 has wrong pathes in the registry?
Any more help?

---


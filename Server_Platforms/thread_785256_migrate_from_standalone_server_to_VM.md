---
title: "migrate from standalone server to VM"
date: 2008-05-07
forum: Server Platforms
---

### Post by GoldWing on 2008-05-07
We want to virtualize a standalone server with VM.
-Siemens hardware
-mirrored disks
-LAMP

The new server will be a standard VM instance (on an ESX server), without mirroring. Also the size of the disks will be much bigger
We will create an image of the server and use this as the base for the VM instance. 

Questions:
-How can I resolve the 'unmirroring' with the copy and the fact that the new disks will be much bigger ?
-we will probably need to reconfigure the NIC's ?
-what other problems can I expect ?
-someone has a good tutorial for this ?

Would it be better (and easier) to start from scratch ? I know a lot of special things need to be installed, like a pdfconverter. It is for a tool called KnowledgeTree.


Thanks.

---

### Post by yogensha on 2008-05-07
I've virutalized a couple of Linux boxes into ESX and the disk is probably the easiest thing to deal with.  I basically booted the target VM with a livecd, prepared the disk (partitioning, mostly) and then did something like:

dd if=/dev/sda1 | ssh root@targetvm 'dd of=/dev/sda1'

...which bascially copies one partiton to the other over the network.  This basically takes care of 'unmirroring' your array.

Getting a bootable kernel was a bit more difficult, but as I recall it was mostly related to issues with ESX interacting with recent x86_64 kernels.

You'll also need to install a boot loader at some point.

Getting the NICs to work is mostly a matter of making sure the kernel supports the virtualized nics.  ESX uses intel EE Pro gigabit nics, which are very widely supported.  I'm very new to Ubuntu, so I can't be sure, but I imagine the nics will work "out of the box".

Starting from scratch has its own issues.  It depends on your application and your level of comfort with each option.

You might note that VMware doesn't officially support Ubuntu, so if you have difficulties, they may not be able to assist you.

Best of luck!

---


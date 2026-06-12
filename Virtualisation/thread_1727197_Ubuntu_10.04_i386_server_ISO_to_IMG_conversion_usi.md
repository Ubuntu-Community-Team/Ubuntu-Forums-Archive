---
title: "Ubuntu 10.04 i386 server ISO to IMG conversion using QEMU"
date: 2011-04-12
forum: Virtualisation
---

### Post by karthik_h on 2011-04-12
Hello all,

I'm trying to convert a ubuntu server ISO to a virtual disc image in order to deploy it in a Opennebula cloud environment. I followed the procedure mentioned at [http://en.wikibooks.org/wiki/QEMU/Images](http://en.wikibooks.org/wiki/QEMU/Images) I initially created a blank img file using the following command. 
$qemu-img create -f qcow2 ubuntu.img 2G 
And then I tried to use the ubuntu ISO to install ubuntu in to the img file created above using the following command. 
$qemu -m 512 -hda ubuntu.img -cdrom ubuntu-10.04.2-server-i386.iso -boot d 
The only thing I see after this is init kbd. I waited for about 25-30 min without any improvement. 
The underlying processor is Intel Xeon 5640 processor. Operating system installed is Ubuntu 64 bit 10.10 server edition.

I have searched in google and went through a few posts in here as well but did not see some thing very relevant to this issue. Could someone please help me find my mistake.

Thanks.

---

### Post by teeks99 on 2011-04-13
I don't know a ton about open nebula, but does it have the ability to mount a virtual CD drive?  The server ISO isn't something that you can run from (unlike the live-cd), all you can do from there is install the operating system onto another disk.  I'm betting that isn't what you want a clone of.

What I recommend is to create a new VM image on a desktop machine (virt-manager with KVM is fairly easy, VirtualBox might also work).  Then load the ISO image you have as a virtual CD drive (the .img file you made is a virtual hard disk).  At this point you can install the operating system using the menus on the virt-manager screen.  Once this is done, you can deploy the working .img file to all the instances you want to run on.

---

### Post by emanhossny on 2011-08-08
actually i have the same problem, do u solved it?

---


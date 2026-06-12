---
title: "LSI MegaRaid 9240-8i Diver-Installation Issues with 10.04B1"
date: 2010-03-25
forum: Server Platforms
---

### Post by npavlica on 2010-03-25
All,
  I'm trying to install Ubuntu 10.04 Beta 1 using a MegaRaid 9240-8i SAS  controller.  Unfortunately, the current installer doesn't load the appropriate driver for it.  I've contacted LSI support, and they stated that they only support a select group of distributions, and Ubuntu isn't currently one of them.  However, the source is available from their website, and tech stated that they work with the main line kernel folks, and that there should be unofficial support in newer kernels.  What needs to be done to get support for this, and other newer 6Gb/s cards in 10.04?  

I've testing this controller with CentOS 5.4 and it works perfectly out of the box.  I'm considering a purchase of a 3ware 9750-8i after talking to LSI/3Ware, which will better support distributions like Ubuntu, but would really like to work towards getting the MegaRaid 9240 to work.  I'm sure there are many others that will need this in the coming months.

Thanks!
--Nick Pavlica

---

### Post by Moshis on 2010-09-04
Hi :

Im really interested in getting one of this for my home server ... where you able to get it running on 10.04 ?

Thanks !

---

### Post by Staffan Ericsson on 2010-10-03
LSI has released kernel additions for 10.04 now and there is work getting them into the Ubuntu Kernel.

---

### Post by gansvv on 2010-10-07
3ware 9750 driver for 2.6.32-21 kernel is available at:

[http://kb.lsi.com/KnowledgebaseArticle15881.aspx](http://kb.lsi.com/KnowledgebaseArticle15881.aspx)


Note that Ubuntu 10.04 LTS is 2.6.32.21, but Ubuntu 10.04.1 has a higher kernel version.

---

### Post by Schuby007 on 2011-01-23
Hi,

I'm planning on building a server with Ubuntu Server Edition 10.04 LTS 64bit. Will this card work out of the box or will I need to install drivers?

Also is this a host-based card or does it have a built in IOP. Do you know if it works with SSDs?

Thanks.

---

### Post by marke9 on 2011-02-16
I have a system using the SuperMicro X8DTi-LN4F motherboard and am using the motherboard's SATA controller for /boot, / and swap.  I added the 3ware 9750-8i controller to create a RAID5 array.  The OS is 10.04.1.

The 3ware BIOS recognized the card and I was able to create the array without any difficulty. But without the proper driver the system could not see the array.  Nor could the 3ware 3DM2 web interface see the controller.

The driver you cited (I used 64-bit: Ubuntu-10.04.1_kernel2.6.32-24-x64-9750.tgz) did the trick.  It's up and running nicely.  Thanks!

---


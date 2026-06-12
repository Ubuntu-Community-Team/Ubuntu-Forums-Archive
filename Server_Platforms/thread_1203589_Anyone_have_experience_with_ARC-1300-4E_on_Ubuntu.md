---
title: "Anyone have experience with ARC-1300-4E on Ubuntu?"
date: 2009-07-03
forum: Server Platforms
---

### Post by Plecebo on 2009-07-03
This item: [http://www.newegg.com/Product/Product.aspx?Item=N82E16816151058](http://www.newegg.com/Product/Product.aspx?Item=N82E16816151058)

4 port eSATA card having trouble getting it working under Ubuntu. 

The card detects the drives in the bios, but when it comes to Ubuntu the drives are no where to be found.

I've tried the following commands: 
```
fdisk -l
dmesg | less
```

Those commands only show the OTHER devices (system hard drive, and dvd drive). No info about the drives in the external enclosure. 

The card comes with drivers for debian, but none for ubuntu :( I tried to install the drivers for debian, but it seemed like the kernel modules were not loading. I don't have much experience with drivers + linux (Personally I find this hilarious, since you basically can't even approach an install of Windows without a stack of drivers), so it is possible that it is something stupid simple. 

I have another esata card that came with my enclosure, and it works, but it is only pciexpress 1x (which with 8 drives can get maxed out pretty fast). 

Anyway, the card indicates it officially supports Suse, and RHEL and Fedora so I am downloading those OS's to see if they detect the drives and perhaps I'll switch :(

---

### Post by talon99 on 2009-07-15
I have a similar card, The Areca ARC-1300IX-16.
 
Like you, I tried the Debian drivers without success. 
 
dmesg gives me the following error:
 
arcsas: disagrees about version of symbol struct_module.
 
I tried sending and email to the areca support but have not recieved a response.
 
If I hear anything, I will let you know.
 
Peter

---

### Post by Plecebo on 2009-07-15
Thanks for the response. After goofing around with the device for a few days I decided to throw in the towel and go with another device (San Digital): [http://www.newegg.com/Product/Product.aspx?Item=N82E16816111069](http://www.newegg.com/Product/Product.aspx?Item=N82E16816111069)

The San Digital is detected without drivers in Ubuntu 9.04 (didn't try other versions) and works without an issue. 

It was a little more then the Areca but given the fact that it works in Kernel and has an 8x interface I figured it was well worth the extra money. 

I was using the esata card that came with my enclosure before I got the San Digital card and when I dropped in the San Digital card I noticed a marked increase in performance transferring to and from the array.

---

### Post by lostlinuxlizard on 2009-11-24
hi all.. I was able to get this working.. sort of.  it seems to crash with IO errors, but who knows, that may be my config or build... the basic idea seems sound, and I do get some IO to some disks...
download the 2.6.31.6 kernel, grab it from kerne.lorg..
apply this patch
[http://patchwork.kernel.org/patch/46202/](http://patchwork.kernel.org/patch/46202/)
follow basic  kernel building instructions, create initrd, etc... and you should be good.  under debian stable I got away with
make mrproper
make oldconfig  # answer  default to everything
make && make modules
make modules_install && make install
update-initramdisk
update-grub
reboot to the new kernel...

---

### Post by blevin on 2010-09-15
updating an old thread, I realize that.

just bought this areca card but cannot get it to work with ubuntu.  tried the kernel patch for mvsas and while it compiled, it did not help.

also tried the very latest kernel from kernel.org (2.6.35.4) and that did not help, either.

what may be the issue is that I'm using a 4bay port multiplier (Silicon Image 3726 based).  that works more or less ok with the included si-image 3132 card and also seems to work ok in jbod with the old jmicron jmb363 esata card.

I know my 4bay P.M. chassis works fine and the drives are fine.  I'm not using raid, again, just jbod.

syslog shows this kind of stuff:

----------------------
```

[  220.761192] drivers/scsi/mvsas/mv_sas.c 1388:found dev[0:5] is gone.
[  220.761254] drivers/scsi/mvsas/mv_sas.c 1388:found dev[1:5] is gone.
[  220.761658] mvsas 0000:01:00.0: PCI INT A disabled
[  306.787347] mvsas 0000:01:00.0: mvsas: driver version 0.8.2
[  306.787365] mvsas 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  306.787372] mvsas 0000:01:00.0: setting latency timer to 64
[  306.789240] mvsas 0000:01:00.0: mvsas: PCI-E x4, Bandwidth Usage: 2.5 Gbps
[  309.030012] drivers/scsi/mvsas/mv_sas.c 1224:port 0 attach dev info is 0
[  309.030016] drivers/scsi/mvsas/mv_sas.c 1226:port 0 attach sas addr is 0
[  309.140010] drivers/scsi/mvsas/mv_sas.c 1224:port 1 attach dev info is 0
[  309.140013] drivers/scsi/mvsas/mv_sas.c 1226:port 1 attach sas addr is 0
[  309.300018] mvsas 0000:01:00.0: Phy2 : No sig fis
[  309.510027] drivers/scsi/mvsas/mv_sas.c 1224:port 3 attach dev info is 200
[  309.510030] drivers/scsi/mvsas/mv_sas.c 1226:port 3 attach sas addr is 3
[  309.510035] scsi10 : mvsas
[  309.510302] drivers/scsi/mvsas/mv_sas.c 2081:port 2 ctrl sts=0x199800.
[  309.510306] drivers/scsi/mvsas/mv_sas.c 2083:Port 2 irq sts = 0x11081
[  309.510312] drivers/scsi/mvsas/mv_sas.c 2109:phy2 Unplug Notice
[  309.510316] drivers/scsi/mvsas/mv_sas.c 2136:notify plug in on phy[2]
[  309.510318] drivers/scsi/mvsas/mv_sas.c 2161:plugin interrupt but phy2 is gone
[  309.511109] drivers/scsi/mvsas/mv_sas.c 378:phy 3 byte dmaded.
[  309.517496] drivers/scsi/mvsas/mv_sas.c 1388:found dev[0:5] is gone.
[  309.517613] ata11.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  309.517655] ata11.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  309.517658] ata11: limiting SATA link speed to 1.5 Gbps
[  309.517662] ata11.00: limiting speed to UDMA7:PIO5
[  309.517702] ata11.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  309.517705] ata11.00: disabled
[  309.517725] scsi_alloc_sdev: Allocation failure during SCSI scanning, some SCSI devices might not be configured

```lots of 'failed to identify' errors.

is this card usable, really?  it seems like it has not been fully tested or developed and I can't find much talk about this card for linux.

using ubuntu 9.10:

% uname -a
Linux abcdef 2.6.35.4 #1 SMP Tue Sep 14 21:40:49 PDT 2010 x86_64 GNU/Linux

---

### Post by blevin on 2010-09-17
update: not good news ;(

after an email exchange with a company employee, it seems that the driver will be 'partially open' and have some binary-only element to it.  the mv_sas driver is not going to be supported or preferred by them, for some reason.

I guess that ends that, for me at least.  there are so many other sata/sas cards out there that are fully source-based, I have no reason to go hybrid or closed-source for a LINUX device..

so that ends that.  card will be returned to vendor and I'll just use the sil image (sigh) card that everyone knows and loves ;)

---


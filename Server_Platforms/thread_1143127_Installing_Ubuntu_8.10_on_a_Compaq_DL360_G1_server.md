---
title: "Installing Ubuntu 8.10 on a Compaq DL360 G1 server"
date: 2009-04-29
forum: Server Platforms
---

### Post by guitarman on 2009-04-29
Hi everyone,
I just bought a Compaq Proliant DL360 G1 server on eBay at it's got 512Meg ram and 2x18gig SCSI disks configured in a RAID 1 using the HP SmartStart 5.50 CD that the HP tech support guy emailed me.  
I went ahead and installed Ubuntu 8.10 Server and selected LAMP to install and everything went through fine (it seemed).  However when the server reboots, it keeps on saying that there is no system disk and does not want to come up in Ubuntu.  Now for this version of server, it seems that it supports Windows 2000, NT4, Novell, RedHat 7.0-9.0 and SUSE 7.0-8.0 and VMWARE ESX 2.1 and 2.5 as well as some Solaris version.  
Are there any drivers that need to be installed so that it would work with Ubuntu - my preferred OS?  I would like it to boot directly into my new install of Ubuntu so that I can setup my website and so on.
thanks,
By the way I also tried to install CENTOS 4.4 on it (thinking that it is similar to RedHat) and the system just freezes on the initial boot of the CD and does not install anything.... at least Ubuntu installed itself.

---

### Post by r4z0r_bl4d3 on 2009-05-08
I got one of these from a local non profit. dual p3 with 1.25 GB of ram and RAID 1 18 GB 15k rpm SCSI drives.  I paid 35 bucks for it, a huge steal.

it was loaded with base Debian 4, and nothing else.  I may keep that install, seeing as installing something else is proving rather difficult. 

From the research I did this server is really tricky to get working properly.  There is no traditional BIOS, you must have a partition made to alter settings.

I would like to put vmware ESXi on there but I don't think the server supports it.  My next thought was ubuntu 9.04 with ext4 as my second choice.

I may just end up upgrading to Debian 5 and leave it at that.

And once I have the OS installed, i really don't know what role it will perform.  The hard drives are really small, but really fast.  Web server or network monitoring seems best to me.

I will post an update when I get this server configured how I want and tell of any trouble I had.

Edit. oh yeah I just remembered reading somewhere that you must install the bootloader to the first bootable flagged partition not the MBR.  So intead of installing to hd0 install to hd0,0 i.e. first partition with a bootable flag, not the master boot record, it screws up the BIOS partition that is made by the HP SmartStart cd.

** BTW first post.**

---

### Post by r4z0r_bl4d3 on 2009-05-13
Quick update.

I tried various thing after wiping out the Debian install.  Cant get anything to really boot except the SmartStart 5.50 cd.  I have tried installing from a pxe server, but that didn't work either.

My last resort is to try a different cd drive.  I have a suspicion that the cd drive in the server is faulty.

---


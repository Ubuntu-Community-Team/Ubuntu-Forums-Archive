---
title: "Suggestions for NAS System and Backups"
date: 2011-12-26
forum: Server Platforms
---

### Post by techguy817 on 2011-12-26
Hi all,

I'm trying to figure out how to handle my backup strategy. I have several Windows systems and Macs that I'd like to setup for backup to a NAS. I have a few p4 systems and was thinking of buying a raid controller and two drives for raid one. I'm not sure if Ubuntu would be best for full functionality or if freenas or openfiler would be better. I've spent quite some time trying to browse the forum but still don't have a clear answer. I think Ubuntu would be better for one thing because it can support linux cloud backup solutions where i think freenas and openfiler wont. Any additional pointers for comparison are greatly appreciated.

---

### Post by rubylaser on 2011-12-26
If you're doing a backup system with just RAID1, there's really no need for a hardware controller.  Either use mdadm on Linux or ZFS on FreeNAS.  There's no parity calculations to do, so a hardware controller is really just an unnecessary expense and an extra hardware dependency.

---

### Post by a2j on 2011-12-26
ubuntu server will do it. even without expensive raid controller. software raid will work just fine. NFS or Samba.

---

### Post by techguy817 on 2011-12-26
Thanks for the quick reply guys. So if there is no need for a hardware raid controller i will do software raid but i'll still need a pci sata controller since these p4 systems are ide only on the mainboard. Is there a sata controller that you can recommend? Also what are some pros and cons of freenas versus ubuntu for this setup on things like speed, capabilities, administration, etc?

---

### Post by rubylaser on 2011-12-26
Ubuntu is a full blown server OS, so you can install pretty much any package you'd like.  FreeNAS is striped down and can easily be installed to a thumb drive.  I've tried FreeNAS a number of times in the past and just a few months ago.  I could never get very good throughput out of it.

mdadm with some tuning can very easily saturate a gigabit connection with a few disks.

Does you board have a PCI-Express slot open?  Otherwise, you'll probably just want to pickup a 2-4 port PCI Sil based SATA controller for around $25. 

If you want a very good controller with lots of room to grow, I run IBM m1015 cards purchased from Ebay and add IT firmware.  [These]("http://www.ebay.com/itm/IBM-ServeRAID-BR10i-SAS-SATA-Controller-w-Optnl-Bracket-/270748220946?pt=LH_DefaultDomain_0&hash=item3f09d9fe12#ht_761wt_1188") are also very nice. But, for a simple 2 disk RAID1, both of these cards are major overkill :)

---

### Post by rubylaser on 2011-12-26
The only other thing I might suggest, is to take the money you where going to spend and build an expensive [AMD Zacate]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131732") based fileserver.  The P4 is going to use alot of power, and the Zacate would use significantly less while supporting 6 SATA ports.  Just another idea :)

---

### Post by techguy817 on 2011-12-26
Thanks rubylaser. I have also seen reports where freenas performance is less than adequate. Maybe its a bsd driver thing? I don't have a pci express slot in my p4 systems and would like to stick with them over new hardware. I was thinking of keeping them off and maybe doing a scheduled wake on LAN from the router.

---

### Post by rubylaser on 2011-12-26
FreeNAS uses ZFS as default now, and it's not in it's native Solaris environment, so that could be some of the issue.  And, ZFS likes to have alot of RAM.  My home Solaris 11 fileserver has 8GB of RAM in it, and really, I wish it had more like 16GB.  But, it is also able to saturate a gigabit connection with (5) 2TB Hitachi 5k3000 disks in a RAIDZ2 array.

---


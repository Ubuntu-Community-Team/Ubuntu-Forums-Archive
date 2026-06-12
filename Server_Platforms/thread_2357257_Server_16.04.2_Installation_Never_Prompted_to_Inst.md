---
title: "Server 16.04.2 Installation Never Prompted to Install Grub"
date: 2017-03-31
forum: Server Platforms
---

### Post by mgb0002 on 2017-03-31
Hello,

I'm new to Ubuntu Server and Raid, but not new to Linux.  I am trying to install Sever 16.0.2 on a machine with 4 8TB drives in Raid5 array using Intel FakeRaid.  Installation saw my "24TB" drive and partitioned as appropriate (/boot, /, /swap).  Installation went smoothly (although it did sit at 83% for about 12 hours), that is until went straight from software package selection to reboot request.  I was never prompted to install Grub (step 19 in this guide [http://www.tecmint.com/installation-of-ubuntu-16-04-server-edition/2/](http://www.tecmint.com/installation-of-ubuntu-16-04-server-edition/2/)).  Seeing as no bootloader was installed, I obviously cannot boot into the system.  I think I may be able to manually install Grub using a Live disk, but I am unable to have Ubuntu Desktop Live disk correctly recognize the Raid array.  I see all of the drives as their own size, and a"drive" that is labeled the Raid5 volume ("Volume1"), but it is only around 2TB in size, not 24TB.  

My question is:

1. Why did installation skip Grub install?

2. What do I need to do to manually install Grub?  I seems like I need to activate some packages in the Live disk, but I am not sure which ones exactly.

Thank you.

---

### Post by oldfred on 2017-03-31
Moved to sever sub-forum where those who know RAID may help.

I do not know RAID, but have some links.

 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.
15.04 or later now uses mdadm to support intel fakeraids 
 sudo mdadm --detail-platform 


User who installed fakeRAID
How to install Ubuntu 14.04 in software fakeraid RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126) 

 Does not recommend "fakeRAID"
[http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/](http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/)
[https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID](https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
"fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0
Hardware RAID drivers
[https://wiki.debian.org/LinuxRaidForAdmins](https://wiki.debian.org/LinuxRaidForAdmins)

Above assumes BIOS install, UEFI install would require ESP partition.
If BIOS install on larger gpt partitioned drives, you must have the bios_grub partition for grub to install correctly. It needs to be 1 or 2MB unformatted with bios_grub flag using parted or gparted or ef02 code if using gdisk.

---


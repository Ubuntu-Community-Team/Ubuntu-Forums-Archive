---
title: "Multiple harddisks"
date: 2016-07-01
forum: Server Platforms
---

### Post by anders20 on 2016-07-01
Hello! 

I'm trying to install some new disks into my system. 
Ubuntu Server 16.04 LTS. 

I get some problems doing it! And i can't figure it out why.. 
Disks already installed: 
1 SSD - 120GB
1 HDD - 2TB
1 HDD - 3TB
2 HDD - 3TB (trying to install - Seagate Desktop HDD 3TB 7200RPM)

System: 
INTEL Core i7-5820K 3,3GHz LGA2011 15MB
[ASRock X99M Extreme 4, Socket-2011-3]("http://www.digitalimpuls.no/PC-komponenter/Hovedkort/Socket-2011-3/ASRock/ASRock-X99M-Extreme-4-Socket-2011-3-MATX-X99-4xDDR4-3xPCI-E-M2-x4130159-p0000089875")
Cooler Master V 750W

When i need a new disk i get this message: 
Welcome to emergency mode! 
VFS: Can't find ext4 filesystem. 
When i use the command lsblk -o NAME,FSTYPE,SIZE it seems like that new disk takes one of the already installed disks name, and crashes? 
So now my 3TB disk, only shows as 700-800GB when i try to format it in windows, to start from scratch. 

Please tell me that there is someone out there that have been true the same, and have a quick and easy solution! 
Thanks alot for your time!

---

### Post by oldfred on 2016-07-01
Are you installing in UEFI mode?
Windows only installs to gpt partitioned drives with UEFI and with 3TB drives you must use UEFI. MBR has a max of 2TiB.

What SATA port order are you installing drives? Best to have main boot drive in SATA0 and use ports in order. I had skipped a port and had issues with flash drive that was sde when plugged in and sdb on reboot. Similar issue with newer UEFI system where I had DVD inbetween the two hard drives.

Post this:
sudo parted -l

---

### Post by anders20 on 2016-07-01
> **oldfred said:**
> Are you installing in UEFI mode?
Windows only installs to gpt partitioned drives with UEFI and with 3TB drives you must use UEFI. MBR has a max of 2TiB.

What SATA port order are you installing drives? Best to have main boot drive in SATA0 and use ports in order. I had skipped a port and had issues with flash drive that was sde when plugged in and sdb on reboot. Similar issue with newer UEFI system where I had DVD inbetween the two hard drives.

Post this:
sudo parted -l
[COLOR=#000000]Thanks for that quick reply. I even tryed to install ubuntu on that 3TB drive just to be sure everything was correct, and when i started ubuntu it showed as a 2,7TB, then i installed it into windows again and used Minitool Partition to just clear the disk and make it ext3, it still showed as 700-800GB. - and i made sure it was GPT. [/COLOR]

[COLOR=#000000]Do you want me to put the disks inside my server, and then do parted -l ? Anyway here is without the new disk installed: [/COLOR][http://pastebin.com/mCL703gc](http://pastebin.com/mCL703gc)
[COLOR=#000000]SSD disk(OS) is in sata 0 i think, worstcase sata 1.[/COLOR]

I have tryed to use different sata ports on my motherboard, the same problem occurs.  
When i remove the new disks and just leave the once i had installed (120GB, 2TB, 3TB) everyone starts as normal.

Tried both the disks, same problem. Hope you got some ideas to what i can try next :)

The disks installed, that works i used this guide to install: 
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) (command line).

---

### Post by oldfred on 2016-07-01
You show drives as 'loop'. That usually is formatting the drive, not the partition. And you show ext3, not ext4 which have been default for Ubuntu for years. Only 6 or 7 years ago was it suggested to stay with ext3 until ext4 issues were resolved.
Only in some special cases may you have a drive formatted, you need to partition drives. LVM is normally inside a partition, so that should not be the issue, but do not know all the details of LVM.

In BIOS mode you can use Something Else install option and choose which drive to install grub into. That should be same drive as Ubuntu install.
With UEFI grub only installs to ESP - efi system partition on whatever drive is seen as sda. And you must have the ESP on sda.

---

### Post by anders20 on 2016-07-02
> **oldfred said:**
> You show drives as 'loop'. That usually is formatting the drive, not the partition. And you show ext3, not ext4 which have been default for Ubuntu for years. Only 6 or 7 years ago was it suggested to stay with ext3 until ext4 issues were resolved.
Only in some special cases may you have a drive formatted, you need to partition drives. LVM is normally inside a partition, so that should not be the issue, but do not know all the details of LVM.

In BIOS mode you can use Something Else install option and choose which drive to install grub into. That should be same drive as Ubuntu install.
With UEFI grub only installs to ESP - efi system partition on whatever drive is seen as sda. And you must have the ESP on sda.

Thanks! But i'm not sure i understand what to do to solve my problem. Is there a guide or something that i can follow to fix this? 
Or do i  need to uninstall everything and start from scratch? - Why did Ubuntu Server install ext4 as default, if it's not recommended?

---

### Post by howefield on 2016-07-02
Thread moved to the "*Server Platforms*" forum.

---

### Post by oldfred on 2016-07-02
I would re-install drives and make sure SSD is in first port SATA0 so it is seen as sda in Ubuntu and hd0 in grub & UEFI.
I would then reinstall in UEFI boot mode. If you want LVM that is fine, I just have never used it and do not know details.

Your ext3 with loop mount are your other 3TB drives, not the Ubuntu install SSD drive. Since you ran Boot-Repair you must also have live installer with gparted. So I would use that or download the latest version of gparted ISO and use that to format other drives.

How are you planning to configure drives, one large LVM, RAID, or just use drives as separate drives? I do not know server configurations, just use of multiple drives.

---

### Post by anders20 on 2016-07-03
> **oldfred said:**
> I would re-install drives and make sure SSD is in first port SATA0 so it is seen as sda in Ubuntu and hd0 in grub & UEFI.
I would then reinstall in UEFI boot mode. If you want LVM that is fine, I just have never used it and do not know details.

Your ext3 with loop mount are your other 3TB drives, not the Ubuntu install SSD drive. Since you ran Boot-Repair you must also have live installer with gparted. So I would use that or download the latest version of gparted ISO and use that to format other drives.

How are you planning to configure drives, one large LVM, RAID, or just use drives as separate drives? I do not know server configurations, just use of multiple drives.

Thanks for your quick replys. 

This is a plex server so i'm not sure what is best, but i'm not gonna use RAID. Was just thinking separate disks to store files on.
SSD - OS and Plex Media Server
HDD - All files, none RAID.

---

### Post by oldfred on 2016-07-03
Now that drives are huge, I typically do not like one very large partition. More difficult to backup and repair when issues. But is a media server probably better to have a large partition.
But you need to partition as gpt and then create one large partition.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
        [https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT) 
    
All my drives are smaller, but I use gpt. With large drive gpt should be default.
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

### Post by darkod on 2016-07-03
As oldfred already mentioned, the large disks show as loop table, not gpt. And you are confusing me by mentioning windows and minitool partition and creating ext3 from windows, etc, etc... Forget that and DO NOT try to use windows for creating linux partitions. I wouldn't trust it, although there are good third party tools I guess... But why, when you have everything you need inside ubuntu. Imagine the partition is not created good because it was done in windows and errors start showing up after you have 5TB of data on your server...

So, lets go back to basics... The loop table will need to be removed... Do you already have data on the big disks???

---

### Post by anders20 on 2016-07-03
> **darkod said:**
> As oldfred already mentioned, the large disks show as loop table, not gpt. And you are confusing me by mentioning windows and minitool partition and creating ext3 from windows, etc, etc... Forget that and DO NOT try to use windows for creating linux partitions. I wouldn't trust it, although there are good third party tools I guess... But why, when you have everything you need inside ubuntu. Imagine the partition is not created good because it was done in windows and errors start showing up after you have 5TB of data on your server...

So, lets go back to basics... The loop table will need to be removed... Do you already have data on the big disks???

I do not have data on the disks(anymore), so I can basically do whatever you want me to do :D
I'm ready!

---

### Post by darkod on 2016-07-03
Post the output of the following commands (you need to run them on the server, over ssh or similar):
```
sudo parted -l (small L)
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
```

Also, confirm for us if you want to use one big storage, because you will need to configure a LVM LV (logical volume) for that. Otherwise the disks will remain as separate data storage, not as one big joined storage.

---

### Post by anders20 on 2016-07-03
> **darkod said:**
> Post the output of the following commands (you need to run them on the server, over ssh or similar):
```
sudo parted -l (small L)
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
```

Also, confirm for us if you want to use one big storage, because you will need to configure a LVM LV (logical volume) for that. Otherwise the disks will remain as separate data storage, not as one big joined storage.

Yes i wan't to use one big joined storage. 
Info without the disks installed. Let me know if you need the info with the disks installed.

parted -l : [http://pastebin.com/1ghW3Lm7](http://pastebin.com/1ghW3Lm7)
pvdisplay: [http://pastebin.com/NzPDnvKe](http://pastebin.com/NzPDnvKe)
vgdisplay: [http://pastebin.com/pNzqXHEV](http://pastebin.com/pNzqXHEV)
lvdisplay: [http://pastebin.com/m1gYy1YA](http://pastebin.com/m1gYy1YA)

---

### Post by darkod on 2016-07-03
OK, so you are using LVM and you have two LVs, one for root and one for swap.

What do you mean "without the disks installed"? I see one 3TB disk (sda) and one 2TB disk (sdc). Is that all the storage you want to use? If you want to add more disks install all of them in the machine and run the parted command again to show us all disks.

---

### Post by anders20 on 2016-07-03
> **darkod said:**
> OK, so you are using LVM and you have two LVs, one for root and one for swap.

What do you mean "without the disks installed"? I see one 3TB disk (sda) and one 2TB disk (sdc). Is that all the storage you want to use? If you want to add more disks install all of them in the machine and run the parted command again to show us all disks.

Okay, will do. Yes i have 2 more 3TB disks that i want to use. I don't have them plugin in because i get emergency mode when they are plugged in.
Give me some time and i'll install the disks and post it again.

---

### Post by anders20 on 2016-07-03
> **darkod said:**
> OK, so you are using LVM and you have two LVs, one for root and one for swap.

What do you mean "without the disks installed"? I see one 3TB disk (sda) and one 2TB disk (sdc). Is that all the storage you want to use? If you want to add more disks install all of them in the machine and run the parted command again to show us all disks.

[COLOR=#000000]parted -l : 
[/COLOR][IMG]https://scontent.fsvg1-1.fna.fbcdn.net/v/t34.0-12/13599596_10157157251345192_1257957389_n.jpg?oh=43cb397395d56fd1164df1c2b306a4b0&oe=577C38CD[/IMG][COLOR=#000000]
 [/COLOR][IMG]https://scontent.fsvg1-1.fna.fbcdn.net/v/t34.0-12/13595517_10157157241050192_1352274503_n.jpg?oh=6dcad22ff05971dc5bec89126abe5543&oe=577B1458[/IMG]
[COLOR=#000000]pvdisplay: [/COLOR]Unchanged
[COLOR=#000000]vgdisplay: [/COLOR]Unchanged
[COLOR=#000000]lvdisplay: [/COLOR]Unchanged

To sum up! 
I have 1 SSD - OS installed.
2 HDD with 2TB and 3TB that works. 
2 HDD with 3TB that won't work, i just get right to emergency mode.

---

### Post by oldfred on 2016-07-03
Is this a Gigabyte motherboard or a motherboard with ASmedia ports.
Do not use the Asmedia ports or the drives will not work.
And if Gigabyte you need some settings for IOMMU.

---

### Post by anders20 on 2016-07-03
> **oldfred said:**
> Is this a Gigabyte motherboard or a motherboard with ASmedia ports.
Do not use the Asmedia ports or the drives will not work.
And if Gigabyte you need some settings for IOMMU.

This is my motherboard:
[ASRock X99M Extreme 4, Socket-2011-3]("http://www.digitalimpuls.no/PC-komponenter/Hovedkort/Socket-2011-3/ASRock/ASRock-X99M-Extreme-4-Socket-2011-3-MATX-X99-4xDDR4-3xPCI-E-M2-x4130159-p0000089875")

---

### Post by oldfred on 2016-07-03
This was an older Asrock, you may want to check manual details to see if yours has Asmedia ports and be sure not to use them.

 Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

---

### Post by anders20 on 2016-07-04
> **oldfred said:**
> This was an older Asrock, you may want to check manual details to see if yours has Asmedia ports and be sure not to use them.

 Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

From the Manual: 
Storage 
&#8226;     10 x SATA3 6.0 Gb/s Connectors, support RAID (RAID0, RAID 1, RAID 5, RAID 10 and Intel Rapid Storage 13),NCQ, AHCI, Hot Plug and ASRock HDD Saver Technology(S_SATA3_3 connector is shared with the eSATA port)(S_SATA3_2 connector is shared with Ultra M.2 Socket)* RAID is supported on SATA3_0 ~ SATA3_5 ports only.
&#8226;     1 x eSATA Connector, supports NCQ, AHCI and Hot Plug
&#8226;     1 x Ultra M.2 Socket, supports M.2 SATA3 6.0 Gb/s moduleand M.2 PCI Express module up to Gen3 x4 (32 Gb/s)

---

### Post by darkod on 2016-07-04
This "emergency mode" you mention, I assume that is something from the motherboard or BIOS??? Ubuntu should not complain just because you installed few more disks.

Double check that you are using SATA controller in plain AHCI mode, no RAID no JBOD, nothing of that kind from the MB options... You only need the MB to pass the disks as plain AHCI disks to the OS, ubuntu will do the rest.

If the emergency mode message is from the MB, have you tried contacting their support for an explanation?

I am still confused why some of the disks have a loop table... That can be sorted out easily, assuming you are not using some option from the MB that is actually doing it.

---

### Post by anders20 on 2016-07-15
> **darkod said:**
> This "emergency mode" you mention, I assume that is something from the motherboard or BIOS??? Ubuntu should not complain just because you installed few more disks.

Double check that you are using SATA controller in plain AHCI mode, no RAID no JBOD, nothing of that kind from the MB options... You only need the MB to pass the disks as plain AHCI disks to the OS, ubuntu will do the rest.

If the emergency mode message is from the MB, have you tried contacting their support for an explanation?

I am still confused why some of the disks have a loop table... That can be sorted out easily, assuming you are not using some option from the MB that is actually doing it.

SORRY for the late reply, i have been on holiday and just got back... 
emergency mode is not something from my motherboard or BIOS, this is Ubuntu. SSH is not working when i get this "error". 
[IMG]https://scontent.fsvg1-1.fna.fbcdn.net/v/t35.0-12/13702433_10157207851495192_2027457990_o.jpg?oh=aa0be321fc20cd7d46b09c7c5290d3ee&oe=578BEF00[/IMG]

Just checked my bios and all my SATA3 Storage Configuration is set on AHCI. 

loop table, don't think it's my MB, at least nothing i have said i would like.

---

### Post by anders20 on 2016-07-21
Still need help to fix this :(

---

### Post by darkod on 2016-07-21
According to this [http://unix.stackexchange.com/questions/279521/ubuntu-16-04-emergency-boot-mode](http://unix.stackexchange.com/questions/279521/ubuntu-16-04-emergency-boot-mode) it can stop in Emergency Mode if it tried to mount not existing device.

Are you sure your /etc/fstab is correct? Take a look at it and if needed leave only the root and swap partition enabled. Comment out anything else. Then try booting with all disks attached and see what happens.

You will have to redo the disks anyway, as we discussed. But lets get to a stage where the system boots with all the disks attached (but not all mounted) first.

---

### Post by Vegan on 2016-07-21
> **anders20 said:**
> Hello! 

I'm trying to install some new disks into my system. 
Ubuntu Server 16.04 LTS. 

I get some problems doing it! And i can't figure it out why.. 
Disks already installed: 
1 SSD - 120GB
1 HDD - 2TB
1 HDD - 3TB
2 HDD - 3TB (trying to install - Seagate Desktop HDD 3TB 7200RPM)

System: 
INTEL Core i7-5820K 3,3GHz LGA2011 15MB
[ASRock X99M Extreme 4, Socket-2011-3]("http://www.digitalimpuls.no/PC-komponenter/Hovedkort/Socket-2011-3/ASRock/ASRock-X99M-Extreme-4-Socket-2011-3-MATX-X99-4xDDR4-3xPCI-E-M2-x4130159-p0000089875")
Cooler Master V 750W

When i need a new disk i get this message: 
Welcome to emergency mode! 
VFS: Can't find ext4 filesystem. 
When i use the command lsblk -o NAME,FSTYPE,SIZE it seems like that new disk takes one of the already installed disks name, and crashes? 
So now my 3TB disk, only shows as 700-800GB when i try to format it in windows, to start from scratch. 

Please tell me that there is someone out there that have been true the same, and have a quick and easy solution! 
Thanks alot for your time!

Check if your BIOS SATA ports are set to AHCI mode. You will then need to clean the disk (wipe the partition tables) and repartition it with GPT. Then you will need to use ext4 to be able to format the disk.

I have seen problems like this with RAID cards and older BIOS based machines a lot.

---

### Post by darkod on 2016-07-21
Also, one option that might be the fastest way, is to create a cd or usb with ubuntu desktop image, boot with it into live mode (Try Ubuntu), not from your OS disk.

Then create new gpt tables on all big disks (except the SSD). I believe you mentioned there is no important data on the disks. That means you can delete the existing tables and create new gpt tables.

See if that helps you boot your server from the OS disk. After that it shouldn't go into emergency mode.

---

### Post by anders20 on 2016-07-27
> **darkod said:**
> According to this [http://unix.stackexchange.com/questions/279521/ubuntu-16-04-emergency-boot-mode](http://unix.stackexchange.com/questions/279521/ubuntu-16-04-emergency-boot-mode) it can stop in Emergency Mode if it tried to mount not existing device.

Are you sure your /etc/fstab is correct? Take a look at it and if needed leave only the root and swap partition enabled. Comment out anything else. Then try booting with all disks attached and see what happens.

You will have to redo the disks anyway, as we discussed. But lets get to a stage where the system boots with all the disks attached (but not all mounted) first.

This is my /etc/fstab: [http://pastebin.com/iMcVG5H6](http://pastebin.com/iMcVG5H6)
/dev/sda and sdc works like a charm, but not sdd and sde1.
If it's possible to do this without cleaning the disk that would be the best, it's alot of Movies and Tv-series. 

So you wan't me to comment out anyevery thing else beside the UUID, /dev/mapper?
Plug in the disks and reboot and check if that works?

---

### Post by darkod on 2016-07-27
1. Is that /boot partition in fstab still available? I assume yes, you probably installed with LVM and separate /boot partition.

2. Do you have data on all the big disks? Or some of them are empty that you want to install into the system now?

We already discussed that the partition tables on the data disks are a mess, and there is no way to redo them without deleting the content. But, if you can manage to keep the content on three disks and have the fourth empty (it doesn't matter which one of the four), you can sort out its partition table first, then move to it the data from another disk, do that one, etc, etc...

That is what I would do.

One thing you can try is whether you can see all disks from live mode. Prepare cd or usb with ubuntu desktop image and boot it into live mode from it. Then check if you can read all disks, and that way you can move data around too and make this happen. But we are coming back to the question whether all disks are really, really full, or you can work with some free space to move the data around and recreate new blank partition tables.

I think where you went wrong is using the whole disk as a device. You NEVER use the disk for formatting, you create partition on it and format them with the filesystem you want to use. I think that's why it shows as loop table. If you keep it as it is, even if you can boot the system with all disks connected, it's a disaster waiting to happen sooner or later... But it's your computer and your data, it depends on you if you want to fix the tables or not...

---

### Post by anders20 on 2016-07-27
> **darkod said:**
> 1. Is that /boot partition in fstab still available? I assume yes, you probably installed with LVM and separate /boot partition.

2. Do you have data on all the big disks? Or some of them are empty that you want to install into the system now?

We already discussed that the partition tables on the data disks are a mess, and there is no way to redo them without deleting the content. But, if you can manage to keep the content on three disks and have the fourth empty (it doesn't matter which one of the four), you can sort out its partition table first, then move to it the data from another disk, do that one, etc, etc...

That is what I would do.

One thing you can try is whether you can see all disks from live mode. Prepare cd or usb with ubuntu desktop image and boot it into live mode from it. Then check if you can read all disks, and that way you can move data around too and make this happen. But we are coming back to the question whether all disks are really, really full, or you can work with some free space to move the data around and recreate new blank partition tables.

I think where you went wrong is using the whole disk as a device. You NEVER use the disk for formatting, you create partition on it and format them with the filesystem you want to use. I think that's why it shows as loop table. If you keep it as it is, even if you can boot the system with all disks connected, it's a disaster waiting to happen sooner or later... But it's your computer and your data, it depends on you if you want to fix the tables or not...

1. Yes it's correct installed using LVM, i was told that was recommended.
2. I do only have data on the 2 big disk you see are not commented out, and 2 empty disks i want to install into the system now. 

-- Let's say i'm willing to start fresh, what should i do step by step to make this as easy as possible. -- 
I have totalt of 1 SSD (system) and 3/4 HDD between 2 and 3 TB. It's gonna be a file server(Plex). So like in windows 1 big partition is what i would like so it's easyer.
I'm not realy good in Ubuntu(linux) but I can say i'm desent. (Google my problems, and mostly find answers there). 

I'm this |#####-| close to just **** it, and install windows like my old server :P

---

### Post by darkod on 2016-07-27
The way it is now you will not have one big partition because all four data disks are separate mount points. I will post back tomorrow because it's too late now in my time zone.

Get ubuntu desktop iso and make cd/usb with it. Then boot in Try Ubuntu mode and check if you see all disks connected. We still need to find a way to boot the system with all disks connected so you can work on them.

If you manage to boot it like that, I will post what to do next. You will sort this out easy...

---

### Post by anders20 on 2016-07-29
> **darkod said:**
> The way it is now you will not have one big partition because all four data disks are separate mount points. I will post back tomorrow because it's too late now in my time zone.

Get ubuntu desktop iso and make cd/usb with it. Then boot in Try Ubuntu mode and check if you see all disks connected. We still need to find a way to boot the system with all disks connected so you can work on them.

If you manage to boot it like that, I will post what to do next. You will sort this out easy...

Hey, just want to say thanks for taking your time helping me. 

I booted up Ubuntu Desktop, and manage to make a partition on both disk with ext4. Check picture. (Used Gparted)
Picture 1: [https://scontent.fsvg1-1.fna.fbcdn.net/v/t35.0-12/13681867_10157265061110192_1677505931_o.jpg?oh=6b0053bf62514da326a5b032fe9f9047&oe=579D4F8F](https://scontent.fsvg1-1.fna.fbcdn.net/v/t35.0-12/13681867_10157265061110192_1677505931_o.jpg?oh=6b0053bf62514da326a5b032fe9f9047&oe=579D4F8F)
Picture 2: [https://scontent.fsvg1-1.fna.fbcdn.net/v/t35.0-12/13646672_10157265061065192_1626064046_o.jpg?oh=52547e44f2143ecf202279cc3e430ff5&oe=579E418C](https://scontent.fsvg1-1.fna.fbcdn.net/v/t35.0-12/13646672_10157265061065192_1626064046_o.jpg?oh=52547e44f2143ecf202279cc3e430ff5&oe=579E418C)

And that i thought everything would be fine, so rebooted, removed the USB with Ubuntu and tryed to boot Ubuntu Server 16.04. 
Then i get the Emergency mode again, took some pictures hope them help. Waiting for you before i do anything else :)
Picture 1: [https://scontent.fsvg1-1.fna.fbcdn.net/v/t35.0-12/13663517_10157265061080192_1499699881_o.jpg?oh=8c436120d7162b53b9519f17b43939c6&oe=579D7CC9](https://scontent.fsvg1-1.fna.fbcdn.net/v/t35.0-12/13663517_10157265061080192_1499699881_o.jpg?oh=8c436120d7162b53b9519f17b43939c6&oe=579D7CC9)
Picture 2: [https://scontent.fsvg1-1.fna.fbcdn.net/v/t34.0-12/13866679_10157265068725192_1505479881_n.jpg?oh=a3a1f25869c206e19897a198b9732fd8&oe=579E8D20](https://scontent.fsvg1-1.fna.fbcdn.net/v/t34.0-12/13866679_10157265068725192_1505479881_n.jpg?oh=a3a1f25869c206e19897a198b9732fd8&oe=579E8D20)

No idea if those picture where to any good :p - Just reply to what you want me to next :)

---

### Post by darkod on 2016-07-29
Well, I never actually told you to do that... :)

You did good booting the live mode but I said once you get there successfully we can continue with the rest...

Looking at these pics I think I know why it's not booting up... You can see it complains about /dev/sdc... In your fstab you are mounting /dev/sdc but in fact now sdc is a 3TB disk (one of the new ones I guess) and it has ext4 partition named sdc1. So you should be mounting that instead of sdc.

But in fact, go few steps back... You did good creating new gpt tables on the new 3TB disks but you shouldn't have created ext4 partitions. If you want to use one big continuous space for data you can use simple partitions on your four disks. You need to use LVM (which you are already using for root and swap LVs (logical volumes).

Here is the plan, but do NOT rush into it if you don't know to perform each step. Ask and I will guide you.

1. On the new 3TB disks (no data on them yet, right?) delete the ext4 and create new partitions marked as "physical volume for LVM" (NOT ext4 or any other filesystem). This is because with LVM the filesystem lies on the LVs, not on the partitions.
2. Create new VG for the data.
3. Add those PV (physical volumes) to the VG.
4. Create one new big LV (logical volume) into that VG. That would give you LV of 6TB approx.
5. Move the data from the old 2TB disks to that new LV. It should fit because the new disks are bigger.
6. Then delete all partitions on the 2TB disks too, create new gpt tables and one single big partition of type "physical device for LVM" too.
7. Add those PVs to the same VG you created earlier for the data. That will give you one VG of approx 10TB.
8. You don't have to expand the data LV right now, you can always expand later as needed, without shutting down or rebooting.

Does this fit your requirements?

PS. All of the above assumes you need the whole 10TB space and plan to use only LVM. But if a disk fails you lose the data. If you want to use raid and LVM, then you need slightly different setup. Of course, raid1 will mean you lose half of the space, but you have the data mirrored... The decision is yours...

---

### Post by darkod on 2016-07-29
Further food for thoughts...

In your fstab you are mounting the partitions like /dev/sdXY. But with adding or removing disks the "letters" assigned to disks change. Your sdc was one of the 2TB disks you had first, now by adding more disks that changed. Hence the emergency mode.

But if you decide to redo the whole storage setup as explained above (and highly recommendable IMHO), don't even bother about this right now. You will modify the fstab as needed after you recreate the storage.

To avoid these errors with /dev/sdXY when a disk changes its letter, few years ago ubuntu started to use UUIDs in the fstab. The UUID is assigned on formatting partitions and is unique. So if you use that in the fstab it will always mount the partitions correctly regardless of adding or removing disks.

But if you keep it as it is now (with ext4 partition on each disk) you will have four separate storages (mount points) and never one big space...

And think about the raid option seriously. Depending how important the data is to you, with raid1 you would have a total of 5TB "only" but the data will be mirrored... Losing a disk does not lose you the data...

---

### Post by anders20 on 2016-07-29
> **darkod said:**
> Well, I never actually told you to do that... :)

You did good booting the live mode but I said once you get there successfully we can continue with the rest...

Looking at these pics I think I know why it's not booting up... You can see it complains about /dev/sdc... In your fstab you are mounting /dev/sdc but in fact now sdc is a 3TB disk (one of the new ones I guess) and it has ext4 partition named sdc1. So you should be mounting that instead of sdc.

But in fact, go few steps back... You did good creating new gpt tables on the new 3TB disks but you shouldn't have created ext4 partitions. If you want to use one big continuous space for data you can use simple partitions on your four disks. You need to use LVM (which you are already using for root and swap LVs (logical volumes).

Here is the plan, but do NOT rush into it if you don't know to perform each step. Ask and I will guide you.

1. On the new 3TB disks (no data on them yet, right?) delete the ext4 and create new partitions marked as "physical volume for LVM" (NOT ext4 or any other filesystem). This is because with LVM the filesystem lies on the LVs, not on the partitions.
2. Create new VG for the data.
3. Add those PV (physical volumes) to the VG.
4. Create one new big LV (logical volume) into that VG. That would give you LV of 6TB approx.
5. Move the data from the old 2TB disks to that new LV. It should fit because the new disks are bigger.
6. Then delete all partitions on the 2TB disks too, create new gpt tables and one single big partition of type "physical device for LVM" too.
7. Add those PVs to the same VG you created earlier for the data. That will give you one VG of approx 10TB.
8. You don't have to expand the data LV right now, you can always expand later as needed, without shutting down or rebooting.

Does this fit your requirements?

PS. All of the above assumes you need the whole 10TB space and plan to use only LVM. But if a disk fails you lose the data. If you want to use raid and LVM, then you need slightly different setup. Of course, raid1 will mean you lose half of the space, but you have the data mirrored... The decision is yours...

Thanks for reply. 

- Can't I just have them as separate disks? and map them to a folder like i have done with the 2 other disks? I don't need 1 big "folder" of 10TB. 
I don't want to risk "all" my disks if they can be separate like they are now, if one goes only the data on that one goes. 

Yes the 2 disks i'm setting up now are empty, and partition to ext4 now since i just did that :P 
- Seems like when i connect the disk it renames\change the names of the old disks? - and that's why it wont start.

---

### Post by darkod on 2016-07-29
Yes, you can have them as separate and mounted to a folder...

If I understand your partitions correctly, you will need to mount the disks with gpt table as /dev/sdX1 (with a number 1), and the loop with /dev/sdX.

So, the old 2TB disks in fstab need to be:
/dev/sda
/dev/sdd
The new 3TB disks because they actually have a partition on them:
/dev/sdc1
/dev/sde1

Mount them to any folder created for that purpose (needs to be empty folder). Once everything is mounted and booted, copy the data to the 3TB disks and create new gpt tables with single ext4 partition on sda and sdd too, to get rid of the loop tables.

You can edit this fstab from live mode, just open the correct root LV from the LVM. You can see it from live mode, but it will not be /etc/fstab. The /etc/fstab is the one belonging to the live mode, you need to edit the one on /dev/Asgard-vg/root. If you need help with that, ask first. Be very careful when editing fstab. And make a copy of it first.

After you do all that and boot the OS correctly, we can talk about mounting by UUID if you want to. So you will not have issues with this any more...

PS. But I think you are missing good opportunity to configure your storage in a better way. Think about this: Now you have space to move the data and format the disks that need formatting. In the future with more data and less free space, you will not be able to do this as easily... But at the end of the day, the decision is yours...

PPS. I forgot to mention maybe a better option to sort out the fstab without going into live mode.
1. Disconnect the new 3TB disks.
2. Boot your server. In this case, only with the old disks, it boots, right?
3. Once you boot the OS modify the /etc/fstab and comment out all data mount lines (ALL of them).
4. Power off the server, connect the new disks, and boot it. It should boot the OS but without any data mounts.
5. Modify again /etc/fstab with the correct mount data for all four data disks/partitions.
6. Reboot and see if it boots like that... It should.

---

### Post by anders20 on 2016-07-29
> **darkod said:**
> Yes, you can have them as separate and mounted to a folder...

If I understand your partitions correctly, you will need to mount the disks with gpt table as /dev/sdX1 (with a number 1), and the loop with /dev/sdX.

So, the old 2TB disks in fstab need to be:
/dev/sda
/dev/sdd
The new 3TB disks because they actually have a partition on them:
/dev/sdc1
/dev/sde1

Mount them to any folder created for that purpose (needs to be empty folder). Once everything is mounted and booted, copy the data to the 3TB disks and create new gpt tables with single ext4 partition on sda and sdd too, to get rid of the loop tables.

You can edit this fstab from live mode, just open the correct root LV from the LVM. You can see it from live mode, but it will not be /etc/fstab. The /etc/fstab is the one belonging to the live mode, you need to edit the one on /dev/Asgard-vg/root. If you need help with that, ask first. Be very careful when editing fstab. And make a copy of it first.

After you do all that and boot the OS correctly, we can talk about mounting by UUID if you want to. So you will not have issues with this any more...

PS. But I think you are missing good opportunity to configure your storage in a better way. Think about this: Now you have space to move the data and format the disks that need formatting. In the future with more data and less free space, you will not be able to do this as easily... But at the end of the day, the decision is yours...

PPS. I forgot to mention maybe a better option to sort out the fstab without going into live mode.
1. Disconnect the new 3TB disks.
2. Boot your server. In this case, only with the old disks, it boots, right?
3. Once you boot the OS modify the /etc/fstab and comment out all data mount lines (ALL of them).
4. Power off the server, connect the new disks, and boot it. It should boot the OS but without any data mounts.
5. Modify again /etc/fstab with the correct mount data for all four data disks/partitions.
6. Reboot and see if it boots like that... It should.

I see the upside with having just one big storage(one folder?) of 10TB and possible to extend it easy, but if i understood you correct, if one disk crash all of my data is gone? 
and i need to start over again, or? - I got 1000/1000 internett connection so getting my stuff back should not take long if it should happen.

If i comment out everything beside the boot disk in fstab, and connected all the disks, will they come up with correct names like you mention above, or might it be different? 
- This is so easy in windows, don't understand why linux has done it so hard :p 

And when i add them to fstab and reboot, it should work? fstab is load and mount right? 
So my fstab should look like this when i'm done: [http://pastebin.com/x0M4ptgA](http://pastebin.com/x0M4ptgA)

If this works, i'll buy you are beer :D
-spot

---

### Post by darkod on 2016-07-29
Yes, that fstab looks correct and it should work with all disks attached.

And yes, all commented disks will still be detected but not auto-mounted. The fstab is only to auto-mount on boot, all HW is detected anyway.

I would disagree this is so hard compared to windows (and I use windows a lot too). It's only that we have been discussing many options for long time, otherwise actually performing this takes about 5mins. :)

---

### Post by anders20 on 2016-07-29
> **darkod said:**
> Yes, that fstab looks correct and it should work with all disks attached.

And yes, all commented disks will still be detected but not auto-mounted. The fstab is only to auto-mount on boot, all HW is detected anyway.

I would disagree this is so hard compared to windows (and I use windows a lot too). It's only that we have been discussing many options for long time, otherwise actually performing this takes about 5mins. :)

WoW! It actually worked.. I either i have not understood the rest of the people that have been trying to help me, or they have misunderstood my question.. :D Thanks ALOT!

Should i do something about the old disks? If yes, explain why and how as easy as you have done so far :)
```
--------------------------------------------------------
Model: ATA ST3000DM001-1ER1 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  3001GB  3001GB  ext3
--------------------------------------------------------
Model: ATA ST2000DM001-9YN1 (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext3
-------------------------------------------------------
My SSD DISK(OS) shows this:
Model: ATA KINGSTON SHFS37A (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  512MB  511MB  primary   ext2         boot
 2      513MB   120GB  120GB  extended
 5      513MB   120GB  120GB  logical                lvm
```

You got a paypal or something? - Send me a private message and i'll donate so you'll get a beer :D
-spot

---

### Post by darkod on 2016-07-30
Well, I would get rid of those loop tables on sda and sdd. Plus this way the filesystem starts from the very beginning (you see it says 0B) and to be aligned for optimum performance it usually starts at 1MB.

Here is what you should do:
1. Mount the new disks in fstab (I think you already did this). This way they will mount at the mount points you selected for them.
2. Copy all data there to empty the 2TB disks (sda and sdd).
3. Create new big partition on sda and sdd using parted in the command line (the server has no GUI right):

```
sudo parted /dev/sda   (opens up the parted prompt for sda)
unit Mib   (changes display unit to MiB for easier working)
print   (prints current info, at the top notice the disk size in MiB, it can be like 1907729MiB)
mklabel gpt   (create new blank gpt table)
mkpart DATA 1 xxxxxx   (create new partition with label DATA starting from 1MiB and ending at xxxxxxMiB, use a number few MiB less than the total disk size)
print    (verify the new table looks as expected)
quit   (if everything is OK quit parted prompt)
```

4. After that is done for both disks create ext4 filesystem on the partitions like:
```
sudo mkfs.ext4 /dev/sda1
```

5. That's it. Now you need to modify fstab to use /dev/sda1 and /dev/sdd1 instead of /dev/sda and /dev/sdd. Don't forget to also modify ext3 to ext4 in the fstab if you format the new partitions as ext4.

NOTE on UUID: If you want to use UUID instead of /dev/sdXY in fstab and not worry about disk names in the future, you can check all partition UUIDs with:
```
sudo blkid
```

Copy the large random string and you can use it in fstab (without the quotes). For example instead of /dev/sde1 use:
```
UUID=<string>
```

The rest of the line in fstab remains identical, just the partition is replaced with the UUID.

PS. In the mkpart command above I think the syntax was 'mkpart label start end' and not 'mkpart start end label'. If it gives you an error try putting the label at the end but I think it was at the start. I haven't used it for a while... :)

That's all...

---

### Post by anders20 on 2016-07-30
> **darkod said:**
> Well, I would get rid of those loop tables on sda and sdd. Plus this way the filesystem starts from the very beginning (you see it says 0B) and to be aligned for optimum performance it usually starts at 1MB.

Here is what you should do:
1. Mount the new disks in fstab (I think you already did this). This way they will mount at the mount points you selected for them.
2. Copy all data there to empty the 2TB disks (sda and sdd).
3. Create new big partition on sda and sdd using parted in the command line (the server has no GUI right):

```
sudo parted /dev/sda   (opens up the parted prompt for sda)
unit Mib   (changes display unit to MiB for easier working)
print   (prints current info, at the top notice the disk size in MiB, it can be like 1907729MiB)
mklabel gpt   (create new blank gpt table)
mkpart DATA 1 xxxxxx   (create new partition with label DATA starting from 1MiB and ending at xxxxxxMiB, use a number few MiB less than the total disk size)
print    (verify the new table looks as expected)
quit   (if everything is OK quit parted prompt)
```

4. After that is done for both disks create ext4 filesystem on the partitions like:
```
sudo mkfs.ext4 /dev/sda1
```

5. That's it. Now you need to modify fstab to use /dev/sda1 and /dev/sdd1 instead of /dev/sda and /dev/sdd. Don't forget to also modify ext3 to ext4 in the fstab if you format the new partitions as ext4.

NOTE on UUID: If you want to use UUID instead of /dev/sdXY in fstab and not worry about disk names in the future, you can check all partition UUIDs with:
```
sudo blkid
```

Copy the large random string and you can use it in fstab (without the quotes). For example instead of /dev/sde1 use:
```
UUID=<string>
```

The rest of the line in fstab remains identical, just the partition is replaced with the UUID.

PS. In the mkpart command above I think the syntax was 'mkpart label start end' and not 'mkpart start end label'. If it gives you an error try putting the label at the end but I think it was at the start. I haven't used it for a while... :)

That's all...

Will this be easier if i do it from the live CD?, like i did on the 2 new disks? - It's the command line that screwed me the first time :p - Yes my server has no GUI. 
Basicly you want me to copy over the files on the existing drives, and partition them with GPT and ext4 like i did on the new drives, right?
I don't touch the SSD(OS) right?

---

### Post by darkod on 2016-07-30
Correct, copy all data to the new disks so you can reformat the old disks. And don't touch the SSD, yes.

Whether it's easier to work with live CD is up to you. You shouldn't be afraid of parted and you should learn it if running linux servers. But again, how you create the new partitions is up to you...

---

### Post by anders20 on 2016-07-30
> **darkod said:**
> Correct, copy all data to the new disks so you can reformat the old disks. And don't touch the SSD, yes.

Whether it's easier to work with live CD is up to you. You shouldn't be afraid of parted and you should learn it if running linux servers. But again, how you create the new partitions is up to you...


Okay I think I did it. 
Here is my Parted -l: [http://pastebin.com/Ksn5gvxG](http://pastebin.com/Ksn5gvxG)
Why is my SDD disk Partition Table: msdos? Should i be worried?

-spot

---

### Post by oldfred on 2016-07-30
If you install in BIOS boot mode, Ubuntu uses MBR partitioning for smaller drives.
If you install in UEFI boot mode Ubuntu uses gpt partitioning.

And if drive is blank and somewhere over 1.5TB it will use gpt, even though gpt is only required for drives over 2TiB.

If you want gpt on smaller drives in BIOS mode, you have to add a tiny 1 or 2MB unformatted partition with the bios_grub flag if using gparted, or code ef02 if using gdisk.

In parted you can use the mklabel command to set drive partitioning to gpt.
see
man parted

---

### Post by darkod on 2016-07-31
What oldfred is saying in short is: No, you don't need to be worried. msdos table on smaller disks is perfectly normal and works just fine.

That's it then, you dii all that you wanted, right?

---

### Post by anders20 on 2016-07-31
> **darkod said:**
> What oldfred is saying in short is: No, you don't need to be worried. msdos table on smaller disks is perfectly normal and works just fine.

That's it then, you dii all that you wanted, right?

Yes, thanks alot for your help! :D - sendt you a beer :D

---


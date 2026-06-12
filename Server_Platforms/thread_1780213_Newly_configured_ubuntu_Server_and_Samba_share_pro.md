---
title: "Newly configured ubuntu Server and Samba share problems"
date: 2011-06-11
forum: Server Platforms
---

### Post by newbuntu007 on 2011-06-11
Hi Gang, I'm new to Linux[2 weeks] and decided to build a RAID5 array with Ubuntu server edition 10.4 LTS. I had a nice Computer I had build for other purposes and decided to turn it into a Ubuntu Server.

***SERVER is for Filesharing only/Backup, maybe other stuff in future but not now.**

Specs:
-BOARD: Gigabyte GA-790XTA-UD4 
-CPU: Athlon II X4 630 2.8GHz Quad-core
-RAM: 4GB CORSAIR XMS3 (2x2GB) 240-Pin DDR3 SDRAM DDR3 1600 Dual channel
-GPU: Geforce FX7100GS 128MB DDR/DVI/TV
-STORAGE: 1x[320GB] Hitachi HDT72503 & 5x[2TB] Samsung F4 Spinpoints HD204UI
-PSU: COOLER MASTER Silent Pro 700 
-CASE: Antec Twelve Hundred Black Steel ATX Full Tower 
-OS: Ubuntu Server 10.04.2 LTS

****Partition/Drive info****

/dev/sda Boot---------->  298.09 GB Hitachi HDT72503   
20GB /
16GB /swap
50GB /var
20GB /tmp
20GB /home
4GB  /usr

/dev/sdb Raid Array 1  1.82 TB SAMSUNG HD204UI   
/dev/sdc Raid Array 2 1.82 TB SAMSUNG HD204UI   
/dev/sdd Raid Array 3 1.82 TB SAMSUNG HD204UI   
/dev/sde Raid Array 4 1.82 TB SAMSUNG HD204UI   
/dev/sdf  Raid Array  5 1.82 TB SAMSUNG HD204UI

[B]
****My PROCEDURE FOR RAID5*****[/B]

a. I configured all x5 Samsung drives RAID5 using "mdadm" command. Created partitions on all 5 sdb---->sdf [used the whole drive]
#fdisk /dev/sdb--->sdf

b. Set drives id to Raid "fd"[All 5 drives]

c. Created Array
#mdadm --create --verbose /dev/md0 -&#8211;level=5 &#8211;-raid-
devices=5 /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf

d. Formatted the RAID Drive 
#mkfs -t ext4 /dev/md0

e.Created the "mdadm.conf file" (changed 00.90-->0.90)
#mdadm --detail --scan >> /etc/mdadm/mdadm.conf

f. Created mount point for RAID5 [FONT=monospace]
[/FONT]# mkdir /mnt/raid
 
g. Edited the "fstab" file to auto mount at start.
#/dev/md0      /mnt/raid     ext4    defaults    1 2

-Finish
*********************************************************
[B]
*****Questions to START***********[/B]

1. It was my fisrt time doing linux and read mad forums and how to do this and that, when it comes to partitions.  Did I partition that 300GB drive correctly? 

2. I've tried to setup Samba files haring but I'm confused when it comes to creating a DIR on my RAID5 partition and accessing it through Windows 7/XP?

3. I have no files setup yet on the RAID5 partition and need to start putting things on there via Windows Share/FTP/OpenSSH. [Whichever]

4. I come from windows, where I create a folder(I can see) and Drag and Drop. I would like to create folders [MUSIC], [MOVIES], [DATA], [TOONS], [MAME] on the RAID5 partition and drag files from my Windows devices to them folders.

5. I literally almost gave up 2 nights ago[I've learned plenty]

I appreciate the help.

---

### Post by kevinthecomputerguy on 2011-06-11
Webmin can make all these tasks easier.
Page 3 talks about samba [http://woodel.com](http://woodel.com)
Dont give up

---

### Post by newbuntu007 on 2011-06-11
> **kevinthecomputerguy said:**
> Webmin can make all these tasks easier.
Page 3 talks about samba [http://woodel.com](http://woodel.com)
Dont give up

Thanks bud, that was easy as pie. Up till now I've been doing everything command style.

I created one share called [music] and testing 200GB upload via windows.

Finally a functional File Server.

---

### Post by kevinthecomputerguy on 2011-06-11
Rock on !

---


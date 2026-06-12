---
title: "new to linux, setting up ubuntu server 12.04 NAS"
date: 2013-05-19
forum: Server Platforms
---

### Post by undadawg on 2013-05-19
[COLOR=#333333][FONT=Ubuntu Beta]I just built my NAS hardware, these are the specs
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]CPU: Intel Core i5-3570 3.4GHz Quad-Core Processor[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Motherboard: Asus P8H77-M PRO Micro ATX LGA1155 Motherboard[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Memory: Kingston 16GB (2 x 8GB) DDR3-1600 Memory[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Storage: Western Digital Red 3TB 3.5" 5400RPM Internal Hard Drive **X 6**[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Storage: Seagate Barracuda 1TB 3.5" 7200RPM Internal Hard Drive[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Case: Fractal Design Arc Mini MicroATX Mini Tower Case[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Power Supply: SeaSonic G 550W 80 PLUS Gold Certified ATX12V / EPS12V Power Supply
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Disclaimer: I have no linux knowledge, this is my first linux build and its meant to be a learning experience..
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I have installed Ubuntu Server 12.04 64BIT on the 1TB HDD. I wasn't sure during installation what is the best partitioning scheme so I did the following (based on a tutorial i followed)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta][http://i.imgur.com/SS6PmO7.jpg](http://i.imgur.com/SS6PmO7.jpg)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]150GB for the OS[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]15GB for Boot[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]35.2GB for SWAP[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]800GB for /home
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]If this is ok, then now how do I partition my 6 x 3TB HDDs to set up my SAMBA(maybe other protocool?) shares? I've read conflicting discussions online on the use of RAID(5) vs ZFS etc etc so I am really confused on what to do now. 
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Which sharing protocol (samba? NFS?), RAID/file format, and parition scheme should i use for a home nas which will store/stream media via plex and store documents/pictures aswell?

I will log everything I do so that I can track where I made any mistakes or if anyone else wants to follow a similar path
_**LOG**_

- Hardware build complete
- Installed Ubuntu Server 12.04 64bit to 1TB HDD
- Configured static ip by editing /etc/network/interfaces
- Installed OpenSSH, can be accessed remotely now
- Installed Webmin
[/FONT][/COLOR]--------[http://ubuntuserverguide.com/2012/06/how-to-install-webmin-on-ubuntu-server-12-04-lts.html](http://ubuntuserverguide.com/2012/06/how-to-install-webmin-on-ubuntu-server-12-04-lts.html) (followed the installation via APT tutorial)[COLOR=#333333][FONT=Ubuntu Beta]
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]-------------- Ran into some problems during installation, when i used the 'cat .......... EOF' command to add the webmin source to the file i followed the instructions but it didnt terminate. so i press ctrl + C to end it. I tried to install webmin but it couldn't be found. I then added the two sources manually via nano to the sources.list file 
--------------and then it could install properly
- Installed lm-sensors to monitor hardware temps
- Installed plex media server and avahi
---------------[/FONT][/COLOR][http://forums.plexapp.com/index.php/topic/26727-how-to-plex-media-server-on-ubuntu/](http://forums.plexapp.com/index.php/topic/26727-how-to-plex-media-server-on-ubuntu/) (followed this)
- Installed hddtemp
- Installed deluge daemon + webui, via [http://www.linuxplained.com/install-deluge-web-interface-on-ubuntu-1204/](http://www.linuxplained.com/install-deluge-web-interface-on-ubuntu-1204/)

REINSTALL
- installed ubuntu again
-partition 100gb for /  , 32gb for SWAP, rest to /home
-created RAID5 array during installation
-installed openSSH and SAMBA during installation
-set static IP
-created filesystem mkfs -t ext4 /dev/md0
-install msmtp to set up email monitoring
-set up directories for cron scripts
-installed monitoring tools , smartmontools etc

---

### Post by 2F4U on 2013-05-19
> [COLOR=#333333][FONT=Ubuntu Beta]150GB for the OS[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]15GB for Boot[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]35.2GB for SWAP[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]800GB for /home
[/FONT][/COLOR]

150 GB for the OS is huge and you will never need that much space. Depending on what you are going to install on that machine, 20 - 40 GB is more than sufficient. Also you don't need a dedicated /boot partition.

[https://help.ubuntu.com/lts/installation-guide/amd64/partitioning.html](https://help.ubuntu.com/lts/installation-guide/amd64/partitioning.html)

---

### Post by undadawg on 2013-05-19
> **2F4U said:**
> 150 GB for the OS is huge and you will never need that much space. Depending on what you are going to install on that machine, 20 - 40 GB is more than sufficient. Also you don't need a dedicated /boot partition.

[https://help.ubuntu.com/lts/installation-guide/amd64/partitioning.html](https://help.ubuntu.com/lts/installation-guide/amd64/partitioning.html)

I see...well i'm guessing its too late to change this now haha. 

Ok so now my plan is to do a complete re-install BUT only once I get everything running the way to want to. Then i will reinstall and do everything again correctly. Since I don't want my 'OS/system' HDD to be part of my 6x3TB group of data drives, I used a spare 1TB drive. Since the drive is so big, what would be the best way to partition it and use all of that space. So far i'm thinking
 
50GB OS (just because I have so much space available)
~32GB for SWAP

the remaining ~900GB as? /home/?

---

### Post by ally_uk on 2013-05-19
100MB - Boot
100 GIG = /
Rest of disk = home
Swap Space

I would setup up LVM on the above if you run out of space on the partitions you can exand the volume across a secondary disk, Regarding your other disks the 3Terrabyte drives are you going to be setting up any form of redundancy? Hardware of Software raid? personally I would go down the Hardware Raid route. 

I would Setup a Raid5 Array on the terabyte disk also use LVM and mount it as /Data

That's how I would go about it there might be a better way of doing things

---

### Post by undadawg on 2013-05-19
> **ally_uk said:**
> 100MB - Boot
100 GIG = /
Rest of disk = home
Swap Space

I would setup up LVM on the above if you run out of space on the partitions you can exand the volume across a secondary disk, Regarding your other disks the 3Terrabyte drives are you going to be setting up any form of redundancy? Hardware of Software raid? personally I would go down the Hardware Raid route. 

I would Setup a Raid5 Array on the terabyte disk also use LVM and mount it as /Data

That's how I would go about it there might be a better way of doing things

thanks for your reply.

I read that it doesn't make sense to use LVM if you have a dedicated drive for the root or OS. Since its a 1TB drive I doubt I will run out of space and need to expand to another disk. 

For my 3TBs i was planning to go with software RAID5 but i have been hearing that its better to go the ZFS route instead of RAID5..

---

### Post by grunge09 on 2013-05-19
mdadm is more flexible than zfs, but it is not meant for a business environment.  Mdadm can GROW an array by adding a disk, can't do that with zfs.  

I recommend Raid6.  If 2 drives fail you can still rebuild the array and continue.  If 2 drives fail on RAID5 you are in trouble.  Even if you have RAID5, you can upgrade to RAID6.  

Others may tell you that do not let this be the only backup system, have a backup for your backup.  mdadm RAID is not mean to be a backup.

My personal experience...

I have a 5u rackmount 4TB box using FREENAS on UFS file system, using hardware raid 5 with hot spares on 2 arrays.  

I also have a 2nd system that is: 

Full Tower case, ubuntu server 12.10 samba shares, mdadm raid5.  

I have 4 x 2TB green drives in RAID5, and have grown the array once already (by mistake).  That took 20 hours to grow the array.  using onboard sata ports.   I use a 8gb usb stick to boot the 12.10 Ubuntu Server OS.   I have a new spare 2tb drive in the box.  Looking to get another and upgrade to RAID6 myself.  

I use RSYNC to backup to both systems, so I have 2 copies of data.  

Good luck.

---

### Post by undadawg on 2013-05-20
> **grunge09 said:**
> mdadm is more flexible than zfs, but it is not meant for a business environment.  Mdadm can GROW an array by adding a disk, can't do that with zfs.  

I recommend Raid6.  If 2 drives fail you can still rebuild the array and continue.  If 2 drives fail on RAID5 you are in trouble.  Even if you have RAID5, you can upgrade to RAID6.  

Others may tell you that do not let this be the only backup system, have a backup for your backup.  mdadm RAID is not mean to be a backup.

My personal experience...

I have a 5u rackmount 4TB box using FREENAS on UFS file system, using hardware raid 5 with hot spares on 2 arrays.  

I also have a 2nd system that is: 

Full Tower case, ubuntu server 12.10 samba shares, mdadm raid5.  

I have 4 x 2TB green drives in RAID5, and have grown the array once already (by mistake).  That took 20 hours to grow the array.  using onboard sata ports.   I use a 8gb usb stick to boot the 12.10 Ubuntu Server OS.   I have a new spare 2tb drive in the box.  Looking to get another and upgrade to RAID6 myself.  

I use RSYNC to backup to both systems, so I have 2 copies of data.  

Good luck.

Interesting set-up.

I think i will go with mdadm RAID 5 with one disk failure redundancy. 

I'm getting a bit confused on the nomenclatures regarding fileformats/protocools.

NFS/SAMBA are protocools
ext4, NTFS, UFS, ZFS are filesystems/fileformat
Then RAID is for different levels of redundancy.

So i need to choose a protocool for serving the shares, a filesystem to format the HDDs and then software RAID5 for redundancy.

If i have a multi platform environment (windows, osx, linux, various mobile/embedded devices, apple TV/roku etc) is NFS better than SAMBA? 

Also will ext4 do for the filesystem? If so then I guess i will go with my 6x3TB drives in RAID5 (via mdadm), formated as ext4, and the server will run NFS to share the files.

---

### Post by LHammonds on 2013-05-20
> **undadawg said:**
> 
[COLOR=#333333][FONT=Ubuntu Beta]CPU: Intel Core i5-3570 3.4GHz Quad-Core Processor[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Motherboard: Asus P8H77-M PRO Micro ATX LGA1155 Motherboard[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Memory: Kingston 16GB (2 x 8GB) DDR3-1600 Memory[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Storage: Western Digital Red 3TB 3.5" 5400RPM Internal Hard Drive **X 6**[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Storage: Seagate Barracuda 1TB 3.5" 7200RPM Internal Hard Drive[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Case: Fractal Design Arc Mini MicroATX Mini Tower Case[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Power Supply: SeaSonic G 550W 80 PLUS Gold Certified ATX12V / EPS12V Power Supply
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I have installed Ubuntu Server 12.04 64BIT on the 1TB HDD. I wasn't sure during installation what is the best partitioning scheme so I did the following (based on a tutorial i followed)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta][http://i.imgur.com/SS6PmO7.jpg](http://i.imgur.com/SS6PmO7.jpg)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]150GB for the OS[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]15GB for Boot[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]35.2GB for SWAP[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]800GB for /home
[/FONT][/COLOR]

You don't need any more than 12 GB for the base OS.  However, you need to design it so it can grow where you need it to grow and prevent growth in places it shouldn't.  For example, you never want your root partition to ever get filled up.  The best way to avoid it is to separate all growth areas into their own partitions so that the root partition itself never actually grows over time.  Need your home folder to grow?  Make sure it can and make sure you know how to do it.

15GB for the boot partition is extreme and unnecessary.  You could get away with a 200 MB partition (which will be 30% usage initially) or 300 MB partition (which will be 20% usage initially) and simply purge old kernels that build up there over time.

35 GB swap is also overkill.  With 16GB RAM, you probably won't even need a swap partition.  I would recommend a small 4GB swap partition and then just monitor it to see if your system ever even touches it. (I doubt it will).  Most of my servers run with just 4 GB of RAM...some with just 512 MB like my MySQL server.

The Ubuntu Server link in my sig covers how I setup a server and its partition layout with LVM (step-by-step) in such a way that it can grow as needed over time.  The extra unused space in the LVM allows you to expand the file system as necessary (even automatically via script) as well as give you room to create online snapshots of your system to perform backups without the need to stop your services or reboot the server to get a full backup (also documented in the link).

As for how you setup your physical drives, there are many different ways and that's up to you.  But make sure you know the advantage and disadvantage of each configuration.  Which ever one you choose to go with, make sure you learn and document how to handle a drive failure and replacement.  I really mean for you to "document" it and "test" it out.  Pull out a drive to simulate it going offline.  Then put in a new drive (different size) to test how it affects your system, data and how long it takes to rebuild, etc.  Doing this now while there is no important data on the system will save you all kinds of woe later one when (not if) a drive fails.  It is nice knowing you have verified backups and a written procedure on how to replace a failed drive and how to restore if the hardware procedure fails you.

LHammonds

---

### Post by undadawg on 2013-05-20
> **LHammonds said:**
> You don't need any more than 12 GB for the base OS.  However, you need to design it so it can grow where you need it to grow and prevent growth in places it shouldn't.  For example, you never want your root partition to ever get filled up.  The best way to avoid it is to separate all growth areas into their own partitions so that the root partition itself never actually grows over time.  Need your home folder to grow?  Make sure it can and make sure you know how to do it.

15GB for the boot partition is extreme and unnecessary.  You could get away with a 200 MB partition (which will be 30% usage initially) or 300 MB partition (which will be 20% usage initially) and simply purge old kernels that build up there over time.

35 GB swap is also overkill.  With 16GB RAM, you probably won't even need a swap partition.  I would recommend a small 4GB swap partition and then just monitor it to see if your system ever even touches it. (I doubt it will).  Most of my servers run with just 4 GB of RAM...some with just 512 MB like my MySQL server.

The Ubuntu Server link in my sig covers how I setup a server and its partition layout with LVM (step-by-step) in such a way that it can grow as needed over time.  The extra unused space in the LVM allows you to expand the file system as necessary (even automatically via script) as well as give you room to create online snapshots of your system to perform backups without the need to stop your services or reboot the server to get a full backup (also documented in the link).

As for how you setup your physical drives, there are many different ways and that's up to you.  But make sure you know the advantage and disadvantage of each configuration.  Which ever one you choose to go with, make sure you learn and document how to handle a drive failure and replacement.  I really mean for you to "document" it and "test" it out.  Pull out a drive to simulate it going offline.  Then put in a new drive (different size) to test how it affects your system, data and how long it takes to rebuild, etc.  Doing this now while there is no important data on the system will save you all kinds of woe later one when (not if) a drive fails.  It is nice knowing you have verified backups and a written procedure on how to replace a failed drive and how to restore if the hardware procedure fails you.

LHammonds

Thanks for your indepth reply. After looking at your tutorial post i'm starting to get the feeling that im in over my head in this nas project. Getting the temptation to fall back to something simple like freeNAS. I think I need to stick to something simple and just go with a static installation of ubuntu since i have such a massive drive just dedicated for the OS (1TB) if i even want this nas to be operational.

---

### Post by undadawg on 2013-05-20
As someone mentioned earlier, is it still necessary to have a separate /boot partition? or can I just get away with having 3 paritions ( /  , swap ,  /home).

My plan now is to do the following.

1.Re-install ubuntu server
-partition the 1TB drive as follow - 100gb for /  ----  16gb for SWAP ---- rest in /home
-create a software RAID5 array during installation using the 6x3TB drives with zero hot spares

2. set up static IP/ connect via SSH
3. format the raid volume (md0) as ext4
4. create the directories in md0 which are going to be shared later via SAMBA
5. create the SAMBA shares / configure SAMBA users etc
6. Install Plex media server + deluge-daemon/webui
 

Does this sound like it will work? I'm still a bit unsure about how the linux filesystem works etc but i think I should be able to figure it out along the way.

---

### Post by grunge09 on 2013-05-20
Try this link see if it helps

[http://www.havetheknowhow.com/default.htm](http://www.havetheknowhow.com/default.htm)

---

### Post by undadawg on 2013-05-21
> **grunge09 said:**
> Try this link see if it helps

[http://www.havetheknowhow.com/default.htm](http://www.havetheknowhow.com/default.htm)

great link thanks!

---

### Post by daniel41 on 2013-09-01
How is your system working out for you?  What set up are you using now?

---


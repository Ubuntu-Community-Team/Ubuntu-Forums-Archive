---
title: "secondary drive on ubuntu server"
date: 2016-03-28
forum: Server Platforms
---

### Post by ryan209 on 2016-03-28
i have just set up my server following [https://www.youtube.com/watch?v=SKJ55ebMcOc](https://www.youtube.com/watch?v=SKJ55ebMcOc)

I used an 80gb drive for the server, after finishing i thought hey why not make this my storage server too so i transferred all the data off my 3tb drive which wasnt much formated it with windows and stuck it in the server.

the drive registers as sdb and has 2 partitions when using fdisk

sdb1 and sdb2

I'm new to linux and I dont know how to format the drive so its all 1 partition and I dont know how to even access the partition.

using putty i tried cd /dev/sdb   sdb1   &  sdb2

and it says theyre not directories

so can someone help me get my drive formatted and then access it

I imagine i have to unmount it and then make it mount on startup, i need basics lol

---

### Post by papibe on 2016-03-28
Hi ryan209.

Here's a good tutorial on how to use fdisk, and mkfs to add a new hard drive to a server: [Installing A New HardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive"). I'd recommend using ext4 instead of ext3 as shown in the examples.

Let us know if that helps, and if you need more directions with that.
Regards.

---

### Post by ryan209 on 2016-03-28
that tutorial will be good for the next step but before doing that i need to format the drive, can this be done through ubuntu server.

i tried running
mkfs-ntfs -f /dev/sdb

but it said it doesnt exist or something

edit ****
ran [COLOR=#333333][FONT=UbuntuMono]mkfs -t ext4 /dev/sdb
seemed to work =)

edit 2***
now this doesnt show my drive -_-
[/FONT][/COLOR]lshw -C disk

> root@dirtrif:~# fdisk /dev/sdb

Welcome to fdisk (util-linux 2.26.2).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


/dev/sdb: device contains a valid 'ext4' signature; it is strongly recommended to wipe the device with wipefs(8) if this is unexpected, in order to avoid possible collisions


Device does not contain a recognized partition table.
The size of this disk is 2.7 TiB (3000592982016 bytes). DOS partition table format can not be used on drives for volumes larger than 2199023255040 bytes for 512-byte sectors. Use GUID partition table format (GPT).


Created a new DOS disklabel with disk identifier 0x483dffd5.


---

### Post by darkod on 2016-03-28
/dev/sdb or /dev/sdb1, /dev/sdb2, etc?

Similar like in windows, you do NOT format a whole disk, only partitions on it. /dev/sdb is the whole disk, while /dev/sdbX is partition #X on that disk.

Depending how many partitions you want on it, and how many you have, you need to format it to linux filesystem with:
```
sudo mkfs.ext4 /dev/sdb1
sudo mkfs.ext4 /dev/sdb2
etc
```

If you somehow formatted whole /dev/sdb I guess it's better to create new empty partition table, create the partitions you want and format them to ext4.

---

### Post by ryan209 on 2016-03-28
update got a little further
```
root@dirtrif:~# lshw -C disk  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       configuration: logicalsectorsize=512 sectorsize=512
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdd
       configuration: logicalsectorsize=512 sectorsize=512
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sde
       configuration: logicalsectorsize=512 sectorsize=512
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sdf
       configuration: logicalsectorsize=512 sectorsize=512
  *-disk
       description: ATA Disk
       product: ST980811AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: C
       serial: 5LY5ERDW
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=f776d7f9
  *-disk
       description: ATA Disk
       product: WDC WD30EZRX-00D
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 0A80
       serial: WD-WMC1T2761543
       size: 2794GiB (3TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=577e93a8
root@dirtrif:~# sudo fdisk /dev/sdb


Welcome to fdisk (util-linux 2.26.2).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


[B]The size of this disk is 2.7 TiB (3000592982016 bytes). DOS partition table format can not be used on drives for volumes larger than 2199023255040 bytes for 512-byte sectors. Use GUID partition table format (GPT).
[/B]

Command (m for help):

```

i have no idea where to go from here



***Edit****
ill get it, booting into ubunutu desktop to re format

ok got it all sorted with guid and the partition set, i just thought this was weird
says i used 44gbs on a fresh partition...
[ATTACH=CONFIG]268044[/ATTACH]

time to boot back into the server and finsih getting this set up

---

### Post by ryan209 on 2016-03-28
got everything working and can now access my drive through /storage which mounts on startup =)

thanks for the help!

---


---
title: "Adding hard drives"
date: 2013-08-31
forum: Server Platforms
---

### Post by Reddoug on 2013-08-31
Hi 

I am trying to teach myself how to work with Ubuntu Server 12.04 LTS. I have three hd's installed, 160 gb, 320gb and 1tb. I have the OS installed on the 160gb drive. I am trying to figure out how to be able to setup the other drive for storage for both Linux and Window backup.  I did figure out how to partition the 320 & 1 TB drive with gparted. Have not been able to figure out how to make them usable. This is a learning experence for personal use. Any help will be greatly appricated. Just haven't figured out what I am missing.

Thanks, Doug

```
doug@ubuntuCFS11:~$ sudo lshw -C disk 
  *-disk                  
       description: ATA Disk
       product: ST31000333AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: SD35
       serial: 5TE02PNL
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=411b80f6
  *-disk
       description: ATA Disk
       product: SAMSUNG HD160JJ
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: WU10
       serial: S08HJ10L438901
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000b5b68
  *-disk
       description: ATA Disk
       product: Hitachi HDP72503
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdc
       version: GM3O
       serial: GEA350RC15P84P
       size: 298GiB (320GB)
       configuration: ansiversion=5 signature=000933ae
  *-cdrom:0
       description: DVD-RAM writer
       product: DVD-RAM LF-D310
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/sr0
       version: A126
       capabilities: removable audio dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: DVD RW AD-7190A
       vendor: Optiarc
       physical id: 0.1.0
       bus info: scsi@6:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr1
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
doug@ubuntuCFS11:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x411b80f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1953521663   976759808   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5b68

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   304209919   152103936   83  Linux
/dev/sdb2       304211966   312580095     4184065    5  Extended
/dev/sdb5       304211968   312580095     4184064   82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000933ae

   Device Boot      Start         End      Blocks   Id  System
doug@ubuntuCFS11:~$
```

---

### Post by oldfred on 2013-08-31
Added code tags, Use them for longer terminal output.

Since internal drives you will want to add to fstab entries to permanently mount on boot the other partitions.
For Linux partitions you have to also set ownership and permissions, but Windows NTFS does no support ownership and permissions, so you just set defaults with fstab.

Specific commands and example of fstab entry for both NTFS and Linux.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

Lots of info but not always instructions on how to do it.

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[URL="https://wiki.archlinux.org/index.php/Fstab"]https://wiki.archlinux.org/index.php/Fstab

[/URL] Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

More info and example of setting permissions.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)

[URL="https://wiki.archlinux.org/index.php/Fstab"]
[/URL]

---

### Post by TheFu on 2013-08-31
An overview of the non-OS disk adding steps:
* connect the HDD to the computer
* determine the device name the computer gives to each HDD - something like /dev/sdX
* partition the HDD using either gparted or parted. This will create sub-devices /dev/sdX1 ... n
* create a file system (mkfs is the command) on each new partition using the file system of choice. ext4 is probably the best all around choice for Linux. If you are dual booting and want Windows AND Linux to access data (programs should not be placed on this storage), use NTFS.
* create a directory somewhere under / to hold the "mount point" for the partition+ file system(s) you have created.
* copy an existing line in the /etc/fstab that uses the same file system you created onto a new line. Change the device, mount point, and consider changing the options.
* mount the new file system (**mount -a**).  
* Consider changing the fstab from device-based mounting to UUID-based mounting.
* setup backups for the new storage. Get backup religion before it is too late. Brand new HDDs fail all the time.

All these commands should be performed with sudo.

---

### Post by nerdtron on 2013-08-31
And when you are done mounting your partitions, here's a tutorial on how to setup a samba share so that windows and linux systems can access the drives and upload files to your server.
[http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/)

---

### Post by CharlesA on 2013-08-31
> **nerdtron said:**
> And when you are done mounting your partitions, here's a tutorial on how to setup a samba share so that windows and linux systems can access the drives and upload files to your server.
[http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/)

Huh. I've never had to install winbind with samba, even on my desktop install. :shock:

I prefer [this]("http://charlesa.net/tutorials/ubuntu/samba3-ubuntu.php") tutorial, but I might be biased... ;)

---

### Post by Morbius1 on 2013-08-31
Because winbind is for something entirely different and doesn't belong anywhere near a home network.

This comes up every year or so and no matter what you do no matter how elegant the rebuttal refuting the need for such a thing it just seems impossible to eradicate. It's like "all workgroups have to match" - can't seem to get rid that one either.  So it goes......

---

### Post by Reddoug on 2013-08-31
Thanks for the quick reply's. It will look them over and see what I can figure out and post my results. 

Thanks, Doug

---

### Post by CharlesA on 2013-08-31
> **Morbius1 said:**
> Because winbind is for something entirely different and doesn't belong anywhere near a home network.

This comes up every year or so and no matter what you do no matter how elegant the rebuttal refuting the need for such a thing it just seems impossible to eradicate. It's like "all workgroups have to match" - can't seem to get rid that one either.  So it goes......

*facepalm*

I know I have heard of it before and I know what it does, and you are entirely correct. At least there are a few tutorials on how to set up a basic samba server without needing to install extra packages that aren't really needed.

@Reddoug: Good luck, if you have questions be sure to post. :)

---


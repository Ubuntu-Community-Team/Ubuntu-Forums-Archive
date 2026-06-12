---
title: "Is NAS on flash USB drive reliable?"
date: 2011-03-05
forum: Server Platforms
---

### Post by ilna on 2011-03-05
I'm estimating a NAS building with OS installed on USB flash drive (say, 16GB). Has anybody experience wrt reliability of such installation in comaprison with raw HDD drives?

---

### Post by windependence on 2011-03-05
Works just fine. I use FreeNAS on mine and it has been running for about two years straight.
 
-Tim

---

### Post by tgalati4 on 2011-03-05
You just don't get any log files.  A hybrid system gives you the benefits of both.  Boot off the hard disk, store your music on the flash drive.  Rsync the media between the hd and the flash drive.

---

### Post by BkkBonanza on 2011-03-05
I've used an Ubuntu Server OS boot usb flash stick for about a year without issues. I recently moved it to an SSD internal for speed. But it did work fine. I found 4GB more than enough as the OS really doesn't use more than 1-2 GB and that leaves space for other stuff. 

One thing is to be aware that there is great variance in USB flash stick performance. Some are lower than 9MB/s and some up to about 30MB/s. Try to choose a fast one if you want decent boot speeds.

I used external USB hard disks as well in an iSCSI config served to my network. Later I changed those to eSata and the performance was much better. But it all worked just fine.

The Linux filesystem has excellent disk caching built in and this really circumvents issues related to wear levelling and worn out flash media even for log files that get updated a lot. By keeping lots of free space it also prevents over active re-writing to flash cells.

---

### Post by ilna on 2011-03-05
Aha, so I can say, flash USB drive is robust enough to use for OS, thanks to all!

**BkkBonanza**, can you elaborate a process of installing Ubunru Server onto USB stick, please? Fast load isn't too critical for me.

---

### Post by BkkBonanza on 2011-03-05
The way I did my router system was to use my desktop to create a USB boot flash stick. From the menu, System, Administration, Startup Disk Creator is the easiest and does work. Just choose the source to be the server ISO if that's the OS you want and the target to be the USB flash stick.

Once you have that you can boot on it in the target system and do the install to a second USB flash stick. To boot on USB flash you may need to play with boot order and USB options in the BIOS. After installed remove the boot flash stick and reboot onto the final one. Of course, the startup flash you made is just temporary and can be used again for whatever else.

That was the way I did it because I didn't have another bootable media like CD-ROM or floppy. It is also possible to build the server boot flash stick directly on another system but the process is more technical and generally it's just easier to use the normal install process from the Ubuntu ISO provided.

On most modern systems the USB flash stick just behaves like a normal hard disk (mass storage device). Older systems without BIOS support are more challenging though.

---

### Post by ilna on 2011-03-05
**BkkBonanza**,

Thanks for the tips! - at last I have installed :guitar: (and updated) Ubuntu Server on a flash drive (without tuning yet, just have set noatime; will turn off unneeded services as well will disable some logs later).

Will webmin and mdadm (I'm going to use two mirrored HDD) be sufficient for remote administration (I mean samba, ftp, nfs, raid, sshd, health)?

Is it good idea to hook ethernet inteface down event with server shutting down? Does anybody use this trick (and how it is configured)?

---

### Post by ilna on 2011-03-05
> **tgalati4 said:**
> You just don't get any log files.  A hybrid system gives you the benefits of both.  Boot off the hard disk, store your music on the flash drive.  Rsync the media between the hd and the flash drive.I don't need any sync/copy between flash drive and SATA HDD. Flash drive will be used as OS to boot only. HDDs will be used for data only.

---

### Post by BkkBonanza on 2011-03-05
> **ilna said:**
> **BkkBonanza**,
Will webmin and mdadm (I'm going to use two mirrored HDD) be sufficient for remote administration (I mean samba, ftp, nfs, raid, sshd, health)?

Is it good idea to hook ethernet inteface down event with server shutting down? Does anybody use this trick (and how it is configured)?

I've always just used ssh command line for admin. I'm sure webmin gives a more friendly interface but I can't comment on whether you can do everything with it. 

I haven't done anything unusual with the ethernet interface. The only thing I did was make sure the ACPI settings enabled the power button to send a shutdown signal. There's some forum posts about that and I find it handy to poweroff when I want to. Otherwise, I just ssh in and do stuff.

I don't think you'd want to shutdown the machine when the interface goes down. I've found that sometimes I need to bring the interface down or restart networking when some problem occurs with my net connection. It may be useful to setup some monitoring scripts and restart networking or even reboot if connectivity fails, but I haven't needed that so far.

---

### Post by ilna on 2011-03-05
> **BkkBonanza said:**
> I've always just used ssh command line for admin. I'm sure webmin gives a more friendly interface but I can't comment on whether you can do everything with it. 

I haven't done anything unusual with the ethernet interface. The only thing I did was make sure the ACPI settings enabled the power button to send a shutdown signal. There's some forum posts about that and I find it handy to poweroff when I want to. Otherwise, I just ssh in and do stuff.

I don't think you'd want to shutdown the machine when the interface goes down. I've found that sometimes I need to bring the interface down or restart networking when some problem occurs with my net connection. It may be useful to setup some monitoring scripts and restart networking or even reboot if connectivity fails, but I haven't needed that so far.
Thanks for sharing!

---

### Post by kgatan on 2011-03-09
Its not recommended to use flash based drives for a journaling system as Ubuntu since it writes alot to the drive.
Flash drives have a limited number of cycles before they break down, about 100.000 if wiki is correct.

FreeNAS on the other hand does not have this issue since it is run from memory and will only load the OS from the drive.

SSD memories does not have this issue.

---

### Post by ilna on 2011-03-09
> **kgatan said:**
> Its not recommended to use flash based drives for a journaling system as Ubuntu since it writes alot to the drive.
Flash drives have a limited number of cycles before they break down, about 100.000 if wiki is correct.

FreeNAS on the other hand does not have this issue since it is run from memory and will only load the OS from the drive.

SSD memories does not have this issue.
It possible to minimize writing with mounting /tmp, /var/lock, /var/run (and even /var/log) to tmpfs in RAM. 

And it is possible to dd flash drive to file (backup) and then to write this file to another (different manufacturer) flash drive (even with larger volume) to get the same bootable OS on the new flash drive (have tried, and it works).

---

### Post by BkkBonanza on 2011-03-09
I've read up a lot on the flash wearing out. Mostly it's not a concern unless you do unusually highly active (constant) writing to disk. The journalling file systems only journal  meta data by defult settings and are not particularly bad in this respect. Some studies by engineers posted by the IEEE looked at the math needed to wear out flash (with wear leveling) and concluded you'd have to write data at max MB/s for years to get to that stage. 

In practical circumstances it isn't a significant concern. If you leave a good portion of free storage available then the wear leveling alogorithms rotate data through that area and reduce the chance of cell failure. And when a cell fails it is removed from use so the flash memory still functions fine.

I can't find a link to that study right now but I read it about a year ago when I was considering using flash. It was thorough enough to put to bed any concerns about flash being "not recommended" except in the most extreme situations.

You have to remember that hard disks eventually die too. Fairly often in my years experience.

A much more significant option is to make sure the file system is mounted "**noatime**" to reduce how often specific fle system data is updated. As those spots are fixed they will get written to much more often than others and cause block rotation at a higher rate.

---

### Post by ilna on 2011-03-10
> **BkkBonanza said:**
> I've read up a lot on the flash wearing out. Mostly it's not a concern unless you do unusually highly active (constant) writing to disk. The journalling file systems only journal  meta data by defult settings and are not particularly bad in this respect. Some studies by engineers posted by the IEEE looked at the math needed to wear out flash (with wear leveling) and concluded you'd have to write data at max MB/s for years to get to that stage. 

In practical circumstances it isn't a significant concern. If you leave a good portion of free storage available then the wear leveling alogorithms rotate data through that area and reduce the chance of cell failure. And when a cell fails it is removed from use so the flash memory still functions fine.

I can't find a link to that study right now but I read it about a year ago when I was considering using flash. It was thorough enough to put to bed any concerns about flash being "not recommended" except in the most extreme situations.

You have to remember that hard disks eventually die too. Fairly often in my years experience.

A much more significant option is to make sure the file system is mounted "**noatime**" to reduce how often specific fle system data is updated. As those spots are fixed they will get written to much more often than others and cause block rotation at a higher rate.
**BkkBonanza**,

I also have read somewhere about rather small additional write operations for ext3/ext4 (say, about 10-15% in not specially selected tests). And there will be plenty of free space. Of course, noatime is in use (I use it in my workstations during years)

At any case having an opportunity to backup and restore an OS with **dd** during minutes, I think the problem is eliminated at all.

---

### Post by TheR on 2011-03-17
I am booting my Ubuntu iScsi and three KVM servers exclusively from usb keys. I am using supertalent pico drives and can not tell any noticable speed difference between booting from disk or usb. Writing small files is different so apt updating is a bit slower (2-3 times). But that is about all writing that goes to drive (beside log). Statistics for five months tells that about 6GB  was written to drive, so there is no worrying about wearing out.

by
TheR

---

### Post by rubylaser on 2011-03-17
> Statistics for five months tells that about 6GB was written to drive, so there is no worrying about wearing out.
Would you post how you setup your /etc/fstab and any other things you did to minimize the writing to the drive.

---

### Post by TheR on 2011-03-18
> **rubylaser said:**
> Would you post how you setup your /etc/fstab and any other things you did to minimize the writing to the drive.

/etc/fstab noatime option when mounting root
/dev/mapper/boot-root /   ext4    noatime,errors=remount-ro 0    1

Turn swap off in /etc/rc.local
swapoff -a
 

by
TheR

---


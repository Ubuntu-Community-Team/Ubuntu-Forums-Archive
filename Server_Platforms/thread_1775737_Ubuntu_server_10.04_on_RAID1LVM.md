---
title: "Ubuntu server 10.04 on RAID1/LVM"
date: 2011-06-05
forum: Server Platforms
---

### Post by jerom_be on 2011-06-05
Hi all,

I was planning to use the following configuration on two 2TB disks (/dev/sda and /dev/sdb): 


[LIST]
[*]/dev/sda1 and /dev/sdb1 into /dev/md0 (RAID1)
[*]/dev/sda2 and /dev/sdb2 into /dev/md1 (RAID1)
[*]/dev/sda3 and /dev/sdb3 into /dev/md2 (RAID1)
[/LIST]
/dev/md0 is used as swap, /dev/md1 is used to mount /boot. On /dev/md2 there is a LVM with one VG and four logical volumes, along which /home and /. 

The setup of Ubuntu Server 10.04 ran smoothly until I had to install GRUB. It failed, noting "Unable to execute grub-install /dev/sda. This is a fatal error.". It tried to install GRUB on /dev/sda and /dev/sdb. 

After some Google'ing, some people told me not to install GRUB on /dev/sda and /dev/sdb, but to install GRUB on the RAID partition. So I tried /dev/md1, /dev/md2 and even /dev/mapper/vg-root (where / should be mounted), but that all gave me the same error. 

The only option I had was to finish the installation without installing a boot loader. But now I'm not able to boot my server... Any help is appreciated!

Thanks in advance!

---

### Post by YesWeCan on 2011-06-05
Hi.
There are no reasons I can think of why you should not be able to install Grub, per se.
If you boot from CD and run bootinfoscript and post the results here (insode code tags, use #) we can see what's going on: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by jerom_be on 2011-06-05
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>..............0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1423104 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     7,813,119     7,811,072 RAID partition (Linux)
/dev/sda2       7,813,120     9,766,911     1,953,792 RAID partition (Linux)
/dev/sda3       9,766,912 3,907,028,991 3,897,262,080 RAID partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048     7,813,119     7,811,072 RAID partition (Linux)
/dev/sdb2       7,813,120     9,766,911     1,953,792 RAID partition (Linux)
/dev/sdb3       9,766,912 3,907,028,991 3,897,262,080 RAID partition (Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1007 MB, 1007681536 bytes
31 heads, 62 sectors/track, 1024 cylinders, total 1968128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     1,968,127     1,968,066   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        99099ae2-1e5b-b3a4-f5e0-0a548daf30ef   linux_raid_member 
/dev/sda2        66414f8d-1270-c6dd-3694-6e4a1ea7ee67   linux_raid_member 
/dev/sda3        3640c044-e011-5735-cf83-a9500549d679   linux_raid_member 
/dev/sdb1        99099ae2-1e5b-b3a4-f5e0-0a548daf30ef   linux_raid_member 
/dev/sdb2        66414f8d-1270-c6dd-3694-6e4a1ea7ee67   linux_raid_member 
/dev/sdb3        3640c044-e011-5735-cf83-a9500549d679   linux_raid_member 
/dev/sdc1        2496-9C8E                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)



```

---

### Post by jerom_be on 2011-06-05
I don't know if this makes any difference, but... yesterday, I was testing some things out with an Ubuntu 11.04 Live USB. I figured out I could only see the contents of /dev/mapper after having installed 'mdadm' and 'lvm2' (learned that after some Google'ing). 

Because I was using my 11.04 Live USB for some other project now, I used a 10.04 Live USB to run the boot info script (of which the results are pasted above). After that, I thought that maybe it could make a difference if I installed 'mdadm' and 'lvm2' too, but the installation was gone after rebooting this stick. 

Does having installed 'mdadm' and 'lvm2' make any differences to the output of the script? In that case, I would run the script again with my 11.04 Live USB.

---

### Post by Gert Hulselmans on 2011-06-05
> Does having installed 'mdadm' and 'lvm2' make any differences to the  output of the script? In that case, I would run the script again with my  11.04 Live USB 	
Yes, it makes a difference.

---

### Post by YesWeCan on 2011-06-05
The problem is that your disks use GUID Partition Tables (GPT) instead of standard MBRs and Grub can not install its MBR to GPT.
I am not familiar with GPT so you'll have to Google for how to use Grub with GPT.

PS: I'm sure you are aware of this but just in case, having both partitions of a RAID1 on the same drive greatly reduces write performance.

---

### Post by tgalati4 on 2011-06-05
Putting the OS on a RAID can cause headaches during troubleshooting and recovery.  Better to put your user data on a separate RAID partition than to dump everything into RAID.  

Study the theory behind the ZFS filesystem and you will see why using 2 TB drives mirrored with software RAID  and hosting the OS can cause issues.

---

### Post by srs5694 on 2011-06-06
It's possible that adding a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) would fix the problem, but I make no promises. Note that the BIOS Boot Partition should not be (and, indeed, *cannot* be) RAIDed. I'm told you *can* create a separate BIOS Boot Partition on each disk and install GRUB simultaneously to all three disks for equivalent capabilities, though. (The BIOS Boot Partition is written to only when you install GRUB, which shouldn't be very often.)

---

### Post by Krupski on 2011-06-06
> **jerom_be said:**
> Hi all,

I was planning to use the following configuration on two 2TB disks (/dev/sda and /dev/sdb): 
...........
The only option I had was to finish the installation without installing a boot loader. But now I'm not able to boot my server... Any help is appreciated!

Thanks in advance!

My suggestion is to use a small PCI to Compact Flash adapter card or an IDE to Compact Flash adapter card and use a 4GB CF card SOLELY for Linux and use your RAID for data storage.

I do this on my server and it works great. And, being a "solid state drive", it will not fail and leave you unable to boot.

Also, being a separate 4GB "drive", it's easy to make "save your behind" backups of the OS simply by using DD (make an image of the entire CF card then GZip it). In an emergency you can boot off a live install disk and use DD to re-write a known good image back onto the CF card.

Here's a pic of my file server. The Compact Flash card in to the right, about centered up and down. It's plugged into a CF to IDE adapter card, then plugged into a PCI-E to IDE disk controller card.

[img]http://three-dog.homelinux.com/images/server.jpg[/img]

(btw, I use a 16GB card because I have it partitioned 4GB for Linux and 12GB for other stuff. Really though only 4GB is needed (actually, 2GB works fine - but I don't want to cut it that close).

Doing it this way will save you a LOT of grief.

Good luck.

-- Roger

---

### Post by jerom_be on 2011-06-13
First of all, I would like to thank you all for your helpful responses. After a week of hard labour at the office, I did find some time off to focus on my server project again. 

I did some reading and tried some different things. Some people thaught the problem was the RAID'ed swap partition: I did not want to keep swap out of the RAID, but tried it to see whether it would fix the problem. It didn't. Some other people said putting the / on an lvm was not a good idea, so I created a separate partition (on RAID) to mount /. It didn't work either. 

Finally, I read the blog of someone having exactly the same problem: [http://room118solutions.com/2011/02/08/ubuntu-10-10-server-grub-gpt-partitions/](http://room118solutions.com/2011/02/08/ubuntu-10-10-server-grub-gpt-partitions/). I followed his strategy, but got stucked almost immediately: when executing "mount -o bind /dev /mnt/ubuntu/dev" it tells me that /mnt/ubuntu/dev does not exist; after creating the dir, executing the chroot command gives me "chroot: can't execute '/bin/bash': no such file or directory". 

I'm sure I'm doing some stupid things, but I'm not familiar with the whole "chroot"-thing. Maybe some of you can help me out?

The configuration at the moment is the following:
- /dev/sda1 and /dev/sdb1 into /dev/md0, used as swap
- /dev/sda2 and /dev/sdb2 into /dev/md1, used as ext4 and mount point for /.
- /dev/sda3 and /dev/sdb2 into /dev/md2, with an LVM, one pv and three lv, among which the mount point for /home. 

Is this such an a-typical setup?

> **YesWeCan said:**
> The problem is that your disks use GUID Partition Tables (GPT) instead of standard MBRs and Grub can not install its MBR to GPT.
I am not familiar with GPT so you'll have to Google for how to use Grub with GPT.
After doing some research on Google, that indeed seems to be the problem. Nevertheless, nobody seems to have an appropriate solution to the problem. I never got the choice between GPT or MBR - to say more, I never heard of GPT before (which tells something about my dummy-ness...). 

> **YesWeCan said:**
> PS: I'm sure you are aware of this but just in case, having both partitions of a RAID1 on the same drive greatly reduces write performance.
I think I am misunderstanding you. If I create a RAID partition /dev/md0 containing, let's say, /dev/sda1 and /dev/sdb1, both partitions of the RAID are on a different drive, right? If that was not the case, having a mirroring RAID does not give any advances... Or did you mean something else?

---

### Post by YesWeCan on 2011-06-13
> **jerom_be said:**
> After doing some research on Google, that indeed seems to be the problem. Nevertheless, nobody seems to have an appropriate solution to the problem. I never got the choice between GPT or MBR - to say more, I never heard of GPT before (which tells something about my dummy-ness...). 
You are not dumb...the documentation of Grub is awful. There is a member here, oldfred, who knows exactly how to do it. Try dropping him a line. It involves creating a mini-partition for Grub to install to instead of the GPT MBR.

> I think I am misunderstanding you. If I create a RAID partition /dev/md0 containing, let's say, /dev/sda1 and /dev/sdb1, both partitions of the RAID are on a different drive, right? If that was not the case, having a mirroring RAID does not give any advances... Or did you mean something else?Sorry - my fault. I misread your first post. Looks fine today. :p

---

### Post by jerom_be on 2011-06-13
After hours of frustration, I solved the problem using this tutorial: [http://room118solutions.com/2011/02/08/ubuntu-10-10-server-grub-gpt-partitions/](http://room118solutions.com/2011/02/08/ubuntu-10-10-server-grub-gpt-partitions/). 

It could have saved me some time if I knew more about the whole chroot story. The tutorial is not complete: in step 2, first the file system has to be mounted into /mnt/ubuntu, using for instance "mount /dev/blabla /mnt/ubuntu". After that, the "mount -o bind /dev /mnt/ubuntu/dev" step can be executed.

I would like to thank everyone that read or replied upon this thread, for helping me finding out what the problem was!

---

### Post by psusi on 2011-06-13
To install grub on disks using GPT, you need to create a 1 MB bios_grub partition.  You also don't need a separate /boot partition, and can put / on LVM just fine.  So you only need two partitions on each disk, one for bios_grub, and one to use for the raid, then use LVM to carve that up into logical volumes.

---

### Post by Jimbro727 on 2011-09-13
> **jerom_be said:**
> After hours of frustration, I solved the problem using this tutorial: [http://room118solutions.com/2011/02/08/ubuntu-10-10-server-grub-gpt-partitions/](http://room118solutions.com/2011/02/08/ubuntu-10-10-server-grub-gpt-partitions/). 

It could have saved me some time if I knew more about the whole chroot story. The tutorial is not complete: in step 2, first the file system has to be mounted into /mnt/ubuntu, using for instance "mount /dev/blabla /mnt/ubuntu". After that, the "mount -o bind /dev /mnt/ubuntu/dev" step can be executed.

I would like to thank everyone that read or replied upon this thread, for helping me finding out what the problem was!

Hey Jerom,

I'm glad you got this figured out - sorry I missed this thread while you were working on the problem.  I'm the author of that article, and it does appear that I left out that ***crucial*** step (mounting the filesystem) .  I don't know how I could have missed that.  I just updated the post - I'm glad you were able to figure that out and continue along with the post.

Thanks,
Jim

---

### Post by Chores on 2011-09-21
Hi,
Utter newbie here but I also have achieved success with the 
[http://room118solutions.com/2011/02/...pt-partitions/]("http://room118solutions.com/2011/02/08/ubuntu-10-10-server-grub-gpt-partitions/") 
link instructions. Thanks Jim.
During my install I lucked into a solution that may help others. When setting up the partitions with the graphical interface I started with the first partition on each drive being a 1MB partition that I did not make part of the raid. I also made a 8GB swap partition and a 2TB / partition which I made part of the RAID. 3 partitions in total.
When I got the error message trying to install the boot loader I followed the instructions but found there wasn't enough room at the beginning of the drive to put a BIOS boot partition. Using Parted I used the rm command as shown on the help screen to remove the first 1MB partitions I had made. This freed up room which was the right size to make the new BIOS boot partition. I am sure there are other ways to do this but I avoided having to make all new partitions and reinstalling Ubuntu.
Eric

---


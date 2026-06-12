---
title: "live import into VMware - Error!"
date: 2011-03-21
forum: Virtualisation
---

### Post by t-hall on 2011-03-21
Hi,

I'm struggling a bit here. I would really be grateful for some help filling the gaps, correcting me or a even complete explanation in basic terms.

I have a ubuntu 10.04.01 LTS server hosting Zimbra and what I now know to be GRUB2. This machine has software raid and I need to import it into VMware. It also has a consistent load average of 5-6 on a dual core processor. Another factor is one of the drives (2 x 1TB drives) has failed and it is running with one.
  
When I try and import I get “an error occurred during the conversion”
  Error: Unable to reconfigure the destination virtual machine
right after:  Installing the GRUB boot loader.
   
  This is after about 40 minutes of the importing process.

I have looked about and have come across this: [http://www.waltercedric.com/component/content/article/193-technical/1593-make-a-vmware-copy-of-a-live-linux-server.html](http://www.waltercedric.com/component/content/article/193-technical/1593-make-a-vmware-copy-of-a-live-linux-server.html)
   
  As well as a number of pages which claim importing Ubuntu with software raid does not go down well. 
   
  From what I have read breaking the array is the way to go. I have come across this: [http://ubuntuforums.org/showthread.php?t=1693950](http://ubuntuforums.org/showthread.php?t=1693950) where Rubylaser suggests booting from livecd, zeroing superblocks (I managed that) and removing mdadm.conf (managed that) 
   
  Updating fstab (help!) and grub2 (Help!!) I need help, I have little idea what I need to do with these. 
   
  And even if I do all of that I do not know if it will work! Or if I am going in a completely irrelevant direction. 
   


   
  Even if you cannot help thanks for taking the time to read this, it is appreciated 
   




  Rock on
  







 
  Here is an fdisk –l , the grub files are on sda3 the data on sda1 (you probably would have told me that anyway)
   
  peter@ks-epsilon:~$ sudo fdisk -l
   
  Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
  255 heads, 63 sectors/track, 121601 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk identifier: 0x0009f40b
   
     Device Boot      Start         End      Blocks   Id  System
  /dev/sda1               1         122      975872   fd  Linux raid autodetect
  Partition 1 does not end on cylinder boundary.
  /dev/sda2             122         608     3904512   82  Linux swap / Solaris
  Partition 2 does not end on cylinder boundary.
  /dev/sda3             608      121602   971880152   fd  Linux raid autodetect
   
  Disk /dev/md0: 999 MB, 999227392 bytes
  2 heads, 4 sectors/track, 243952 cylinders
  Units = cylinders of 8 * 512 = 4096 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk identifier: 0x00000000
   
  Disk /dev/md0 doesn't contain a valid partition table

---

### Post by Hedgehog1 on 2011-03-22
Oh lordy - RAID and Vbox in the same post.

Based on the fact that one drive has failed, and the system is running on the other drive, I am assuming you are running RAID 1 on the 'old' box.

Lets see if we can help a little here.

Would you please post the contents of the text file /etc/fstab on your next post (fstab: **F**ile **S**ystem **TAB**le).

Based on what the /etc/fstab file shows, we will try to get 'old' the system off of software raid and using the remaining disk as a single 'traditional' disk.  Once that is done, I don't think you need (or even want to) remove grub2 (grub: **GR**and **U**nified **B**oot loader) because that is how your Ubuntu system boots up.


***The Hedge***

:KS

p.s. This is a WHOPPER of a first post.

---

### Post by t-hall on 2011-03-22
Hi Hedgehog1

thanks for replying! (sorry about the whopper)


It is Raid 1

peter@ks-epsilon:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md1 during installation
UUID=8db67fe6-908d-457e-9b58-0074ea59920e /               ext4    errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=e1b821dd-6d3d-4d9a-b31e-9063726e7c47 /boot           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=89043110-61f9-44f8-8e01-10ba7e32c1fd none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=dc9b052d-87a7-4c63-9c31-0f02f2f5c8f7 none            swap    sw              0       0
peter@ks-epsilon:/etc$

---

### Post by Hedgehog1 on 2011-03-22
> **t-hall said:**
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on **/dev/md1** during installation
UUID=8db67fe6-908d-457e-9b58-0074ea59920e /               ext4    errors=remount-ro 0       1
# /boot was on **/dev/md0** during installation
UUID=e1b821dd-6d3d-4d9a-b31e-9063726e7c47 /boot           ext4    defaults        0       2
# swap was on **/dev/sda2** during installation
UUID=89043110-61f9-44f8-8e01-10ba7e32c1fd none            swap    sw              0       0
# swap was on **/dev/sdb2** during installation
UUID=dc9b052d-87a7-4c63-9c31-0f02f2f5c8f7 none            swap    sw              0       0

As a note, If I do suggest changes to a line in your /etc/fstab file, do not delete the old line, instead put a '#' at the front of the line to make it a comment.  This way you can revert to an earlier setting.

Thanks for this.  We next need to determine what drives are really still working, and what UUIDs the 'actual' devices have.

If you would, please, do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

p.s. I see two drives, called /dev/sd**a** and dev/sd**b**.  Has the 'dead' drive been removed from the system?

---

### Post by Hedgehog1 on 2011-03-22
You asked about other ways to move the data from the real disk to the virtual disk.

The basic way to do this is with **tar** (**T**ape **AR**chive).  It's name shows it's age, but don't be put off.  You can save .tar files to a disk or a tape.  Few folks use tape now-a-days.

Here is a brief summary of the tar options:

**[SIZE="3"]Operating Tape Drives from Linux[/SIZE]**

[SIZE="2"]**SCSI tape device names:**[/SIZE]

The st driver provides the interface to a variety of SCSI tape devices under Linux.

* First (auto rewind) SCSI tape device name: /dev/st0
* Second (auto rewind) SCSI tape device name: /dev/st1

* First the non-rewind SCSI tape devices: /dev/nst0
* Second the non-rewind SCSI tape devices: /dev/nst1

[SIZE="2"]**IDE tape device names:**[/SIZE]

The ht driver provides the interface to a variety of IDE tape devices under Linux.

* First (auto rewind) IDE tape device name: /dev/ht0
* Second (auto rewind) IDE tape device name: /dev/ht1

* First the non-rewind IDE tape devices: /dev/nht0
* Second the non-rewind IDE tape devices: /dev/nht

[SIZE="2"]**Examples** [/SIZE](Please replace **/dev/st0** with your tape drive name):

Rewind tape drive:
```
mt -f /dev/st0 rewind
```
Backup directory /www and /home with tar command (z &#8211; compressed):
```
tar -czf /dev/st0 /www /home
```
Find out what block you are at with mt command:
```
mt -f /dev/st0 tell
```
Display list of files on tape drive:
```
tar -tzf /dev/st0
```
Restore /www directory:
```
cd /
mt -f /dev/st0 rewind
tar -xzf /dev/st0 www
```
Unload the tape:
```
mt -f /dev/st0 offline
```
Display status information about the tape unit:
```
 mt -f /dev/st0 status
```
Erase the tape:
```
mt -f /dev/st0 erase
```

To backup to multiple tape use the following command (backup /home file system):
```
tar -clpMzvf /dev/st0 /home
```
To compare tape backup, enter:
```
tar -dlpMzvf /dev/st0 /home
```
To restore tape in case of data loss or hard disk failure:
```
tar -xlpMzvf /dev/st0 /home
```

[SIZE="2"]**tar** options are:
* **d**: find differences between archive and file system
* **x**: extract files from an archive
* **l**: list the contents of an archive (Lower case 'L'
* **p**: ignore umask when extracting files
* **M**: create/list/extract multi-volume archive (multiple tapes)
* **z**: Compress backup using gzip
* **v**: verbosely list files processed
* **f */dev/st0***: Tape device name (replace ***/dev/st0*** with your tape device name)[/SIZE]

You can route the 'tape' output to disk instead of tape, create the VM disk manually, and then restore the .tar to build the VM ware disk.

It may take a little fooling about, but it is a possible option.

***The Hedge***

:KS

---

### Post by t-hall on 2011-03-22
Hi Hedge,

Thanks again, the failed drive has been removed and never replaced, that's another side story involving WD 

the output from the bootinfo:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for .

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     1,953,791     1,951,744  fd Linux raid autodetect
/dev/sda2           1,953,792     9,762,815     7,809,024  82 Linux swap / Solaris
/dev/sda3           9,762,816 1,953,523,119 1,943,760,304  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        470e5d3b-8366-c56b-c7d7-5aa712b1fbec   linux_raid_member                               
/dev/sda2                                               swap                                     
/dev/sda3        8db67fe6-908d-457e-9b58-0074ea59920e   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md1 during installation
UUID=8db67fe6-908d-457e-9b58-0074ea59920e /               ext4    errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=e1b821dd-6d3d-4d9a-b31e-9063726e7c47 /boot           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=89043110-61f9-44f8-8e01-10ba7e32c1fd none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=dc9b052d-87a7-4c63-9c31-0f02f2f5c8f7 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200



Rock on

---

### Post by t-hall on 2011-03-22
I should add I have managed to ghost it at the weekend. and have restored it to an identical box with an identical hard disk, so I can muck around with it without comprimising the live system.

---

### Post by Hedgehog1 on 2011-03-23
I have read the script output a few times now.

I have an idea of what to do to get the remaining RAID 1 disk back to being a 'plain old disk', however I am a true-believer in hardware RAID (***Hardware RAID: A Hedgehog's best friend!***) and am still guessing here on software RAID.

I am going to ask another forum member that has more practical experience in software RAID to look at this.

***The Hedge***

:KS

---

### Post by t-hall on 2011-03-23
Thanks again Hedge for your time, you have quite a bit of it with my problem. 

I agree on the raid front when I get it on VM (however long it takes) it will be on a Pucka Raid 6 Array. 

Rock on

---

### Post by deconstrained on 2011-03-23
Are you certain that the two problems are related? The error "Unable to reconfigure the destination virtual machine" may not be caused by the drive failure.

As for the RAID, you determine which of the drives has failed by looking at /proc/mdstat. Then, mark the appropriate drive as failed, then remove it (assuming the partition in question is sdb1);

mdadm --manage /dev/md0 -f /dev/sdb1
mdadm --manage /dev/md0 -r /dev/sdb1

Perform any diagnostics on the hard drive (i.e. with SMART or the like)
[http://www.linuxjournal.com/magazine/monitoring-hard-disks-smart](http://www.linuxjournal.com/magazine/monitoring-hard-disks-smart)
and if it has indeed gone bad, then remove it. Otherwise, if it's just a corrupt superblock or some other problem and not the drive physically going bad, **then** you might try zeroing the superblock and then re-inserting it into the array;

mdadm --manage /dev/md0 --add /dev/sdb1

---

### Post by t-hall on 2011-03-24
I honestly do not know now, 

during the initial import attempts I had the message "there is no /boot device mounted" after searching for a few weeks software raid being the cause came up pretty constantly. 

The Drive had failed and was sent back to manufacturer (so no longer present), it has taken three attempts before a same size drive was returned. Since then I now I want to migrate to Vmware I’m thinking keeping the software raid may be unnecessary. 

I have added the output from mdstat for info.

peter@ks-epsilon:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda1[0]
      975808 blocks [2/1] [U_]

unused devices: <none>
peter@ks-epsilon:~$#

I’ll have another go at the import part and post a more complete log of it, and i'll have a go at failing the sdb drive tonight.

Thanks for replying.

Rock on

---

### Post by t-hall on 2011-03-24
from the VM Import: log highlights

Error: Unable to reconfigure the destination virtual machine.
Installing the GRUB boot loader.
Starting the reconfiguration of the destination virtual machine.
Completed cloning the volume mounted on '/' from '10.133.132.20'.
Starting to clone the volume mounted on '/' from '10.133.132.20'.
Formatting the destination partitions.
Partitioning the destination disks.

---

### Post by fjgaude on 2011-03-24
My experience with software raid points to first umounting the arry, then stopping it, then you can zero the superblock of the bad drive. As long as the array is active you can't zero superblocks.

I know the bad drive isn't there anymore, but I think you still have to think that it is.

---

### Post by t-hall on 2011-03-24
I've done the zeroing of superblocks from the live cd, i am a bit clueless about what I need to do with fstab and grub2

there are three partitions from what i can ssee, the filesystem (sda1) the swap (sda2) and the boot (sda3). I've posted some stuff so feel free to correct me or speak in basic.

---

### Post by fjgaude on 2011-03-24
Can you active the VM from the VBox console? What makes you think you have to do anything with the fstab and grub2?

The transfer likely brought all of it over and as a guest the console will ignore them.

I've never tried to do this, what you are doing. A clean install would be so much easier, if you had backup of your important data.

---

### Post by deconstrained on 2011-03-25
If the failed drive is already long gone (missed that detail earlier) then there's no need to mark it as failed, or at least, there's nothing left to do.

---

### Post by fjgaude on 2011-03-25
> **deconstrained said:**
> If the failed drive is already long gone (missed that detail earlier) then there's no need to mark it as failed, or at least, there's nothing left to do.

Are you sure about this? The md data still thinks that the array, in this case, has two drives?

---

### Post by deconstrained on 2011-03-26
> **fjgaude said:**
> Are you sure about this? The md data still thinks that the array, in this case, has two drives?
...I meant, except for replacing the drive. \\:D/

According to the last /proc/mdstat posted, there's only one device there. Adding a new drive should fill that gap.

---


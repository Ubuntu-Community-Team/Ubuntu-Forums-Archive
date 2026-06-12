---
title: "Create partitiontable on extra harddisk"
date: 2010-06-07
forum: Server Platforms
---

### Post by imjakes on 2010-06-07
I have added a new harddisk to my system and would now like to use this as simple storrage.

This is my fdisk info 

> jakes@jakes-server:/bin$ sudo fdisk -lu
[sudo] password for jakes:

Disk /dev/sda: 1000.2 Gb, 1000204886016 byte
255 heads, 63 sectors/track, 121601 cylinders, i alt 1953525168 sektorer
Units = sektorer of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b36a6

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sda1   *        2048  1942208511   971103232   83  Linux
/dev/sda2      1942210558  1953523711     5656577    5  Udvidet
/dev/sda5      1942210560  1953523711     5656576   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 Gb, 1000204886016 byte
255 heads, 63 sectors/track, 121601 cylinders, i alt 1953525168 sektorer
Units = sektorer of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb indeholder ikke en gyldig partitionstabel
(Danish for "does not contain a legal partition table"


Now my quistion is how do i mount this disk?

Im running Ubuntu command-line server (is this called debian or what?)

Hope you can help

Regards,
Jacob

---

### Post by FemmeFatale on 2010-06-07
If you prefer command line tools, you might start with:

sudo fdisk /dev/sdb

a menu will appear on your screen, choose you want to add new primary partition. You will be asked for a number of that partition - type 1, if it asks for cylinder - type 1 again. Once you are done, you have to format it typing (I believe you want to use it under windows, as well):

sudo mkfs -t fat32 /dev/sdb1

and finally, to mount:

sudo mount /dev/sdb1 /media/your_new_hard_drive_mount_point
[FONT=monospace]
[/FONT]Hope that helps.

---

### Post by imjakes on 2010-06-07
Great that helped.

I have mountet the disk to /home/fileshare2

I have added that to samba like this:
> 
[Fileshare2]
path = /home/fileshare2
read only = No
guest ok = Yes


But i am not able to write anything to it.

I have tryed to change owner by using :

jakes@jakes-server:/etc/samba$ sudo chown jakes:jakes /home -R
chown: change owner for '/home/fileshare2': Operation not permitted

And then i tryed :
sudo chmod 777 /home -R

But it did not help

Any ideas?

---

### Post by oldfred on 2010-06-07
You cannot set permissions or ownership on non-linux partitions:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by imjakes on 2010-06-08
Great that solved my problem, thanks.

---


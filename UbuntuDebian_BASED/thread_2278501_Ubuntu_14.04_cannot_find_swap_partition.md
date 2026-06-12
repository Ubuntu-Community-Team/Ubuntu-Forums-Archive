---
title: "Ubuntu 14.04 cannot find swap partition"
date: 2015-05-17
forum: Ubuntu/Debian BASED
---

### Post by bwanaaa on 2015-05-17
Laptop had Windows 7.
Installed Ubuntu 14.04
--no problem. grub2 gave appropriate choices
Added mate theme
--no problem. 
Installed Kali Linux 1.1.0
--initially defaulted to grub boot menu but got back to grub 2  with grub customizer
Choosing to boot into windows or kali linux is ok.
Choosing to boot into Ubuntu show the mate boot screen with this dialog

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Disk drive UUID=4f135f04-2b2f-4a9e-a108-53e00e6167ae cannot be found
Press S to skip or M for manual
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 
sudo fdisk -l  shows:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x581395e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS/exFAT
/dev/sda2          411648   507443649   253516001    7  HPFS/NTFS/exFAT
/dev/sda3       507445246   945829887   219192321    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda4       945829888   976773167    15471640    2  XENIX root
/dev/sda5       885022720   945829887    30403584    7  HPFS/NTFS/exFAT
/dev/sda6       507445248   690067455    91311104   83  Linux
/dev/sda7       868362240   885020671     8329216   82  Linux swap / Solaris
/dev/sda8       690069504   868360191    89145344   83  Linux

Partition table entries are not in disk order
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

gksudo gedit /etc/fstab  shows

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=b0c6fcd3-3a45-497f-99dd-4c619ed98b28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4f135f04-2b2f-4a9e-a108-53e00e6167ae none            swap    sw              0       0
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I remember when I installed Kali that I specified the free space on the drive as  ext4 and the pre-existing swap partition (from the pre-existing ubuntu 14.04 install) as swap. I saw no reason to have two swap partitions

How can I eliminate the error that occurs on the mate screen during ubuntu boot?

---

### Post by Bucky Ball on 2015-05-17
Please provide the output of:

```
sudo blkid
```

How are you installing the OSs after the first one? Are you manually partitioning and using the existing /swap or you are letting them do their own thing and create a new /swap for each install? The latter is not necessary nor desirable (same applies if you are creating a new /home partition for each install).

As you install each new OS, they install their grub to the same place, over the last grub, unless you are manually telling the install to put grub elsewhere. Kali was the last? We concentrate on what that is doing with grub and fstab.

PS: You can hit 's' to skip and continue without swapon to sort this out without an issue (if you have a decent amount of RAM).

---

### Post by bwanaaa on 2015-05-17
output of sudo blkid

-many screens were presente
```
/dev/sda1: UUID="1C72C0A372C082CE" TYPE="ntfs" 
/dev/sda2: UUID="A0F2C00FF2BFE824" TYPE="ntfs" 
/dev/sda4: LABEL="LENOVO_PART" UUID="884ECE6E4ECE551A" TYPE="ntfs" 
/dev/sda5: LABEL="LENOVO" UUID="265CF03E5CF009F7" TYPE="ntfs" 
/dev/sda6: UUID="b0c6fcd3-3a45-497f-99dd-4c619ed98b28" TYPE="ext4" 
/dev/sda7: UUID="b391130e-4db4-4bd6-8804-0c604ae877ee" TYPE="swap" 
/dev/sda8: UUID="83b9aa16-5e0c-4baf-864c-c4bf64c624d0" TYPE="ext4" 
```

windows 7 was preexisting on the laptop
the windows 7 partiton was shrunk and free space created
ubuntu was installed w default params
---everything was fine at this point
kali was installed using gui
- partitioning screens offerred option to change partitions
-i identified the preexisting swap partition and changed 'do  not use' to 'swap'

kali will boot without any swap error dialog
ubuntu boots but presents swap error dialog

---

### Post by sudodus on 2015-05-17
Maybe Kali 'stole' the swap partition from Ubuntu. Please continue with some more output from terminal window commands.

```
cat /etc/fstab
```

```
sudo lsblk -fm
```

```
swapon -s
```

Edit: Do this while booted into Ubuntu if it is possible.

---

### Post by Bucky Ball on 2015-05-17
*Thread moved to **Ubuntu/Debian based**.*

This is starting to look more like a Kali related problem as it occurred after the Kali install. Might improve your chances if you post on their forum also. ;)

---

### Post by bwanaaa on 2015-05-17
fstab is in the first post


> sudo lsblk -fm


NAME   FSTYPE LABEL       MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                  sda    465.8G root  disk  brw-rw----
&#9500;&#9472;sda1 ntfs                          &#9500;&#9472;sda1   200M root  disk  brw-rw----
&#9500;&#9472;sda2 ntfs                          &#9500;&#9472;sda2 241.8G root  disk  brw-rw----
&#9500;&#9472;sda3                               &#9500;&#9472;sda3     1K root  disk  brw-rw----
&#9500;&#9472;sda4 ntfs   LENOVO_PART            &#9500;&#9472;sda4  14.8G root  disk  brw-rw----
&#9500;&#9472;sda5 ntfs   LENOVO                 &#9500;&#9472;sda5    29G root  disk  brw-rw----
&#9500;&#9472;sda6 ext4               /          &#9500;&#9472;sda6  87.1G root  disk  brw-rw----
&#9500;&#9472;sda7 swap               [SWAP]     &#9500;&#9472;sda7     8G root  disk  brw-rw----
&#9492;&#9472;sda8 ext4                          &#9492;&#9472;sda8    85G root  disk  brw-rw----
sr0                                  sr0     1024M root  cdrom brw-rw----


> 
swapon -s
Filename				Type		Size	Used	Priority

but if run the 'disks' app and 'play' the swap file

> swapon -s
Filename				Type		Size	Used	Priority
/dev/sda7                               partition	8329212	0	-1

---

### Post by Elfy on 2015-05-17
> # swap was on /dev/sda7 during installation
UUID=4f135f04-2b2f-4a9e-a108-53e00e6167ae none swap sw 0 0

> /dev/sda7: UUID="b391130e-4db4-4bd6-8804-0c604ae877ee" TYPE="swap" 

swap's UUID has changed.

swapoff -a

edit and save fstab with the new UUID for swap

swapon -a 

to check it

---

### Post by bwanaaa on 2015-05-17
@Elfy

Yes! that fixed it. Thank you. I should have noticed the discrepancy when looking at the blkid compare to the stab but my eyes just glossed over the pile of hex.

Now I have to figure out why the boot process takes so long since I installed Kali. I'll post a new thread for that.

---


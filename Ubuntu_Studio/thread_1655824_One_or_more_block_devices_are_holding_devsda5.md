---
title: "One or more block devices are holding /dev/sda5"
date: 2010-12-30
forum: Ubuntu Studio
---

### Post by nighthawk77 on 2010-12-30
I've been getting this message when I want to mount logical storage partition. I have both Windows7 and UbuntuStudio 64bit. In windows storage partiton works well and I did reformat but still Ubuntu cannot mount it. :confused:
Thanx for your help!

---

### Post by dasan on 2010-12-30
make sure that you didn't ener anything wron in /etc/fstab
and you can take some preliminary steps like checking drive from windows for errors and so

---

### Post by nighthawk77 on 2010-12-30
hi
when I open fstab file it's read only and I get /dev/sda5 configured as swap:
# / was on /dev/sda1 during installation
UUID=351b0f4b-8bca-4e26-a362-bf73c57ccdee /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=dac038c4-8b8c-4aef-bcf8-f574e6775a91 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

so is there a safe way modify this?
Thanx

---

### Post by matt_symes on 2010-12-30
Hi

> **nighthawk77 said:**
> I've been getting this message when I want to mount logical storage partition. I have both Windows7 and UbuntuStudio 64bit. In windows storage partiton works well and I did reformat but still Ubuntu cannot mount it.
Thanx for your help!

First things first. You need to identify the partition you want to mount at startup before you enter it into fstab, so open a terminal and type

```
sudo blkid
```

and

```
sudo fdisk -l
```

Enter you password for both. You will not see it echoed on the screen. This is normal and for security.

Post the results back here along with the partition name you think is the one you want to mount.

BTW: /etc/fstab will be 'read only' if you open it with your privileges as it is owned by root. You have to use sudo to gain temporary admin privileges to save the file after you edit it.

Kind regards

---

### Post by nighthawk77 on 2010-12-30
Ok, first I got:
/dev/sda1: LABEL="System Reserved" UUID="1E54478154475B23" TYPE="ntfs" 
/dev/sda2: UUID="01CB59846EC042C0" TYPE="ntfs" 
/dev/sda5: LABEL="SKLADIM-^ZTE" UUID="1F13-8D00" TYPE="vfat" 
/dev/sda6: UUID="01CB62E114B5E620" TYPE="ntfs" 
/dev/sdb1: UUID="351b0f4b-8bca-4e26-a362-bf73c57ccdee" TYPE="ext4" 
/dev/sdb5: LABEL="swap" UUID="dd550c04-3b71-4901-a70b-59234a57e6e9" TYPE="swap" 
/dev/mapper/cryptswap1: UUID="8bbcd4fe-b23b-44de-89cd-938b4b544433" TYPE="swap"

...then, for sudo fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf35393c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       13067   104852052+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           13067       38233   202146836+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5           13067       31733   149937448+   7  HPFS/NTFS
/dev/sda6           31733       38233    52209260+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00059889

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9328    74920960   83  Linux
/dev/sdb2            9328        9730     3227649    5  Extended
/dev/sdb5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/dm-0: 153.5 GB, 153535947264 bytes
255 heads, 63 sectors/track, 18666 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93311eef

Disk /dev/dm-0 doesn't contain a valid partition table

It is /dev/sda5 partition problem.
Note I have two physical disks. Ubuntu is located on 80GB hard drive

---

### Post by matt_symes on 2010-12-30
Hi

A quick question. Any reason /dev/sda5 is FAT and not NTFS?

Kind regards

---

### Post by nighthawk77 on 2010-12-30
I tried to reformat partition from windows. Tried both NTFS and FAT but no results.

---

### Post by matt_symes on 2010-12-30
Hi

> I tried to reformat partition from windows. Tried both NTFS and FAT but no results.

If you want to, you can format partitions using gparted in Ubuntu. You will have to install it either through synaptic package manager (search for gparted) or through the terminal (sudo apt-get install gparted). 

It allows you to format partitions to many different formats and would enable you to format the partition to ntfs.

Do you want to do this (i can talk you through it) or keep as FAT?

The reason i ask is because some people prefer NTFS.

Kind regards

---

### Post by nighthawk77 on 2010-12-31
Ok. I did install Gparted through terminal. I reformatted partition successfully to NTFS, but after restarting PC same happens...some block devices holding that partition. I believe it's something related with Ubuntu boot menu and "fstab" file. But I'm not linux expert so I'm confused.
And thanx for your help!

---

### Post by matt_symes on 2010-12-31
Hi

No problem. Lets try to mount it manually.

Open a terminal and type.

```
sudo mkdir /media/win_storage
```

Enter password. Then type

```
sudo mount -t ntfs /dev/sda5 /media/win_storage/
```

Does this mount it? If it does we will update fstab next to mount it at startup.

EDIT: TO TEST type *ls /media* at the terminal. win_storage will have a background colour.

to unmount type

```
sudo umount /media/win_storage
```

Kind regards

---

### Post by nighthawk77 on 2010-12-31
Here's what I got:

nighthawk77@UbuntuStudio:~$ sudo mkdir /media/win_storage
[sudo] password for nighthawk77: 
mkdir: cannot create directory `/media/win_storage': File exists
nighthawk77@UbuntuStudio:~$ sudo mount -t ntfs /dev/sda5 /media/win_storage/
fuse: mount failed: Device or resource busy
nighthawk77@UbuntuStudio:~$

---

### Post by matt_symes on 2010-12-31
Hi

> mkdir: cannot create directory `/media/win_storage': File exists

That is odd. I would be very surprised if that directory was already there (You did no try to create it twice did you?). I think you should run a file system check on your partition.

Open a terminal and type

```
sudo touch /forcefsck
```

then reboot your PC. It will run a file system check.

Once you have done that could you repost back the output of

```
sudo blkid
```

and we will just add it to fstab and see what happens regardless. It needs to be done again because the partition is NTFS now.

Kind regards

---

### Post by nighthawk77 on 2011-01-04
SOLVED
After I deleted partition from Windows and leave empty unformatted space, I shutdown the Windows and boot into Ubuntu and I did manage to get to partition and format it with disk utility software in Ubuntu. 
Now I can copy my files back again to that location. I'm not quite sure what went wrong in the first place. It happens suddenly but thank you very much for your help. I appreciate it! 
Regards

---

### Post by M. Fawzy on 2011-07-18
#13 looks the silliest thing in the world, however I assure it really works :D:D ... thanks nightwalk77 :)

---

### Post by jbalcedo on 2011-07-26
Hi guys out there! I'm really dumbfounded with a similar situation I've been unable to solve. My box is running Lucid Lynx 10.04.3, and when I try to mount a logical partition (which lives inside an extended partition I created long ago, and *am able to mount with my old Red Hat 9.0 OS*), I keep getting this error message, partition number aside.
Now, here's the output of **udisks --show-info /dev/sda6**

Showing information for /org/freedesktop/UDisks/devices/sda6
  native-path:                 /sys/devices/pci0000:00/0000:00:02.5/host0/target0:0:0/0:0:0:0/block/sda/sda6
  device:                      8:6
  device-file:                 /dev/sda6
    presentation:              /dev/sda6
    by-id:                     /dev/disk/by-id/ata-HDS728040PLAT20_PFD110S1C1V22E-part6
    by-id:                     /dev/disk/by-id/scsi-SATA_HDS728040PLAT20_PFD110S1C1V22E-part6
    by-id:                     /dev/disk/by-id/wwn-0x5000cca202c0d639-part6
    by-id:                     /dev/disk/by-uuid/0BF3-0C4C
    by-path:                   /dev/disk/by-path/pci-0000:00:02.5-scsi-0:0:0:0-part6
  detected at:                 Tue 26 Jul 2011 01:53:22 PM ART
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Tue 26 Jul 2011 01:53:22 PM ART)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        9220506624
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        vfat
  version:                     FAT32
  uuid:                        0BF3-0C4C
  label:                       JAB_HD#2
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    6
    type:                      0x0c
    flags:                    
    offset:                    31947019776
    alignment offset:          0
    size:                      9220506624
    label:                     
    uuid:                      

which is exactly right and describes precisely the partition.
Just in case, this is the output of **fdisk -l /dev/sda**:

Disk /dev/sda: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48dc48dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         383     3076416    7  HPFS/NTFS
/dev/sda2             384         393       80325   83  Linux
/dev/sda3             394         424      249007+  82  Linux swap / Solaris
/dev/sda4             425        5005    36796882+   f  W95 Ext'd (LBA)
/dev/sda5             425        3884    27792418+  83  Linux
/dev/sda6            3885        5005     9004401    c  W95 FAT32 (LBA)

As you can see, the device holds several partitions that I'm using normally, such as the swap space, the NTFS on /dev/sda1 (mounts without a hitch with userspace tools, namely Places->"Label of /dev/sda1") and (which is really why I can't understand the problem) the *ext3 partition /dev/sda5* (my old RH9 root partition). This one is inside the same extended partition (/dev/sda4) as /dev/sda6, and again, mounts without any problem.
I should add that, even when (as you can see on the output of fdisk) the /dev/sda6 partition is not bootable, I can use it normallly (eg, with my old Win98 OS) booting from a diskette, or, running from within RH9, mount it or use it with an old VMWare application.
So, any assistance will be appreciated.
Thanks in advance.

---


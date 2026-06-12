---
title: "Cloned USB drive with Lubuntu Eoan and Focal can be made persistent live"
date: 2019-09-12
forum: Ubuntu Development Version
---

### Post by sudodus on 2019-09-12
During several versions it is straightforward to create a live USB drive by cloning from an iso file with Ubuntu and Ubuntu flavours. But it has **not** been possible to make a cloned drive **persistent** by using the unallocated space behind the cloned part of the USB drive. At least, I don't know any way to make it work with 18.04 LTS and older versions.

Today I have tested a [method developed by F. Hauri which works for Debian 10](https://unix.stackexchange.com/questions/118965/how-to-create-a-debian-live-usb-with-persistence/538571), and I found that it works with Lubuntu Eoan. It is actually rather simple. I think and hope that it will work in the next LTS release, 20.04, not only with Lubuntu but with the whole family of Ubuntu and the flavours.

I used the following commands, where the real editing commands are high-lighted.

```

strings eoan-desktop-amd64.iso |grep 'quiet splash'  # check that 'quiet splash' is there to be replaced by 'persistent  ' (12 characters)
**sed 's/quiet splash/persistent  /' eoan-desktop-amd64.iso > persistent-eoan-desktop-amd64.iso**  # yes, sed works with binary files
ls -l *eoan*  # check that the size is the same
strings persistent-eoan-desktop-amd64.iso |grep 'persistent  '  # check that 'persistent' is there now
**dus persistent-eoan-desktop-amd64.iso**  # I use mkusb-dus, you can use the Ubuntu Startup Disk Creator or another cloning tool
sudo lsblk -fm  # It is important to check the device letter of the target drive (the USB drive, that you want persistent live
**sudo fdisk /dev/sdx**  # x is the device letter of the target drive, please double-check that you have the correct letter
**n**           # new partition
**p**           # primary
**<Return>**    # default: 3
**<Return>**    # default: next free sector
**<Return>**    # default: last addressable sector
**w**           # write and quit
sudo lsblk -fm  # check that things look good and verify that partition #3 is the correct partition to be used to store the persistent data
**sudo mkfs.ext2 -L casper-rw /dev/sdx3**  # put label and file system into the partition of persistence
sudo lsblk -fm  # check that things look good
**sync**  # flush the buffers and wait for prompt

```

After the sync command you can unplug the drive to test it in another computer or reboot to test it in the same computer.

**Edit1**: I added a screenshot from cloned drive running persistent live. The commands were recalled from .bash_history (and created in BIOS mode, while the system was running in UEFI mode at the screenshot).

**Edit2**: The task can be simplified: You need not create a partittion 'behind' the cloned part of the target drive. **It is enough the modify the iso file with sed and clone that modified iso file to the target drive**. When you boot into it, the Ubuntu system will create the partition for persistence and its file system *automatically* and it will be a persistent live drive.

There is a graphical user interface in the mkusb family of tools, [mkusb-plug](https://help.ubuntu.com/community/mkusb/plug), that takes advantage of this new feature of Ubuntu 19.10, 20.04 LTS and future versions of Ubuntu and the Ubuntu family flavours.

---

### Post by C.S.Cameron on 2019-09-13
I have been playing with 19.10 and persistent partitions and syslinux.
It is good to see they are working again.
I have started to write up some instructions but am hung up on easiest way to copy the existing casper-rw file to the new casper-rw partition:

**Add a Persistent Partition to a UNetbootin Live/Persistent USB, (Ubuntu 19.10+)**

No additional USB drive required.

- Back up the bootable drive, copy and preserve it's casper-rw file.

- Boot the USB drive "toram",  At the UNetbootin boot menu press the Tab key.

- Type a space then "toram" and hit enter.

Now the computer will boot toram (8GB max required for UNetbootin drive). You will be able to edit and overwrite the Live USB.

**We will add a persistent partition and a NTFS partition for data storage**.

- Open GParted, select the USB drive and unmount it.

- Shrink the FAT32 partition to a minimum.

- Add a new ext4 partition for persistence.

- Label the ext4 partition "casper-rw".

- In the remaining space create a NTFS partition.

- Apply all Operations.   

- Reboot in order to populate the casper-rw partition.

**Now we copy the existing casper-rw file to the new casper-rw persistent partition: **

Mount old casper-rw file:

```
sudo mkdir /media/casper

sudo mount -o loop /cdrom/casper-rw /media/casper/
```

Copy old casper-rw file contents to the new casper-rw partition.

```
sudo rsync -a /media/casper/ /media/cscameron/casper-rw/
```

- Reboot

**The original casper-rw file will become unused and can be deleted. **

Similar procedure should work for drives made using other bootdrive apps such as Rufus, a SDC drive can not be modified.

---

### Post by sudodus on 2019-09-13
> **C.S.Cameron said:**
> I have been playing with 19.10 and persistent partitions and syslinux.
It is good to see they are working again.

:-)
> 
I have started to write up some instructions but am hung up on easiest way to copy the existing casper-rw file to the new casper-rw partition:

I suggest that you back up the content on the file level with **rsync** or **tar** with superuser privileges (sudo) to see and preserve all files and their ownership and permissions. That way you will not backup free space and individual files will be available, not only the whole file system.
> 
Add a Persistent Partition to a UNetbootin Live/Persistent USB, (Ubuntu 19.10+)
...

Many people like Unetbootin, and they will be happy to make persistent live drives with a partition (or partitions) for persistence to get rid of the 4 GiB size limit of files in FAT32.

---

### Post by C.S.Cameron on 2019-09-13
Have you tried adding a persistent partition to a SDC install?
I don't think the ISO9660 FS is modifiable.

---

### Post by sudodus on 2019-09-14
The code chunk in the opening post shows all the steps (except downloading and md5sum-checking the iso file).

I used **mkusb-dus** in cloning mode. It creates an exact clone just like the **Ubuntu Startup Disk Creator**. So I would answer 'Yes'.

A. I modified the ISO file by 'binary edit' with **sed** taking care, that the size of the replacement was exactly the same size (12 bytes),

```

'quiet splash' --> 'persistent  '

```

and every other byte was copied. I created a modified iso file and cloned that file, because 

1. I wanted to check that the substitution was correct
2. I wanted to use the modified iso file more than once

It would have been possible to redirect the output of **sed** to the USB device directly.

B. Another crucial point is to create a partition 'behind' the cloned iso file. It did not work at all with **gparted**, and did not work to create a working system with **parted**. But [F. Hauri](https://unix.stackexchange.com/questions/118965/how-to-create-a-debian-live-usb-with-persistence/538571) showed that it works with **fdisk**. This way the partition table at the head end is 'correct enough' for the system for persistence to understand and use it.

---

### Post by oldfred on 2019-09-21
I have Ubuntu-Mate ISO.
So I extracted ISO for UEFI boot to the only flash drive I have available, 4GB and created small ext2 partition and NTFS partitions.
After extraction changed quiet splash to persistent.

      ```
 menuentry "Try Ubuntu MATE without installing" {

 set gfxpayload=keep
linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu-mate.seed persistent ---
initrd    /casper/initrd 
 }     
```

       cd ISO  # folder where I have all my ISOs
# zsynced to refresh ISO & extracted to partition on USB flash drive "LIVE"
 zsync [http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/eoan-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/eoan-desktop-amd64.iso.zsync)
sudo 7z x eoan-desktop-amd64Mate.iso -o/media/fred/LIVE 

  
Partitions on flash drive:
```
sdc                                                           
&#9500;&#9472;sdc1  vfat   LIVE      34E9-77B0                            /media/fred/LIVE
&#9500;&#9472;sdc2  ext2   casper-rw a255626a-7dce-4e8b-97ac-602673a1f392 /media/fred/casper
&#9492;&#9472;sdc3  ntfs   data      2849D14C70F09A70                     /media/fred/data 


```

Booted flash drive, ran Boot-Repair and it shows it saved into casper-rw partition.

---

### Post by sudodus on 2019-09-21
@oldfred,

Yes, your extraction method works well with persistence too :-)

---

### Post by oldfred on 2019-09-21
Saw somewhere that with newer Windows the extraction method does not work directly.
The Windows install file .win now exceeds 4GB, so cannot be in a FAT32 partition. You have to create both a FAT32 for UEFI boot and a NTFS for the rest of the install files. Not sure how UEFI file is configured to find NTFS partition with more files?

Ubuntu install files have not exceeded 4GB, so all fit nicely in one FAT32 partition.

I normally do not use installer on flash drive, nor just one version on a flash drive. So normally I would not need persistence. 

Most of my flash drives are now larger, so get full install and then can have ISO one another partition and loopmount them. And most test full installs are just from SSD or HDD to other drive in system or to a flash drive.

---

### Post by sudodus on 2019-09-22
> **oldfred said:**
> Saw somewhere that with newer Windows the extraction method does not work directly.
The Windows install file .win now exceeds 4GB, so cannot be in a FAT32 partition. You have to create both a FAT32 for UEFI boot and a NTFS for the rest of the install files. Not sure how UEFI file is configured to find NTFS partition with more files?

That's right. This is implemented in [WoeUSB](https://askubuntu.com/questions/1097560/woeusb-error-code-256-with-ntfs-formatted-usb/1098185#1098185), when running in text mode. And you can do it manually according to the following link,

[help.ubuntu.com/community/Installation/iso2usb/diy/windows-installer-for-big-files](https://help.ubuntu.com/community/Installation/iso2usb/diy/windows-installer-for-big-files)

-o-

Some UEFI systems can boot from NTFS, and the simple extraction method works directly (in UEFI mode, but you must fix the bootloader for BIOS mode). But many UEFI systems need FAT, an ESP partition with a FAT file system. I have [computers with] both kinds of UEFI systems and have verified what works.

-o-

But as you say, this is no problem with Ubuntu :-)

---

### Post by sudodus on 2019-09-24
This new feature alias removed bug in casper makes it much easier to create persistent live drives with a partition for persistence. It is already there in Debian 10 and we have tested it here in Ubuntu Eoan.

- So we will soon have it in Ubuntu 19.10

- It will take months (maybe years) until it will appear in Ubuntu 18.04.x LTS.

- We can expect to get it in Ubuntu 20.04 LTS.

[SIZE=4]Risk[/SIZE]

General tools may start prompting people into trying to create partitions for persistence with Ubuntu 18.04.x LTS. It will fail and people will get frustrated with a USB drive that does not work at all. **We should be prepared, and recognize when this happens.**

Rufus has released a version with this feature, and I have already seen a few cases at AskUbuntu, where this has happened.

- [Can't get Ubuntu 18.04 installed as dual boot on Dell Precision 7540](https://askubuntu.com/questions/1176277/cant-get-ubuntu-18-04-installed-as-dual-boot-on-dell-precision-7540)

- [USB persistence not working](https://askubuntu.com/questions/1175880/usb-persistence-not-working) with a discussion between me and @Akeo, the developer of Rufus

This is a typical output from a USB pendrive that does not boot with Ubuntu 18.04.x, when Rufus failed to make it work with a partition for persistence:

```

(initramfs) mount: mounting /cow on /root failed: invalid argument
overlay mount failed

```

Please remember that mkusb works as usual.

---

### Post by C.S.Cameron on 2019-09-25
Post 2 above updated.

---

### Post by sudodus on 2019-11-07
[SIZE=4]This simple cloning method can be ported to Windows[/SIZE]

Have a try with the simple way to make a persistent live drive in Windows according to the following links

[Win32DiskImager/iso2usb/persistent](https://wiki.ubuntu.com/Win32DiskImager/iso2usb/persistent)

[Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

[SIZE=3]Easier for Windows users to start using Ubuntu and the Ubuntu family flavours[/SIZE]

It has already been easy to use some of the well-known tools, for example Rufus, to create USB boot drives that are live-only.

Now there is a simple method in Windows, that works with Ubuntu 19.10 and Focal Fossa iso files. It can create **persistent live** drives for people who do not want Ubuntu to touch the internal drive, but want installed programs and saved files to persist past shutdown and reboot.

1. Use **HxD** to edit the iso file with a binary editor replace two cosmetic boot options 'quiet splash' with 'persistent ' (replace 12 characters with 12 characters)

2. Use **Win32 Disk Imager** to clone the edited iso file

The first time the cloned drive is booted, the Ubuntu system will create a casper-rw partition with an ext4 file system automatically. Simple and robust!

See the attached screenshots. There are more detailed descriptions at the links in the beginning of this post.

---

### Post by sudodus on 2019-11-16
Just a reminder:

- Standard [mkusb](https://help.ubuntu.com/community/mkusb) (mkusb-dus) is still working in and with all current versions of Ubuntu and Ubuntu family flavours including Focal Fossa. The [current versions](https://ubuntuforums.org/showthread.php?t=1958073&page=43&p=13905175#post13905175) (2019-11-16) are 12.3.7 in the stable PPA and 12.3.8 in the unstable PPA.

- The new [mkusb-minp](https://help.ubuntu.com/community/mkusb/minp) uses the method described and discussed in this thread - with a safety belt. It works with the version 19.10 and Focal Fossa.  

I am keeping an eye on Focal Fossa to make sure these tools continue to work at least as well as they are working now.

---

### Post by sudodus on 2020-06-28
The task can be simplified: You need not create a partittion 'behind' the cloned part of the target drive. It is enough the modify the iso file with **sed** and **clone** that modified iso file to the target drive. When you boot into it, the Ubuntu system will create the partition for persistence and its file system automatically and it will be a persistent live drive.

**mkusb-minp** described in earlier posts is forked to **mkusb-sedd**, and there is a graphical user interface, [**mkusb-plug**](https://help.ubuntu.com/community/mkusb/plug), that takes advantage of this new feature of Ubuntu 19.10, 20.04 LTS and future versions of Ubuntu and the Ubuntu family flavours.

---

### Post by sudodus on 2020-10-03
[SIZE=4]Tweak for Pop!OS[/SIZE]

The current version of **Pop!OS** is based on Ubuntu 20.04 LTS. **mkusb** can clone to make live (live-only) drives that boot both in UEFI and BIOS mode. But neither mkusb-dus nor mkusb-plug can create persistent live drives from this iso file. But it works after a minor tweak to modify the iso file.

```

sed 's/noprompt  ---/persistent --/' pop-os_20.04_amd64_intel_13.iso > persistent_pop-os_20.04_amd64_intel_13.iso

```

When mkusb-dus or mkusb-plug ***clones*** this modified file to a USB drive, a persistent live drive will be created.

Example with dus (select cloning)

```

dus persistent_pop-os_20.04_amd64_intel_13.iso

```

---


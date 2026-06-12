---
title: "Question about Whole Disk Encryption with Lubuntu 14.04 LTS"
date: 2016-02-20
forum: Ubuntu, Linux and OS Chat
---

### Post by wjbmd48 on 2016-02-20
Hi:

I'm reasonably familiar and happy with the LUKS WDE on install.  The only problem is that it's difficult to impossible to do a two-way clone using either clonezilla boot to lubuntu or with acronis on a windows platform on a fully encrypted system because of even small disk size differences.(Ie, clone the disk from A to B, then back again, as you might want to do so you can always restore a secure, clean initial install.)

With Windows/Truecrypt, this is much easier to do, since you can easily decrypt the disk, which makes the clone go much more smoothly.  

My question, then, is are there any WDEs for Lubuntu that can a) be done post-install, and b) can be reversed easily?

My version of Truecrypt (7.1a) doesn't do WDE (it will encrypt containers and non-system disks), and I don't think Veracrypt is ready for prime time (as in, I can't get it to work on my system after install). I've heard bruited about that there's a "Truecrypt 7.1a-2" that does WDE on Lubuntu, but can't seem to find a downloadable file.

Can anyone offer some advice?

Thanks,



Bill

---

### Post by Bucky Ball on 2016-02-21
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not related to ***Installations and Upgrades*** or technical support. That forum area concerns installing and upgrading the OS itself, not the apps in it. 

Good luck.

---

### Post by sudodus on 2016-02-21
Have you tried making a ***compressed image*** of the whole drive with ***Clonezilla***, and restoring it to a drive of the same size or larger? I think it should work for you also when encrypted.

An alternative is to run some backup program or shellscript while logged in and get an unencrypted backup of the directory trees you select. This kind of backup can be based on ***rsync***.

---

### Post by Bucky Ball on 2016-02-21
I don't know a lot about this, but [would dd be of use]("https://help.ubuntu.com/community/DriveImaging")? Bit for bit copy but may have issues with encrypted? :-k

Be aware dd is also known as 'disk destroyer'. Be very careful. It will do what you ask exactly without asking questions. If you ask it to wipe your /home partition with zeros it will do so immediately, no 'are you sure?'.

---

### Post by wjbmd48 on 2016-02-21
I'm not concerned about corrupting/destroying my system; I have multiple X40s, and I'm constantly reimaging/reinstalling, and my data are backed up more ways than I can count.

I have tried compressed backups of encrypted disks with clonezilla, no joy there. From what I gather, it's a dicey procedure, and I have in fact not gotten it to work, and backing up the unlocked disk image is more trouble than it's worth.

Being able to clone, *then* encrypt would be a minor convenience, but not much less trouble than simply doing a fresh install each time i wanted a shiny new secure system.

Again, thanks all, you guys are the best!

Bill

---

### Post by sudodus on 2016-02-21
OK, you have more experience of Clonezilla with encrypted disks than I. (I have used Clonezilla for years, but not with encrypted disks.) But I know that making a compressed cloned image with

```

sudo -s
dd if=/dev/sdx bs=4096 | gzip > dd-file.img.gz
sync
exit  # from superuser privileges
```

should definitely work (except if there are bad sectors on the drive).

Recovering with

```

sudo -s
< dd-file.img.gz zcat | dd of=/dev/sdy bs=4096
sync
exit  # from superuser privileges
```

or safer with

```
sudo -H mkusb dd-file.img.gz
```

should work directly if an MSDOS partition table, and should work after fixing with ***gdisk*** if a GUID partition table. (There are repair commands in gdisk's  'recovery & transformation' menu and 'experts' menu.)

-o-

The first command sequence 'writes only to a file', which should not be too risky. But ***it is very important to double-check that the drive letter y is correct for the target drive***, otherwise you might destroy the family pictures. So instead of the second command sequence, you can use [mkusb](https://help.ubuntu.com/community/mkusb) to wrap a safely belt around dd. It helps you to select the correct target drive.

[hr][/hr]
***Edit:*** I was too curious to stay away from testing if it worked for me in UEFI mode :-P

I grabbed a [COLOR="#cc0000"]60GB[/COLOR] SSD that had been used via USB 3, so it was not trimmed. I put it inside a laptop (as an internal SATA drive), installed a fresh Ubuntu Xenial system with  encrypted disk and made a compressed image (with dd|gzip). There was almost no compression. Zeroising (wiping) 'inside' by overwriting all unused space was not efficient. Then I wiped the whole drive (using mkusb), and after that installed a fresh Ubuntu Xenial system with  encrypted disk in UEFI mode. It was compressed rather well from 60GB to 6.3GiB (6.74GB) by dd|gzip,

```
$ ls -lh /media/usbdata/dd-file.img.gz 
-rw------- 1 sudodus sudodus 6,3G feb 22 05:19 /media/usbdata/dd-file.img.gz
```

I expanded this compressed Ubuntu Xenial system with mkusb into a [COLOR="#cc0000"]320GB[/COLOR] HDD and repaired with gdisk (to get a backup partition table at the tail end of the drive), and it works. I can login via the passphrase and password and run the system.

```
tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]sudo lsblk -fm[/COLOR]
[sudo] password for tester: 
NAME                    FSTYPE      LABEL UUID                                   MOUNTPOINT NAME                    SIZE OWNER GROUP MODE
sda                                                                                         sda                   298,1G root  disk  brw-rw----
&#9500;&#9472;sda1                  vfat              6567-A0CC                              /boot/efi  &#9500;&#9472;sda1                  512M root  disk  brw-rw----
&#9500;&#9472;sda2                  ext2              e243db09-f9bb-46f3-b403-217552ce5923   /boot      &#9500;&#9472;sda2                  244M root  disk  brw-rw----
&#9492;&#9472;sda3                  crypto_LUKS       cd0aab8d-d5fc-46d4-8dfc-fb6426da4e3e              &#9492;&#9472;sda3                 55,2G root  disk  brw-rw----
  &#9492;&#9472;sda3_crypt          LVM2_member       4N5N66-boVS-YeCH-bYrR-Sufm-0mxP-mo5K5t              &#9492;&#9472;sda3_crypt         55,2G root  disk  brw-rw----
    &#9500;&#9472;ubuntu--vg-root   ext4              92461b8b-1c26-45a8-9253-1612b2c47589   /              &#9500;&#9472;ubuntu--vg-root  51,3G root  disk  brw-rw----
    &#9492;&#9472;ubuntu--vg-swap_1 swap              39818eea-088c-4af1-af0d-98ea4244deb2   [SWAP]         &#9492;&#9472;ubuntu--vg-swap_1
                                                                                                                    3,9G root  disk  brw-rw----
sr0                                                                                         sr0                    1024M root  cdrom brw-rw----

tester@tester-SATELLITE-PRO-C850-19W:~$ [COLOR="#0000FF"]sudo parted -ls[/COLOR]
Model: ATA ST320LT007-9ZV14 (scsi)
Disk /dev/sda: [COLOR="#cc0000"]320GB[/COLOR]
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   794MB   256MB   ext2
 3      794MB   [COLOR="#cc0000"]60.0GB[/COLOR]  59.2GB


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 55.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  55.0GB  55.0GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 4169MB
Sector size (logical/physical): 512B/4096B320GB
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  4169MB  4169MB  linux-swap(v1)


Error: /dev/mapper/sda3_crypt: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/sda3_crypt: 59.2GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 


```

[hr][/hr]
It is probably easier to make a fresh installation. I think it is a better idea to use some kind of ***backup of your personal files*** instead of cloning or making a compressed image of the whole system, particularly with a system, that has been used for a while and does not compress well.

---

### Post by Bucky Ball on 2016-02-21
And you know more about dd than me. While I use it quite a bit, I follow instruction. I thought it would probably work which is why I suggested earlier. :D

Handy but deadly.

---


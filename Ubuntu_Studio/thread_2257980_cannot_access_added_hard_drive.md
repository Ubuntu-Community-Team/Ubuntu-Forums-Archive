---
title: "cannot access added hard drive"
date: 2014-12-23
forum: Ubuntu Studio
---

### Post by handysmurf on 2014-12-23
desktop works okay on the 30 gig HD, and can "see" the freshly added 80 gig, but cannot save anything to it.
jumper was installed, configuring drive as "slave".  ran gparted, and deleted partition.  created new partition, and formatted as "ext4".  And when "properties"/"premissions" are accessed, it shows owner as "root/root", and "read/write", but all choices are "greyed out"  don't know where the "about" (thing) is to display my system info.

---

### Post by Bashing-om on 2014-12-23
handysmurf; Hello ;

Does the system see the hard drive ? :
post back the outputs - Between code tags - of terminal commands:
```

sudo fdisk -lu
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

One can not access the hard drive until the file systems are mounted; how are you mounting this 2nd hard drive ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by handysmurf on 2014-12-24
```

spc@spc-KM400-8237:~$ sudo fdisk -lu

Disk /dev/sda: 37.3 GiB, 40060403712 bytes, 78242976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000015a7

Device     Boot    Start      End  Sectors  Size Id Type
/dev/sda1  *        2048 76212223 76210176 36.3G 83 Linux
/dev/sda2       76214270 78241791  2027522  990M  5 Extended
/dev/sda5       76214272 78241791  2027520  990M 82 Linux swap / Solaris

Disk /dev/sdb: 76.3 GiB, 81964302336 bytes, 160086528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000f1854

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdb1        2048 160086015 160083968 76.3G 83 Linux

Disk /dev/sdc: 29.5 GiB, 31625052160 bytes, 61767680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x1c50dd72

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1        8064 61767679 61759616 29.5G  c W95 FAT32 (LBA)


```
```

spc@spc-KM400-8237:~$ sudo blkid
/dev/sda1: UUID="c6eea86b-c591-4770-a0a1-ea0fde47c2a7" TYPE="ext4" PARTUUID="000015a7-01" 
/dev/sda5: UUID="827e3e69-fbaa-4e5a-be56-a26e51c1266d" TYPE="swap" PARTUUID="000015a7-05" 
/dev/sdb1: UUID="4a65a27f-8727-4f2d-903e-2655cfc572af" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="000f1854-01" 
/dev/sdc1: UUID="1C50-DD72" TYPE="vfat" PARTUUID="1c50dd72-01" 
spc@spc-KM400-8237:~$

```

---

### Post by oldfred on 2014-12-24
You probably just need to set ownership & permissions to give yourself permission to use it. 
And if a permanent not external drive you probably want it to automount when you reboot rather than have to click on it every time. When you manually mount or use Nautilus it will also default mount to /media/$USER/{UUID} or label. I do prefer to label all partitions and some that I only mount occassionly I know which is which and it mounts under a name I know than some very long UUID.

It looks like it is ext3 not ext4? That makes a difference on how you mount it.

If manually mouned at /mnt/data, change to your mount

 sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data

You can copy the template from this and just use your UUID.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by handysmurf on 2014-12-24
```

It looks like it is ext3 not ext4? That makes a difference on how you mount it.

```
Um, yeah, i reformatted it to ext3 after posting hoping that was the problem.

Contents of /etc/fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=c6eea86b-c591-4770-a0a1-ea0fde47c2a7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=827e3e69-fbaa-4e5a-be56-a26e51c1266d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

i'm still a noob...  that said, i'm lost on this template stuff, but if i read you right I would add this line to the end of /etc/fstab
```

"UUID=4a65a27f-8727-4f2d-903e-2655cfc572af /mnt/Data ext3 defaults,noatime 0 2"

```
can i instead substitute "LABEL=Data" for "UUID=4a65a27f-8727-4f2d-903e-2655cfc572af" which would be:
```

"LABEL=Data /mnt/Data ext3 defaults,noatime 0 2"

```
AND if that much is correct, do i also first create a directory named "Data" in /mnt/

---

### Post by oldfred on 2014-12-24
If you want to use label, then with gparted or with Disks add the label to the partition. And it must match exactly, so Data. (And no quotes around it in fstab).

I mount with UUID after making a mount point:
 sudo mkdir /mnt/data

When installing it was seen as sdc, but is sdb. Flash drive or DVD was seen as sdb when I installed.
# Entry for /dev/sdc4 :
UUID=a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data ext4 relatime 0 2

Shows labels, but it only is a convience that my label is the same as mount in this case. I could mount by label also. But I have had different labels than mounts and gotten very confused, espeically with label "Data" and mount "data" as they are totally different.
```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  vfat    EFI      /boot/efi      FD76-E33D
/dev/sda3  ext4    trusty   /              45de38c8-6748-4634-b207-628d9aa8b42b
/dev/sda4  swap             <swap>         7f429d54-b2e9-417a-ab13-b93af50f5159
/dev/sda5  ext4    iso_ssd  (not mounted)  695d18b5-16f8-4e9c-bf66-675a12da5a26
/dev/sdb1  vfat    efi      (not mounted)  68CD-3368
/dev/sdb3  ext4    myth     (not mounted)  8e9b2ec7-56d7-4691-8fcd-bec142445d90
/dev/sdb4  ext4    data     /mnt/data      a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5

```

---

### Post by handysmurf on 2014-12-25
it's all good now, the main problem was that the permissions were set to "root" which made it read-only,

the other thing was getting drive to "auto-mount" on desired path at boot which i finally got once i made the choice.  Both issues were addressed in #4 of this thread.
he first issue was fixed with :
```

sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data

```
And my second issue was fixed with info gleaned from this link, also in #4.  Naturally i had to customize the path to suit my choice 8-)
```

You can copy the template from this and just use your UUID.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

```

I mucked about attempting to use "$USER" in the path so anyone could use it, and had to scramble for a live CD to edit my added line in /etc/fstab, because it hung at the "splash screen".
scratched around in manuals for mount, and fstab, and could only just make sense of the info you guys gave me. I'da never figured this out on my own, with just "the book.
Many Thanks to you both Bashing-om, and oldfred, I much appreciate your time, and brainpower... oldfred sounds like "old friend" said with a severe head cold, gave me a laugh.

---

### Post by Bashing-om on 2014-12-25
handysmurf; Great !

Pleased ya got it all sorted out.

[INDENT]we are all somewhere on that learning curve
[INDENT][INDENT][INDENT][INDENT]it is all a process in learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---


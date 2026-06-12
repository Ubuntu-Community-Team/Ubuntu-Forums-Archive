---
title: "Can't acces second hard drive"
date: 2013-02-22
forum: Server Platforms
---

### Post by Dragnix on 2013-02-22
[I]Mod note :
Reference Thread : [http://ubuntuforums.org/showthread.php?t=1983273](http://ubuntuforums.org/showthread.php?t=1983273)
-----------------------------------------[/I]

I have exactly the same problem.
but i couldnt fix it.

fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/***server-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=135c6306-feac-41cd-95af-afe589e0194a /boot           ext2    defaults        0       2
/dev/mapper/***server-swap_1 none            swap    sw              0       0
/dev/sdf /mnt/2nd-hdd ext4 defaults 0 0
```
samba .conf
```
[global]
 
## Browsing/Identification 
###
# Change this to the workgroup/NT-domain name your Samba server will part of
 
workgroup = WORKGROUP
encrypt passwords = yes
wins support = yes

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home director as \\server\username
[homes]
comment = Home Directories
browseable = no
hide unreadable = yes
guest ok = no
read only = no

[Data]
comment = Data
path = /mnt/2nd-hdd
vlid users = nico
writable = yes
hide unreadable = yes
read only = no
browsable = yes
available = yes
writable = yes
public = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0770

```

I am able to access the server via puTTY so network seems okay
and i have no problem with acces the home folder with windows
```
****@***server:~$ sudo mount
/dev/mapper/***server-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdf on /data type ext3 (rw)
/dev/sda1 on /boot type ext2 (rw)
/dev/sdf on /mnt/2nd-hdd type ext3 (rw)
```

```

****@***server:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 koppen, 63 sectoren/spoor, 19457 cilinders, totaal 312581808 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x000ac216

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  uitgebreid
/dev/sda5          501760   312580095   156039168   83  Linux

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders, totaal 1953525168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 4096 bytes
in-/uitvoergrootte (minimaal/optimaal): 4096 bytes / 4096 bytes
Schijf-ID: 0xdc384dcd

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdf1            2048  1953520064   976759008+  83  Linux

Disk /dev/mapper/sda5_crypt: 159.8 GB, 159782010880 bytes
255 koppen, 63 sectoren/spoor, 19425 cilinders, totaal 312074240 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x00000000

Schijf /dev/mapper/sda5_crypt bevat geen geldige partitietabel

Disk /dev/mapper/***server-root: 159.3 GB, 159308054528 bytes
255 koppen, 63 sectoren/spoor, 19368 cilinders, totaal 311148544 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x00000000

Schijf /dev/mapper/***server-root bevat geen geldige partitietabel

Schijf /dev/mapper/***server-swap_1: 469 MB, 469762048 bytes
255 koppen, 63 sectoren/spoor, 57 cilinders, totaal 917504 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x00000000

Schijf /dev/mapper/***server-swap_1 bevat geen geldige partitietabel
nico@bosserver:~$
```

```
****@***server:~$ sudo ls -l /mnt
totaal 4
drwxrwx--- 3 root root 4096 feb 22 23:33 2nd-hdd

```

---

### Post by varunendra on 2013-02-25
Post moved to its own thread and posted for a bump!
--------------------------------

Welcome to the forums Dragnix :)

Please also post which version of Ubuntu server you are using.

---

### Post by volkswagner on 2013-02-26
As you can see your folder only has permissions granted to root.

```
****@***server:~$ sudo ls -l /mnt
totaal 4
drwxrwx--- 3 root root 4096 feb 22 23:33 2nd-hdd
```

To give proper advice we will need more info about how you would like to access/share this drive.

A simple setup would be to change owner:group to your user.
Unmount it first.
```
sudo umount /dev/sdf
```
Change owner and group.
Again, It would help if I new you had a certain group in mind.  If you have a group with members substitute your group name after username.  I will assume nico is your Linux username as well as samba username.
```
sudo chown nico:nico /mnt/2nd-hdd
```
Change permissions:
```
sudo chmod 775 /mnt/2nd-hdd
```

A couple errors I see.  You have the drive mounted, not the partition.  You need to change /etc/fstab to /dev/sdf1 not /dev/sdf.

You may also want to mount the drive with the user option.  
For you /etc/fstab line:
```
/dev/sdf1 /mnt/2nd-hdd ext4	rw,auto,user	0	0
```


You also have an error in your smb.conf.

```
vlid users = nico
```
should be:
```
valid users = nico
```

After making the above changes:
mount the partition.
```
sudo mount -a
```
Restart samba:
```
sudo service smbd restart
```

See if you can write to the mount as your regular user.

```
mkdir /mnt/2nd-hdd/test
```
```
ls -l /mnt/2nd-hdd
```

If the above gets you going, you may also consider using BLKID instead of /dev/sdf1 to mount the drive.  These /dev can change after a reboot, especially if you add/remove or change drives.

To find the BLKID:
```
sudo sudo blkid
```

You can then change /etc/fstab entry similar to your /boot mount point.  I believe the UUID needs to be capital letters.  Substitute your results from the blkid command without the quotes.

---

### Post by Dragnix on 2013-03-10
im stuck by the commando "sudo mount -a"  the command don't work

---

### Post by Dragnix on 2013-03-10
i'm using Ubuntu 12.04.2 LTS

---

### Post by darkod on 2013-03-10
Lets split it step by step a little. First lets address how you mount it. As mentioned, you would usually mount a partition, not the whole hdd. Post the output of:
```
sudo parted /dev/sdf print
sudo blkid
```

After that we can give more advice.

---

### Post by volkswagner on 2013-03-10
> **Dragnix said:**
> im stuck by the commando "sudo mount -a"  the command don't work


What error message do you get?

When the command is run successful you will be returned to the prompt with no additional output. You can verify the mount worked by issuing the mount command with no switches.
```
Mount
```

---

### Post by Dragnix on 2013-03-16
sudo parted /dev/sdf print > Model: ATA WDC WD10EARX-32N (scsi)
Schijf /dev/sdf: 1000GB
Sectorgrootte (logisch/fysiek): 512B/4096B
Partitietabel: msdos
Nummer  Begin   Einde   Grootte  Type     Bestandssysteem  Vlaggen
 1      1049kB  1000GB  1000GB   primary


sudo blkid > /dev/sde1: UUID="135c6306-feac-41cd-95af-afe589e0194a" TYPE="ext2"
/dev/sde5: UUID="67c38509-59fc-44e9-8a77-224344800675" TYPE="crypto_LUKS"
/dev/mapper/sda5_crypt: UUID="677Fi5-zEte-Awpl-G7mW-coVj-svNw-kg0krd" TYPE="LVM2_member"
/dev/mapper/Bosserver-root: UUID="e25d4b82-dbaa-4af7-823f-2d832a216c0c" TYPE="ext4"
/dev/mapper/Bosserver-swap_1: UUID="4dff7412-739e-44e1-be8e-acfabd3e604a" TYPE="swap"

---

### Post by Dragnix on 2013-03-16
When i put the command sudo mount -a > mount: onjuiste bestandssysteemsoort, ongeldige optie, ontbrekende codepagina,
       ontbrekend hulpprogramma, slecht superblok op /dev/sdf1, of een andere fout
       Soms staat er nuttige informatie in het systeemlog --
       probeer zoiets als:  dmesg | tail Sorry it's dutch version..

---

### Post by koenn on 2013-03-16
> ```
/dev/sdf /mnt/2nd-hdd ext4 defaults 0 0
```
that looks wrong and could be the reason mount -a doesn't work
you probably need to mount the partition, /dev/sdf1.

(the error you posted is a generic "I don't know how to mount this - maybe wrong fs type, maybe bad superblock, ... " complaint) 

there's similar rubbishj in the output of your mount command : 
```

/dev/sdf on /data type ext3 (rw)

/dev/sdf on /mnt/2nd-hdd type ext3 (rw)

```

---

### Post by darkod on 2013-03-16
Yes, you do need to mount the partition but that's not the only issue. Look at the parted output, you have no filesystem on sdf1. Next to primary partition type it doesn't say anything more, the filesystem column is empty.

This is a new disk and you still have no data on it, right?
If that is right, format it with:
```
sudo mkfs.ext4 /dev/sdf1
```

After that adjust fstab to mount /dev/sdf1 not /dev/sdf. And make sure the mount point you are trying to use exists first, if it doesn't you need to create it the first time you want to use it.

That should sort it out.

If you did have data on the disk, don't format it, it will destroy it. You will need to investigate why the filesystem is missing if it was formatted once and has data on it.

---


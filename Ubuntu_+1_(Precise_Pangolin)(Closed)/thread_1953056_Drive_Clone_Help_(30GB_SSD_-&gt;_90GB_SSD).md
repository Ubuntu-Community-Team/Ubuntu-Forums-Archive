---
title: "Drive Clone Help (30GB SSD -&gt; 90GB SSD)"
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Skyflyer4life on 2012-04-05
This doesn't exactly pertain to Ubuntu 12.04 Beta and isn't a pressing issue but I was looking for some expert help and thought I would ask around here.  I'm currently running 12.04 Beta 2 and was trying to swap out the 30 GB SSD drive for a 90 GB SSD drive and have not been successful over the past 2 days of working on it.  I've tried Clonezilla without success as well as dd commands.  I'm running into GPT issues I think and chrooted into the cloned distro on the new SSD to try to install grub2 but without success.  

This is my first attempt at cloning so bear with me.  My first question is that after the drive is cloned, the fstab is going to have the wrong UUID identifiers for the drive it is sitting on right?  I don't understand how that could work? From all my reading this has never come up so I'm probably barking up the wrong tree.  If anyone can help with some easy to follow instructions that would be awesome.  BTW.. I have one of those newer mobo with UEFI bios.

[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)

---

### Post by CharlesA on 2012-04-05
Why not just use clonezilla and do a disk-to-disk copy?

You may have to expand/enlarge the partition, but that should be fairly easy to do.

---

### Post by Skyflyer4life on 2012-04-05
Thanks Charles... I'm going to run Clonezilla again and see what happens.

---

### Post by rubylaser on 2012-04-05
Just 1 more idea to add to CharlesA's already good suggestions.  Normally, I'd use ddrescue to clone drives because it handles bad sectors better, and it seems a little faster than dd for me.  I'd just do it like this.

```
sudo apt-get install gddrescue
```

/dev/sda would be your 30GB SSD and /dev/sdb would be your 90GB SSD.
```
sudo ddrescue -v /dev/sda /dev/sdb
```

I'd run a filesystem check when it's done, and then use Gparted as CharlesA mentioned to grow the partitions to accomodate the new space.

---

### Post by CharlesA on 2012-04-05
Nice catch ruby. I didn't think about ddrescue. That might be due to me not using dd a whole lot though.

But yeah, +1 to disk check after cloning.

---

### Post by Skyflyer4life on 2012-04-05
Awesome... thanks so much for your help.  I'll give ddrescue a try if Clonezilla doesn't work.  Right now Clonezilla failed with the grub2/bootloader partition for some reason.  It should handle it no problem from what I've been reading so I'm now working on chrooting into the distro and rebuilding grub2.  I had this problem once before after and 12.04 update (which are in these forums somewhere) and ended up re-installing Ubuntu.  I'm hoping I can master Grub2 after this and never loose an install because of a grub issue!

---

### Post by Skyflyer4life on 2012-04-05
I've been working with boot-repair but am still having problems.  The  first link below I tried "Reinstall Grub" and the second I went back and  tried "Restore MBR".

When I start up Boot-Repair, it gives me a message "/boot detected.  Please check the options."  What does this mean?

I also get a message about a bios-boot flag and unformatted partition.  Does any of this make sense to anyone?

[http://paste.ubuntu.com/916491/](http://paste.ubuntu.com/916491/)

[http://paste.ubuntu.com/916509/](http://paste.ubuntu.com/916509/)

---

### Post by CharlesA on 2012-04-05
I've not heard of that happening. Clonezilla should not have messed with Grub at all.

---

### Post by Skyflyer4life on 2012-04-05
I tried it again.
[http://paste.ubuntu.com/916557/](http://paste.ubuntu.com/916557/)

When running Clonezilla, I got the following message.
"The boot loader on /dev/sdX is not grub, Skip running grub-install"  

I don't know if that is where the problem comes into play.

I'm really starting to hate UEFI and Grub.

---

### Post by CharlesA on 2012-04-05
Hrm. Does it do the same thing if you go into the advanced features of clonezilla and uncheck "reinstall grub" ?

[http://clonezilla.org/clonezilla-live/doc/03_Disk_to_disk_clone/advanced/05-advanced-param.php](http://clonezilla.org/clonezilla-live/doc/03_Disk_to_disk_clone/advanced/05-advanced-param.php)

I remember having to do that with a *nix box I imaged.

---

### Post by Skyflyer4life on 2012-04-05
Whoa... I just booted into the system using the cloned drive!  Strange and exciting.  When booting up now, I have the old Grub menu appear (v. 1.99-21ubuntu2) with different OS options (Ubuntu, Ubuntu (recover mode), and Previous Linux Versions).

I select Ubuntu where I get the message at loading screen.. 
"The disk drive for /boot/efi is not ready or not present.  Continue to wait, or Press S to skip mounting or M for manual recover"

if I press S it will boot me into ubuntu (on cloned 90 GB ssd drive)

---

### Post by CharlesA on 2012-04-05
Strange.

Can you post the contents of /etc/fstab

---

### Post by Gregory Lee on 2012-04-05
> **Skyflyer4life said:**
> My first question is that after the drive is cloned, the fstab is going to have the wrong UUID identifiers for the drive it is sitting on right?[]("http://ubuntuforums.org/showthread.php?t=1680929")
You don't have to use the UUIDs in fstab -- old style /dev/sda1 etc. are still understood.

---

### Post by CharlesA on 2012-04-05
> **Gregory Lee said:**
> You don't have to use the UUIDs in fstab -- old style /dev/sda1 etc. are still understood.
Well, if you clone the drive, the UUID doesn't change. ;)

---

### Post by Skyflyer4life on 2012-04-05
Here is the output from fstab.  Still having some boot up issues but at least I'm in and using Ubuntu right now.  Now if I could just tweak out Grub2.


```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=b7ec14fd-9b43-4420-b154-e0c66c40fb75 /               ext4    discard,noatime,errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=EA8B-B93B  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
# UUID=ab855bfc-4f0d-4661-b4d7-a52d09415db7 none            swap    sw              0       0
```

---

### Post by CharlesA on 2012-04-05
> **Skyflyer4life said:**
> Here is the output from fstab.  Still having some boot up issues but at least I'm in and using Ubuntu right now.  Now if I could just tweak out Grub2.


```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=b7ec14fd-9b43-4420-b154-e0c66c40fb75 /               ext4    discard,noatime,errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
**UUID=EA8B-B93B  /boot/efi       vfat    defaults        0       1**
# swap was on /dev/sda3 during installation
# UUID=ab855bfc-4f0d-4661-b4d7-a52d09415db7 none            swap    sw              0       0
```
Did you have anything else plugged in when you installed?

It would probably be a USB stick or some such thing since it's FAT.

In any case, just comment that line out of fstab by adding a # to the start of the bolded line.

It might have been a boot partition, but as vfat? I dunno.

---

### Post by oldfred on 2012-04-05
If you are using 12.04 why clone, a new install would avoid all these issues.

The fellow who wrote gdisk used to post here a lot and one time he mentioned that with gpt partitions you should not use dd.

One of your boot info scripts shows grub in the MBR but an efi partition. If booting with UEFI then boot script should show this in the efi partition:
/boot/efi/EFI/ubuntu/grubx64.efi

If booting with BIOS and gpt you need a bios_grub partition for grub to correctly install.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive.

You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02. Or with terminal:
sudo parted /dev/sda set <partition_number> bios_grub on

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

If you're using EFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS.

---

### Post by xyzzyman on 2012-04-05
I'm with oldfred. It's one thing if you were trying to migrate an old install, but an install from an alpha or beta might be better to just start with a fresh install (Especially as we're so close to final now), and just copy your home folder back in.

Seems like a nice fresh start for the LTS. :) You already would be done by now and out enjoying life instead of banging your head on your desk.

---


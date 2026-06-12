---
title: "attempting to set up dual boot fails: &quot;grub-install /dev/sdx failed&quot;?"
date: 2015-04-22
forum: System76 Support
---

### Post by sfinnie on 2015-04-22
Hello all.

Firstly, I realise this is for "System76 hardware installed with Ubuntu".  I have a System76 laptop (Galago Ultra pro) and it has Kubuntu 14.04 installed.  And I'm trying to dual boot with ElementaryOS Freya (0.3) which is an Ubuntu derivative.  So that's hopefully close enough...

Secondly, am sure this must be documented somewhere but afraid I couldn't find it.  Pointers appreciated if so.

I installed Elementary Freya (0.3) from live CD.  Re-partitioned the boot disk (240GB SSD - /dev/dsb.  Machine also has 512GB backup disk as /dev/sda).  Installation went fine until it tried to install boot loader, at which point it fails with "grub-install /dev/sda failed - this is a fatal error".  I tried selecting /dev/sdb but same result.

My Kubuntu installation continues to work on reboot (Kubuntu on /dev/sdb1) but doesn't present boot selection menu on starting - just boots straight into Kubuntu.

**So: what do I need to do to set up dual boot?**

Thanks.  Partition table below for reference.  ElementaryOS installed on /dev/sdb5.

 -S.
--
[TABLE="width: 500"]
[TR]
[TD][B]Partition
[/B][/TD]
[TD][B]Type
[/B][/TD]
[TD][B]Mount Point
[/B][/TD]
[TD][B]Label
[/B][/TD]
[TD][B]Size
[/B][/TD]
[/TR]
[TR]
[TD]/dev/sdb1
[/TD]
[TD]ext4
[/TD]
[TD]/
[/TD]
[TD]Ubuntu
[/TD]
[TD]56GiB
[/TD]
[/TR]
[TR]
[TD]/dev/sdb3
[/TD]
[TD]extended
[/TD]
[TD][/TD]
[TD][/TD]
[TD]164GiB
[/TD]
[/TR]
[TR]
[TD]    /dev/sdb5
[/TD]
[TD]ext4
[/TD]
[TD][/TD]
[TD][/TD]
[TD]164GiB
[/TD]
[/TR]
[TR]
[TD]/dev/sdb2
[/TD]
[TD]linuxswap
[/TD]
[TD][/TD]
[TD][/TD]
[TD]4GiB
[/TD]
[/TR]
[TR]
[TD]/dev/sda1
[/TD]
[TD]ext4
[/TD]
[TD][/TD]
[TD]Extra Drive 1
[/TD]
[TD]466GiB
[/TD]
[/TR]
[/TABLE]

---

### Post by Bashing-om on 2015-04-22
sfinnie; Hello;;

Not at all sure of what is not going on here.
Which system is to be that primary operating system, as only one can control the boot process ?

Please post back the outputs - between code tags, please - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
so we see the partitioning in a format that is recognizable .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then we see about (RE-)installing the boot code for the appropriate controlling authority.

[INDENT][INDENT]there can be only one - to a hard drive
[/INDENT][/INDENT]

---

### Post by sfinnie on 2015-04-23
Hi Bashing-om, thanks for the reply.  Output as follows:

```

scoot@Friday:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003250c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   117462578    58730265+  83  Linux
/dev/sdb2       460472320   468860927     4194304   82  Linux swap / Solaris
/dev/sdb3       117463038   460472319   171504641    5  Extended
/dev/sdb5   *   117463040   460472319   171504640   83  Linux

Partition table entries are not in disk order

```
-------------------------------------------------
```

scoot@Friday:~$ sudo parted -l

Model: ATA WDC WD5000LPVX-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name     Flags
 1      1049kB  500GB  500GB  ext4         primary


Model: ATA INTEL SSDMCEAW24 (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  60.1GB  60.1GB  primary   ext4
 3      60.1GB  236GB   176GB   extended
 5      60.1GB  236GB   176GB   logical   ext4            boot
 2      236GB   240GB   4295MB  primary   linux-swap(v1)

```

Right now I'm booted into Kubuntu (/dev/sdb1).  I would like to add Elementary (/dev/sdb5) as a dual boot option.

 -S.

Thanks for any help.

---

### Post by Bashing-om on 2015-04-23
sfinnie; Hey ... 

Looks good to me .
Edit: Boot flag set to sdb5 ! Maybe have to (RE-)install grub to sdb's MBR ? .. we can we can .

Boot kubuntu ( sdb1 ) as that primary controlling operating system.

Now run terminal command:
```

sudo update-grub

```

Does kubuntu pick up EOS and chainload it into kubuntu's boot menu ?

If so then we make it so that EOS can not preempt kubuntu's grub .

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-04-23
Grub will not install to your sda, unless you create a small 1 or 2MB unformatted partition anywhere on sda. If using gparted it needs the bios_grub flag, or if gdisk the code is ef02. That assigns the correct GUID for grub to use as a location for extra boot code that it needs on a gpt partitioned drive.

Often better once you start to change to gpt to convert all drives, but not required as long as you understand the differences.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by sfinnie on 2015-04-23
Hi Basing-om, result of update-grub as follows:

```

scoot@Friday:~$ sudo update-grub
[sudo] password for scoot: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
Found elementary OS Freya (0.3) on /dev/sdb5
done

```

So it looks like it was detected.  Also in grub.cfg:

```

scoot@Friday:~$ cat /boot/grub/grub.cfg | grep menuentry

        [...]
        menuentry 'elementary OS Freya (0.3) (on /dev/sdb5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--0e1422e2-db94-4a02-9200-8553f5fec640' {

```

which seems OK....?

---

### Post by sfinnie on 2015-04-23
Hi oldfred.  Thanks for the reply - but I'm afraid I don't understand the significance.  Do I need grub on sda?  sdb is the system disk, sda a data/backup drive.  And I assume grub is already on sdb since Kubuntu is booting from there (and update-grub runs per answer to Bashing-om).  Apologies if I'm missing/mis-understanding something...

---

### Post by Bashing-om on 2015-04-23
sfinnie; Maybe,

Rebooted and;
What now:
```

sudo parted -l

```
is the boot flag now set to sdb1 ?
When booting, you get kubuntu's grub boot menu, and in this menu is an option to boot elementary ?
When selecting elementary to boot  -> it does ?

IF yes to all the above, time to disable ' 30_os-prober ' in EOS .

[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by sfinnie on 2015-04-23
Hi Bashing-om,

```

scoot@Friday:~$ sudo parted -l
Model: ATA WDC WD5000LPVX-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name     Flags
 1      1049kB  500GB  500GB  ext4         primary


Model: ATA INTEL SSDMCEAW24 (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  60.1GB  60.1GB  primary   ext4
 3      60.1GB  236GB   176GB   extended
 5      60.1GB  236GB   176GB   logical   ext4            boot
 2      236GB   240GB   4295MB  primary   linux-swap(v1)

```

Boot flag hasn't changed - but I can now boot successfully into both EOS and Ubuntu.  Do I need to disable `30_os-prober`?  Seems to be working OK now, the only small change I'd like to make is for EOS to be the default.  I can live without that though.

---

### Post by oldfred on 2015-04-23
Grub does not use boot flag. Windows boot loaders do use boot flag.

But Windows has to have boot flag on a primary partition and a few BIOS must see a boot flag to even let grub boot. So we still suggest having a boot flag.

With multiple drives I usually install different grub versions to each MBR. And grub always defaults to install to sda, so your new installs will try to install to sda, but error out without the bios_grub partition. And letting other installs use sda is good, as then your working main install and its grub in sdb is not changed.

Unrelated you may want to house clean out some kernels. I normally keep one old one, and the newest. Once it gets to 3 or 4 then I houseclean.

       Check current kernel I also keep one older just in case:
#Current kernel:
uname -a

 I prefer synaptic and keeping 2 kernels, current and one known working older on.
 Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)


[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

   kernel house clean
[http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this](http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this)

---

### Post by Bashing-om on 2015-04-23
sfinnie; Well,

Well, a change in thought process then:
> 
 I'd like to make is for EOS to be the default. 


To make sure there are no ambiguity always a good thing to label partitions:
labelling your partitions makes things a lot easier > 
Not only do they display in terminal, they display as labelled in Ubuntu, which makes it a lot easier than perhaps displaying a UUID. 
Here is the command to label your partitions: 
```

sudo tune2fs -L "Trusty" /dev/sdb1 
sudo tune2fs -L "EOS" /dev/sdb5

```
the "name" between the quotes can be what ever description you choose.
same procedure for what is on 'sda1'.

OK .. back to making EOS the default>

As we had already ran update-grub from kubuntu .. now we need to wipe it out and set EOS.
Boot the EOS install medium to terminal:
Terminal commands:
```

sudo mount /dev/sdb5 /mnt
sudo grub-install --boot-directory=/mnt /dev/sdb
sudo umount /mnt

```

reset in bios to boot from sdb and boot into kubuntu (sdb1) .. and disable '30_os-prober':
```

sudo chmod -x /etc/grub.d/30_os-prober

``` As there can be but 1 controlling authority and we do not want it to be kubuntu.

Reboot now into EOS .. and set up EOS's grub.
```

sudo update-grub

```
Reboot to see the effect ->

Now all should be finer than a frog's hair

---

### Post by sfinnie on 2015-04-28
Delayed reply - sorry.  Typing this from eOS and all working fine - many thanks @Bashing-om and @oldfred.  In case anyone else is using this: I didn't go as far as setting up grub from eOS.  It's working fine using the Kubuntu grub installation, and I can live with having to select eOS from the boot menu on the odd time I reboot.  Thanks again for the help.

---

### Post by Bashing-om on 2015-04-28
sfinnie; Good 'nuff ;

As you are tickled, I am pink all over.

just keep on
[INDENT][INDENT][INDENT]keep'n on
[/INDENT][/INDENT][/INDENT]

---


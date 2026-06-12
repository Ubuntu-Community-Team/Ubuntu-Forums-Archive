---
title: "boot problem - GPT, BIOS, GPT, bios_grub, GRUB command line"
date: 2014-01-08
forum: Ubuntu Development Version
---

### Post by eris23 on 2014-01-08
ASUS P5N-D BIOS Revision 1401 motherboard
4TB drive, GPT with bios_grub partition

On install, and every kernel upgrade, the following stanza is created in grub.cfg -- but boots to grub command line:

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  72e05257-d053-4e56-b49f-064b28d63ba0
else
  search --no-floppy --fs-uuid --set=root 72e05257-d053-4e56-b49f-064b28d63ba0
fi
    font="/usr/share/grub/unicode.pf2"
fi

Oddly, the following WILL boot:

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  72e05257-d053-4e56-b49f-064b28d63ba0
else
  search --no-floppy --fs-uuid --set=root 72e05257-d053-4e56-b49f-064b28d63ba0
fi
    font="/usr/share/grub/unicode.pf2"
fi

The boot-repair CD, with default settings, also creates a non-booting system.

It's a GPT disk, why isn't GRUB recognizing GPT?  And why IS it recognizing non-existent msdos partition type?

System is currently Xubuntu trusty (same problem, though, with Saucy).

---

### Post by grahammechanical on 2014-01-08
There is just a little bit of misunderstanding here. This is the Grub naming convention and it applies not just to Trusty.

hdo = the first hard disk
hd1 = the second hard disk
and so on
msdos1 = the first partition
msdos2 = the second partition
and so on
So, hdo,msdos1 = the first partition on the first hard disk. That is all. It is the naming convention that the Grub developers have chosen. 

By the way, set root='hd0,gpt2' means the second partition on the first hard disk. Is "gpt2" a typing error or the reason for booting to a Grub command line. In one instance the boot parameters point to a hard disk UUID on the second partition and that configuration does not boot. And in the other instance the boot parameters point to a hard disk UUID on the first partition and that configuration does boot. 

It could just be a typing error. We can download a Grub manual from here.

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

I do not know why the OS boots when the partition scheme is listed as msdos and not gpt. Perhaps, it is a setting that works whether the partition scheme is msdos or gpt.

Regards.

---

### Post by eris23 on 2014-01-08
parted shows the following:

Model: ATA ST4000DM000-1F21 (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2097kB  1049kB                        bios_grub
 2      2097kB  3992GB  3992GB  ext4
 3      3992GB  4001GB  8587MB  linux-swap(v1)

The two grub.cfg entries in my first message were automatically generated.  The non-working one on the 4TB drive, the working one was copied from a functional install on a 1TB drive (with the GUID changed to match).

---

### Post by oldfred on 2014-01-08
There was an old bug where grub did on work correctly with very large over 500GB / (root) partitions. I still suggest smaller root partitions as then drive does not have to jump all over drive to boot.

I used gpt on a 160GB drive with 10.10. But back then they did not have any reference to gpt even thought it would work if you specified it with a insmod. And to boot Windows on a MBR drive you had to specify with insmod that it was MBR. There was not the newer (hd1,gpt1), it was always (hd1,1) type entries.

My current install of 12.04 on my SSD is gpt and it only has the gpt entries.

What version of grub and Ubuntu?

---

### Post by eris23 on 2014-01-08
Trusty, amd64, Xubuntu, grub-pc 2.00-22

---

### Post by oldfred on 2014-01-09
With trusty you cannot be sure if just an issue as it is still not even beta, but often it is the newest version.

I still would try a small 25GB / (root) partition.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by eris23 on 2014-01-15
Kernel/init.rd updated.  Wouldn't boot.  Tried copying above entry.  Wouldn't boot -- grub couldn't find partition.  Tried boot-repair cd.  Default repair -- but decided to add boot flag to root partition (though I know it's not recommended for gpt drives, with the exception of paricular intel boards).  Booted.

Following is relevant entry from grub.cfg:

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  72e05257-d053-4e56-b49f-064b28d63ba0
else
  search --no-floppy --fs-uuid --set=root 72e05257-d053-4e56-b49f-064b28d63ba0
fi
    font="/usr/share/grub/unicode.pf2"
fi

So, now the gpt entry works.

---


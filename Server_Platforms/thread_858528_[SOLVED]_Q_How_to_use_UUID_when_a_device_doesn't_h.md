---
title: "[SOLVED] Q: How to use UUID when a device doesn't have one?"
date: 2008-07-13
forum: Server Platforms
---

### Post by Krupski on 2008-07-13
[SIZE="5"]**[COLOR="Red"]SOLVED! See post #3[/COLOR]**[/SIZE]


Hi all,

I'm running Ubuntu server 8.04.1 64 bit in a homebuilt NAS box.

The system has Ubuntu server installed on a small compact flash card, 2GB for the OS and 2GB for swap (on a 4GB CF card). The storage is two 1TB hard drives configured as RAID-1 (mirror).

I've got a small script that I use to make an IMAGE backup of the CF card so that I can revert to a known-good setup if I make some major boo-boo.

Here's the script I use:

```

echo Saving OS image, please wait...
/bin/dd if=/dev/sdc of=/home/shared/ftp/linux/ubuntu/ubuntu-server-cf-bootdisk-snapshot-$(date +%d-%b-%Y-%H.%M).img bs=1M count=4096
echo Done!

```

It works fine... I can use Winimage (in Windoze) to copy the image back to the CF card if I need to.

Now here's the problem: The device names don't always stay the same. Sometimes the CF card is /dev/sda and sometimes it's /dev/sdc

Of course, the solution would seem to be simply use UUID instead... but the CF card itself doesn't HAVE a UUID!

The root and swap partitions do, but not the main device itself!

Here's a dump of "blkid | sort":

```

/dev/md0: LABEL="linux-storage" UUID="35ea8bc6-1cc3-4abb-8d86-23497ffe3b5e" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda: UUID="0ea78486-aaa3-87b3-1499-94a4a304f114" TYPE="mdraid"
/dev/sdb: UUID="0ea78486-aaa3-87b3-1499-94a4a304f114" TYPE="mdraid"
/dev/sdc1: LABEL="linux-root" UUID="9a364efd-0521-40ff-a76b-1005cdd8e41a" TYPE="ext3"
/dev/sdc2: TYPE="swap" UUID="070d44c8-e6a2-4e4f-933d-0f571830551a"

```

Note that (*this* time) the RAID drives are /dev/sda and /dev/sdb, and Linux is on /dev/sdc1 and 2. But, there's no UUID for /dev/sdc as a whole!

Is there any way to find or make or set a UUID or some other way to POSITIVELY identify the CF card so that my OS backup script ALWAYS works when Ubuntu plays name switch-er-oo?

Thanks in advance!

-- Roger

---

### Post by sisco311 on 2008-07-13
try something like:
> [FONT=monospace]
[/FONT]echo Saving OS image, please wait...[FONT=monospace]
[/FONT]/bin/dd if=/dev/disk/by-uuid/*UUID-OF-sd?1-HERE* of=/home/shared/ftp/linux/ubuntu/ubuntu-server-cf-bootdisk-snapshot-**1**-$(date +%d-%b-%Y-%H.%M).img bs=1M count=4096
/bin/dd if=/dev/disk/by-uuid/*UUID-OF-sd?2-HERE* of=/home/shared/ftp/linux/ubuntu/ubuntu-server-cf-bootdisk-snapshot-**2**-$(date +%d-%b-%Y-%H.%M).img bs=1M count=4096
echo Done!

---

### Post by Krupski on 2008-07-13
> **sisco311 said:**
> try something like:

Thanks... I tried it and it did what I expected... it saved the partitions... not the raw disk data (i.e. it didn't work).

However, I found the solution by accident!

I was doing "ls /dev/disk" and forgot to type "by-uuid" and I saw there were other options!

* by-id
* by-label
* by-path
* by-uuid


The line "ls /dev/disk/by-id | sort" yielded this:

```

**ata-Sony_NCFC4G_011910H0207P2150**
ata-Sony_NCFC4G_011910H0207P2150-part1
ata-Sony_NCFC4G_011910H0207P2150-part2
ata-WDC_WD10EACS-00D6B0_WD-WCAU40312948
ata-WDC_WD10EACS-00D6B0_WD-WCAU40433302
**edd-int13_dev80**
edd-int13_dev80-part1
edd-int13_dev80-part2
md-uuid-8684a70e:b387a3aa:a4949914:14f104a3
**scsi-1ATA_Sony_NCFC4G_011910H0207P2150**
scsi-1ATA_Sony_NCFC4G_011910H0207P2150-part1
scsi-1ATA_Sony_NCFC4G_011910H0207P2150-part2
scsi-1ATA_WDC_WD10EACS-00D6B0_WD-WCAU40312948
scsi-1ATA_WDC_WD10EACS-00D6B0_WD-WCAU40433302

```

Ah so now I'm thinking... maybe.... so I tried using this line in my script to describe the device:

"/dev/disk/by-id/**edd-int13_dev80**"

SUCCESS!!! Yippie!!

In fact, *any* of the ones which point to the CF card work:

* ata-Sony_NCFC4G_011910H0207P2150
* edd-int13_dev80
* scsi-1ATA_Sony_NCFC4G_011910H0207P2150

Of course the second line (edd-int13_dev80) is probably the best choice since it's generic whereas the other two lines (ata-Sony_NCFC4G_011910H0207P2150 and scsi-1ATA_Sony_NCFC4G_011910H0207P2150) specifically describe THAT PARTICULAR CF card and using them would fail if I installed a different CF card. The "edd-int13_dev80" line, however, will work with any device installed at that location.


So, my problem is solved... by accident!

Thanks!

-- Roger

(edit to add):

This alternate naming also works in fstab and grub's "menu.lst".

Here's an example (from my NAS box - fstab):

```

# /etc/fstab: static file system information.
#
# <file system>                         <mount point>   <type>  <options>       <dump>  <fsck>

# /dev/sda1
/dev/disk/by-id/**edd-int13_dev80-part1**   /               ext3    relatime,errors=remount-ro  0  1

# proc filesystem
proc                                    /proc           proc    defaults        0       0

# /dev/sda2
/dev/disk/by-id/**edd-int13_dev80-part2**   none            swap    sw              0       0

# RAID 1 storage drive
/dev/md0                                /home/shared    ext3    defaults        0       2

```

...and menu.lst:


```

title           Ubuntu 8.04.1, kernel 2.6.24-19-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-server root=/dev/disk/by-id/**edd-int13_dev80-part1** ro
initrd          /boot/initrd.img-2.6.24-19-server

title           Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-server root=/dev/disk/by-id/**edd-int13_dev80-part1** ro single
initrd          /boot/initrd.img-2.6.24-19-server

title           Ubuntu 8.04.1, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin

```


So much fun to learn new things! =D>

---

### Post by VapourDoc on 2008-08-14
Thanks for documenting your set-up and your fix.  I plan to set up CF-based NAS later this fall, and this gives me a good idea of how you did it.

You might want to mark this as SOLVED in your thread title so that others can take advantage of your solution (sisco311 has a link on how to do it in his footer).

Again, thanks.  :)

---

### Post by Krupski on 2008-08-14
> **VapourDoc said:**
> Thanks for documenting your set-up and your fix.  I plan to set up CF-based NAS later this fall, and this gives me a good idea of how you did it.

You might want to mark this as SOLVED in your thread title so that others can take advantage of your solution (sisco311 has a link on how to do it in his footer).

Again, thanks.  :)

Thanks. I didn't know how to mark posts as solved when I posted this one. It's marked now.

BTW, FYI a 4GB CF card is plenty large enough for a NAS box... 2 gigs for Linux and 2 gigs for swap space.

Linux takes up around 600MB of the 2GB partition... and swap is barely used.

Check out this little goodie: [[COLOR="Red"]**LINK**[/COLOR]]("http://www.addonics.com/products/flash_memory_reader/adebidecf.asp")

It's a small card that plugs directly into an IDE/ATAPI 40 pin connector on a motherboard. A CF card plugs into it and looks just like a bootable IDE drive to the system.

Once you have Server installed on the CF card, you can use 'dd' to back it up or Winimage in Windows to backup / restore it.

It's handy to have the OS on compact flash because you can make a "snapshot" of it any time you wish (and before you make any changes). If you make a mistake, no re-install is necessary... just copy a "last known good image" back to the card and you're back in business in 5 minutes!

Good luck!

-- Roger

---


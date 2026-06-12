---
title: "Question about RAID1 and updates"
date: 2020-01-07
forum: Server Platforms
---

### Post by Hex on 2020-01-07
Hey, guys,

I recently installed 18.04 with RAID1, with each drive having a separate boot partition (non-raided). As I understand, I have to copy the active boot partition (especially after update) using dd to the redundant one, so if I either drive fails, I can safely boot the system.

During the last kernel update however, I was puzzled. I updated the kernel, saw some messages about boot being updated, so I decided that it's time to clone this partition to the other drive. I did "mount | grep boot", got "/dev/**sdb1** on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)" and decided that I have to copy /dev/sdb1 to /dev/sda1. Just to be sure that everything was fine with the update, I rebooted the server and when I double checked with "mount | grep boot", I got "/dev/**sda1** on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)".

So it booted from the other drive? I'm really puzzled here as what to do?

"uname -r" shows the latest kernel update, which is "4.15.0-74-generic".

Any help is much appreciated! :)

---

### Post by slickymaster on 2020-01-07
Thread moved to **Server Platforms** for a better fit

---

### Post by SeijiSensei on 2020-01-07
I suggest using UUIDs instead of /dev/sd* references in /etc/fstab. You can see the UUIDs for each partition by running "sudo blkid".  You don't need the quotation marks for the entries in /etc/fstab. For instance, the entry for my /boot partition looks like this:
```
UUID=67ffaea8-3829-4682-ba69-35e843355c0a /boot   ext2    defaults   0  2
```

---

### Post by Hex on 2020-01-07
The /boot/efi entry in fstab uses UUID, it was set during installation. I thought UUID and /dev/sdx are linked - why would it change from sdb1 to sda1 over a reboot?

---

### Post by SeijiSensei on 2020-01-07
/dev/sdX designations depend on things like which drive is connected to which SATA port. They are not permanently linked to UUIDs. That's why UUIDs are preferred since they remain fixed no matter how the drives are connected or the order in which they are started.

Try swapping the SATA cables and see if /dev/sdb becomes /dev/sda and vice versa.

---

### Post by Hex on 2020-01-07
I've tried switching in BIOS and they change. However, I did no such thing when I rebooted after the kernel update, and they changed on their own, which is what is confusing. I don't know why this happens and which boot partition was updated and which was not.

---

### Post by darkod on 2020-01-07
If your board supports it I recommend to consider switching to legacy (MBR) boot. Linux supports using disks with either GPT or msdos (MBR) partition tables, and legacy boot. But some boards insist on using EFI boot when GPT disks are used.

If your boot supports legacy that's way better for mdadm. The reason is that the boot files are on all disks and you don't have to worry about the EFI system partition and what will happen if that disk fails.

---

### Post by TheFu on 2020-01-07
> **Hex said:**
> I've tried switching in BIOS and they change. However, I did no such thing when I rebooted after the kernel update, and they changed on their own, which is what is confusing. I don't know why this happens and which boot partition was updated and which was not.

The order that disk devices are found by the kernel can change due to race conditions.  It has been this way since around 2003, which is why UUIDs were created.  You don't need to use UUIDs if you don't want to, there are other options, but using /dev/sdA-Z .... **is** a dangerous practice.  You can use LABELs (assuming you manually ensure the partition labels are unique) or PATHs (a controller-->port--> disk --> partition neomenclature) ... look under /dev/disk/by*  to see the other options. These become symbolic links to the current sdA-Z devices during device discovery for each boot.

---

### Post by Hex on 2020-01-07
So what you are saying is that in a RAID1 system, with a UUID in fstab for /boot, the boot partition may show either as sda1 or sdb2, depending on race conditions, but it will always actually be the same physical drive?

---

### Post by TheFu on 2020-01-07
> **Hex said:**
> So what you are saying is that in a RAID1 system, with a UUID in fstab for /boot, the boot partition may show either as sda1 or sdb2, depending on race conditions, but it will always actually be the same physical drive?

No. That is not what I'm saying.  I'm saying that the sda or sdb or sdc or sdd can change based on race conditions at boot time. You cannot trust those devices directly.  Use UUIDs.  The problem with cloning a boot drive like I think you might is that the UUID could be identical on both, which breaks that method regardless of the /dev/sd[A-Z] order found.  I know that 100% cloned disks have the same UUIDs.  I don't know if cloned partitions do or not, but I wouldn't risk it.

YMMV.

---

### Post by Hex on 2020-01-08
Hmmm... Then is there a way to check which boot partition was updated by the system and which was not? E.g. newer files or something like that?

---

### Post by darkod on 2020-01-08
You're wasting too much time on this IMHO.

1. Go back and read my post #7 in case you missed it. That is the best way forward with raid.

2. You don't need to do so many complex checks to know which EFI partition is used. When doing kernel updates, after that run lsblk which will show which partition is mounted at /boot/efi currently. So that is the partition with newest files (if you wanna call it like that). And you need to use cp or rsync (but NOT dd) to copy the files from that partition to the other one.

---

### Post by Hex on 2020-01-08
I've somehow missed your post, sorry. I think I can only boot with EFI, the RAID drives were missing when I enabled EFI + Legacy, as far as I remember.

blkid shows:

/dev/sda1: UUID="1478-3B05" TYPE="vfat" PARTUUID="4d46c7f4-a415-420b-9c0f-b74273aba245"
/dev/sdb1: UUID="1478-3B05" TYPE="vfat" PARTUUID="9817f059-d900-4820-bf09-c4b40de48207"

lsblk shows:

sda1    8:1    0   1.9G  0 part  /boot/efi
sdb1    8:17   0   1.9G  0 part

However, as I mentioned, the system had sdb1 mounted as /boot during the kernel update and sda1 after I rebooted.

Why would you suggest against dd? Because it copies the same UUID? I see that there is a PARTUUID, which, despite using dd once already, after the initial installation, show different values for both drives. My knowledge here is lacking...

---

### Post by TheFu on 2020-01-08
> **Hex said:**
> I've somehow missed your post, sorry. I think I can only boot with EFI, the RAID drives were missing when I enabled EFI + Legacy, as far as I remember.

blkid shows:

/dev/sda1: UUID="1478-3B05" TYPE="vfat" PARTUUID="4d46c7f4-a415-420b-9c0f-b74273aba245"
/dev/sdb1: UUID="1478-3B05" TYPE="vfat" PARTUUID="9817f059-d900-4820-bf09-c4b40de48207"

lsblk shows:

sda1    8:1    0   1.9G  0 part  /boot/efi
sdb1    8:17   0   1.9G  0 part

However, as I mentioned, the system had sdb1 mounted as /boot during the kernel update and sda1 after I rebooted.

Why would you suggest against dd? Because it copies the same UUID? I see that there is a PARTUUID, which, despite using dd once already, after the initial installation, show different values for both drives. My knowledge here is lacking...

How this early mounting stuff works has been drastically changed since the systemd team took over.  They have a habit of ignoring the older methods and sometimes their changes seem arbitrary, break things that have always worked some other way previously.  In short, from systemd version to systemd version, all this code can change without being documented.  That team is known for creating "aspirational" documentation, for where they are headed, no how it actually works today.  Some of the stuff they do **is** brilliant, but I find I get burned more than necessary.

YMMV.

---

### Post by darkod on 2020-01-08
> **Hex said:**
> However, as I mentioned, the system had sdb1 mounted as /boot during the kernel update and sda1 after I rebooted.

This is the important part. Do not reboot after the update, not needed.

Run the update, check immediately with lsblk which partition is mounted at /boot/efi, mount the other one at temporary mount point, and copy the files from /boot/efi to the temp mount. That should do it (although I'm no expert on EFI boot).

---

### Post by Hex on 2020-01-08
Sounds logical, but why copy and not dd?

---


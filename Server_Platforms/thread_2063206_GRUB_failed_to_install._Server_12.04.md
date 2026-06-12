---
title: "GRUB failed to install. Server 12.04"
date: 2012-09-26
forum: Server Platforms
---

### Post by MG2R on 2012-09-26
I'm the proud owner of a DIY home server (pics: [https://plus.google.com/photos/114774128950272893084/albums/5687622317703943905](https://plus.google.com/photos/114774128950272893084/albums/5687622317703943905)). It has been running 24/7 for the last 1.5 years (approx.). Now, I added a third 2TB XDC green drive to it and wanted to install server 12.04 instead of 10.04. To do this, I decided to perform a complete clean install because the server had a lot of junk on it from 1.5 years of trying stuff out without having a clue about what I'm doing (yes, that's how I learn about computers).

The system consists of following storage media:

[LIST]
[*]SATA1: WDC green 2TB
[*]SATA2: WDC green 2TB
[*]SATA3: (new) WDC green 2TB
[*]SATA4: 32 GB SSD (OS)
[/LIST]
SATA1 and SATA2 were combined in a RAID1 config us mdadm in 10.04.
When I try to install 12.04, everything goes well up until the point where I need to install GRUB to the MBR of my 32GB SSD. That step always fails for no apparant reason. I tried burning a new disk, creating a new partition table instead of just simple formatting the existing OS partition, installing GRUP by starting from the CD and performing 'sudo grub-install'.


I'm running out of ideas here and need my server up and running so I can access my data. 

Any help? :)

---

### Post by darkod on 2012-09-26
The SSD has msdos or gpt table? If it's gpt it needs another small partition without any filesystem and with the bios_grub flag on it so that grub2 can install there. It doesn't fit on the MBR of gpt disks.

---

### Post by oldfred on 2012-09-26
If it is BIOS and gpt then it needs the bios_grub partition as Darko says.

But if a very new system it may have UEFI boot and then you need an efi partition.

UEFI systems offer both efi or BIOS boot. And how you set UEFI/BIOS and how you install Ubuntu may determine whether efi or BIOS booting.

---

### Post by MG2R on 2012-09-27
Thanks, how would I go about detecting what partition table the SSD has? And how would I create te bios/efi_grub partition if necessary?

---

### Post by darkod on 2012-09-27
The easiest way I use about tables, is parted.

```
sudo parted -l (small L)
```

That will show disk model, size, total number of sectors, table type, and below all partitions and filesystems on them.

---

### Post by MG2R on 2012-09-27
Okay, it says I have an msdos partittion table on the SSD, so it should be able to install GRUB, right? Still, it always fails :/

---

### Post by darkod on 2012-09-27
Have you tried letting it finish the install without grub2, and then try to add it using chroot-ing into the root partition?

If you need the procedure we can provide it, just tell us whether you have separate /boot partition or not, because it makes a difference. Also tell us which partition is root on /dev/sda (and which one is /boot if it exists).

---

### Post by MG2R on 2012-09-27
> **darkod said:**
> Have you tried letting it finish the install without grub2, and then try to add it using chroot-ing into the root partition?

If you need the procedure we can provide it, just tell us whether you have separate /boot partition or not, because it makes a difference. Also tell us which partition is root on /dev/sda (and which one is /boot if it exists).

I have tried a grub-install with the rescue disk before (if that's what you meant). Right now, I don't have a /boot partition and my root is in /dev/sdc1, which is ext4.

---

### Post by darkod on 2012-09-27
No, a grub-install won't really do it because if it didn't install grub2 at all, core.img and config files will be missing in /boot/grub.
The grub-install usually only adds small piece of code on the MBR. But if the other files are missing, that's worthless.

Another thing, which doesn't matter much: Since this is a new install, why didn't you reorder your disks so that the OS disk is /dev/sda? The letters get assigned according to the SATA ports, so sda will need to be in the first port (usually smallest number like SATA_0).

Anyway, you will need a live cd of any version so that you can boot the live mode, open terminal and do the chroot procedure.

Prepare the chroot first:
```
sudo mount /dev/sdc1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are like inside the installation on sdc1 and not in live mode any more. Remove completely grub2 of any remains, install new and create the config files. Also, install it on the MBR of /dev/sdc:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
grub-install /dev/sdc
update-grub
```

Exit chroot and unmount all:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart without the cd and if it worked, it should boot OK.

---

### Post by MG2R on 2012-10-01
> **darkod said:**
> No, a grub-install won't really do it because if it didn't install grub2 at all, core.img and config files will be missing in /boot/grub.
The grub-install usually only adds small piece of code on the MBR. But if the other files are missing, that's worthless.

Ok, I wanted to start the procedure and decided the best way to begin was to reinstall everything again (just because I like installing linux so much *cough*). During the install I noticed that the GRUB installation by default happens on the FIRST hard disk, which isn't the one I want it to be on. So I selected the right drive (my SSD) and GRUB installed without any issues!

It does fail to boot, still... I get the choice of what kernel to boot (regular/recovery mode/memtest...), but after that nothing but a black screen. No OS loading :/ I'm going to check the boot parameters now, but I'm not an expert whatsoever.

Thank you so much for the tutorial, bu the way! You're way to helpful!

---------
EDIT: I was able to boot into the recovery mode (getting a shell that says (initramfs)). The are a bunch of files in /boot/grub, including core.img...
---------
EDIT EDIT: It turns out the system hanged during boot because of a degraded raid system... Have been able to boot! Yay!

Again, thank you all for helping and thinking with me!

---


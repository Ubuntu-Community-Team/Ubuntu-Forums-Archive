---
title: "Adding network driver to LiveCD initrd.gz (Dell r210ii with 10.04.2)"
date: 2011-09-13
forum: Server Platforms
---

### Post by Jonathan L on 2011-09-13
Hello All

I am building a network with servers running 10.04.2 server (conventionally installed from CD-ROM) and a number of clients running 10.04.2 desktop -- running the LiveCD delivered over PXE diskless boot.  The general environment is well tested, the PXE, DHCP, TFTP, NFS and so on all work perfectly, and it all works perfectly on several different hardware platforms.  The network is isolated and has no connection at all to the internet.

My difficulty is that the real hardware -- brand new Dell R210ii servers -- has the Broadcom NetXTreme II Gigabit network card (two of them, built-in). I've been having difficulty in modifying the Casper initrd.gz to put the drivers in the right place.

I added these files (These file paths are within the initrd.gz file):
```
/lib/modules/2.6.32-28-generic/kernel/drivers/net/bnx2.ko
/lib/firmware/2.6.32-28-generic/bnx2/bnx2-mips-09-5.0.0.j3.fw
/lib/firmware/2.6.32-28-generic/bnx2/bnx2-rv2p-09-5.0.0.j3.fw
```and rebuilt the initrd.gz file and can manually load it (from busybox prompt once the boot fails with no root filesystem) with
```
insmod /lib/modules/2.6.32-28-generic/kernel/drivers/net/bnx2.ko
```Presently I've managed to bodge it and added the insmod to /scripts/casper, just above the ipconfig inside function do_netmount().  


**The question is how to do it properly: what do I do to get the normal boot to realise it needs to load the bnx2.ko file?**

Just to be clear about the network booting, the pxeboot config has the following:

```
LABEL debug
  MENU LABEL debug
  KERNEL debug/vmlinuz
  APPEND initrd=debug/initrd.gz root=/dev/nfs boot=casper netboot=nfs nfsroot=19
2.168.1.32:/exports/ubuntu-10.04.2-desktop-i386 --
```
[LIST]
[*]The exported directory /exports/ubuntu-10.04.2-desktop-i386 is a loopback mount of the normal CD-ROM image: ubuntu-10.04.2-desktop-i386.iso
[*] debug/vmlinuz is a copy of the one on the CD-ROM /casper/vmlinuz
[*] debug/initrd.gz was a copy of CD-ROM /casper/initrd.lz but decompressed and recompressed with gzip -9 (because pxeboot can't decompress .lz files)
[*]I unpacked and repacked this initrd.gz to add the bnx2 files (the .ko and two .fw files) and my horrible bodge to /scripts/casper
[*]The bnx2 files were found on the CD-ROM inside the filesystem /casper/filesystem.squashfs
[/LIST]
  To make changes to the initrd.gz, I unpack and repack it with
```
cd /var/lib/tftpboot/debug
mkdir new
cd new
zcat ../initrd.gz | cpio -i
edit or add files
find . | cpio --dereference -o -H newc | gzip -9 > ../initrd.gz
```Just to repeat: everything works fine with different hardware.  I just need to know where to add my bnx2.ko file so it gets loaded automatically.

Two days so far!

My thanks for any help.  Happy to do experiments or add detail if asked.

Jonathan.

---

### Post by Jonathan L on 2011-09-14
Hi All

In brief, the solution is depmod, which appears to make the appropriate indexing to tell the kernel to find the appropriate ethernet driver.  This solution is probably only really important for diskless booting, as you need your drivers before your filesystems are live, but is also the key to making any changes to a bootable Live CD image for use over PXE.  It took me three days to find the proper solution, so I thought I'd write it down in some detail for others.

PROBLEM

Diskless booting the Live CD image over PXE with unsupoorted ethernet card.  The hardware is brand new Dell R210ii server with Broadcom NetXTreme II ether card, which isn't supported for the PXE boot; but the drivers are on the CD.

ERROR MESSAGE

It manifests as a competely different problem, which actually should get trapped much earlier and more simply as a missing ether driver.

Boot over PXE and after the PXEBOOT menu you get messages scrolling past (assuming no splash screen)  The repeated error message says:
```
NFS over TCP not available from 192.168.1.32
```whcih will send you off checking your file server and perhaps (like me) trying to find out if it's really doing NFS over TCP not UDP. 

The earliest error message says
```
ipconfig: eth0: SIOCGIFINDEX: No such device
ipconfig: /tmp/net-eth0.conf: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
```This simply means you've got no ether cards and so you'll get no NFS.  This is the root cause.  The system could do the first phase of PXE booting because that code is in the firmware of the ethernet cards themselves.

It's difficult to catch the right message on the console as there's not much scrollback.

DRIVER

You may have to do some work to find the right driver.  In my case, with Dell R210ii servers, I have ones with installed hard disks and could simply find out the drivers
```
# dmesg | fgrep -i -C3 ether
[    5.304565] vga16fb: initializing
[    5.304568] vga16fb: mapped to 0xc00a0000
[    5.304613] fb0: VGA16 VGA frame buffer device
[    5.331478] Broadcom NetXtreme II Gigabit Ethernet Driver bnx2 v2.0.2 (Aug 21, 2009)
[    5.331502] bnx2 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.331511] bnx2 0000:01:00.0: setting latency timer to 64
[    5.331697] bnx2 0000:01:00.0: firmware: requesting bnx2/bnx2-mips-09-5.0.0.j3.fw
```FIX

In any case [B]the fix is to add the driver module, and its firmware files, and then rebuild the index with depmod.
[/B] 

It's fiddly because the files are all inside various filesystems-within-files.  Because of this, I thought I'd put the detail which might save someone some considerable time

We have a copy of the ubuntu CD-ROM image file:
```
# md5sum /cdroms/ubuntu-10.04.2-desktop-i386.iso
477350cbea8936c63d587cf2be69181b  /cdroms/ubuntu-10.04.2-desktop-i386.iso
```We're going to mount this CD-ROM image as an NFS export (normally done in /etc/fstab in real life):
```
mkdir /exports/ubuntu-10.04.2-desktop-i386
mount -o loop /cdroms/ubuntu-10.04.2-desktop-i386.iso /exports/ubuntu-10.04.2-desktop-i386
exportfs -a
```The Live CD real filesystem is a squashfs file: it's got the drivers we want, so we'll mount it temporarily (don't forget to umount it later)
```
mount -o loop /exports/ubuntu-10.04.2-desktop-i386/casper/filesystem.squashfs /mnt

```Now we'll make the new initrd image, which is the filesystem used by initramfs in the very beginning, and is the one which doesn't have the ether driver we need

We'll make a directory to hold our new filesystem
```
mkdir /tmp/newroot
cd /tmp/newroot
```Unpack the existing one
```
lzcat -S .lz /exports/ubuntu-10.04.2-desktop-i386/casper/initrd.lz | cpio -i
```Now add the drivers we want
```
cp -R /mnt/lib/firmware/2.6.32-28-generic/bnx2 lib/firmware/2.6.32-28-generic
cp /mnt/lib/modules/2.6.32-28-generic/kernel/drivers/net/bnx2.ko lib/modules/2.6.32-28-generic/kernel/drivers/net
```Now rebuild the index: this was the missing step I didn't know about
```
depmod -b `pwd` 2.6.32-28-generic
```Now rebuild the filesystem and compress with gzip as required by PXEBOOT
```
find . | cpio --dereference -o -H newc | gzip -9 > ../initrd.gz

```Now make the TFTP area for this, with the generic kernel and the new filesystem we just made
```
mkdir /var/lib/tftpboot/yippee
cp /exports/ubuntu-10.04.2-desktop-i386/casper/vmlinuz /var/lib/tftpboot/yippee
cp /tmp/initrd.gz /var/lib/tftpboot/yippee

```For completeness, this is an entire /var/lib/tftpboot/pxeboot.cfg/default file
```
DEFAULT vesamenu.c32
MENU TITLE Network boot
LABEL yippee
  MENU LABEL Yippee
  KERNEL yippee/vmlinuz
  APPEND initrd=yippee/initrd.gz root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.1.32:/exports/ubuntu-10.04.2-desktop-i386 --
```There is still an error coming from ipconfig, but that's apparently a bug in the casper script which won't matter to us.

TEST

When you boot, it no longer gets stuck in a loop trying to mount the NFS, and continues with boot.

Hope somehow this helps someone else.

All best,
Jonathan.

---

### Post by Entilza on 2011-09-14
Can't you use mkinitramfs to make a new initrd with your new driver?

---

### Post by Jonathan L on 2011-09-14
Hi

Thanks for your suggestion:

> **Entilza said:**
> Can't you use mkinitramfs to make a new initrd with your new driver?

I'm quite sure you can and I'm quite sure that's the proper way: but the manual for mkinitramfs is rather unclear about what it makes the image from, and it's a rather complex script which would seem to introduce a lot of depencies which were unnecessary for the task at hand.  But if you know the exact invocation for this problem that would be great.

The general reason for using CD-ROM images and booting from the network and so on is to reduce the ways in which the system can change, for audit purposes.

Thanks,
Jonathan.

---

### Post by Maxim Samoilenko on 2012-06-14
Thanks a lot for detailed and comprehensive description. I had the same issue with my R610. And got stuck as the same point as you, looking for the proper way of doing things. 

mkinitramfs creates initrd from scratch, w/o any casper-specific stuff, so I doubt it will work without manual intervention anyways.

---


---
title: "Copy server, to another machine (testing)"
date: 2009-03-18
forum: Server Platforms
---

### Post by ethos84 on 2009-03-18
Hi guys

I have a live intranet server running ubuntu 8.10 server. My goal is to be able to install this on a test machine for any changes (before changing on the live server).

I've tried ping:

[http://ping.windowsdream.com/]("http://ping.windowsdream.com/")

But well... it doesn't seem to work.

Any ideas / recommendations? The live server needs to be left as it is, so the "solution" would need to suite this.

Thanks

---

### Post by albandy on 2009-03-18
An example:

boot with the ubuntu cd
mkdir /mnt/sda1
put an USB hard disk, it should be mounted in something like /media/disk
mount the server linux partition
sudo mount /dev/sda1 /mnt/sda1
cd /mnt/sda1
sudo tar zcvfp /media/disk/serverbackup.tgz ./

now go to the test machine
boot the cd
insert the usb drive
mount the test machine linux partition
untar the file:
cd /mnt/sda1
sudo tar zxvf /media/disk/serverbackup.tgz
umount all partitions
reboot with the rescue cd
and regenerate grub

---

### Post by ethos84 on 2009-03-18
Hmm, well technically all the files are on the new hdd but it says "non system disk".

I've tried booting up into the live cd and sudo "dpkg-reconfigure grub" but no luck.

---

### Post by albandy on 2009-03-18
you need to reinstall grub in the mbr

boot with the rescue cd
mount the disk as /
then
grub-install /dev/sda --recheck

---

### Post by wkulecz on 2009-03-18
I clone live systems pretty often.

I use a USB to Hard drive adaptor, format and partition the hard drive to be compatible with the system being cloned (easiest if just one partition)
and then mount the USB drive.

I then clone the live system with:
rsync -ax / /media/wherever/the/USB/drive/mounts.

So far, ignoring the .gvfs errors from rsync during the copy, I haven't noticed any issues on the cloned systems.

I find the "Super Grub Boot CD" (Goggle it) to be the best way to boot the clone drive once installed in the target test system.

Overall I find this is significantly faster than the tar and untar operations.

--wally.

---


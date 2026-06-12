---
title: "Install files from onboard cdrom, dvdrom onto server."
date: 2011-03-27
forum: Server Platforms
---

### Post by jramshu on 2011-03-27
I hope this is the proper place to post this. I set up an Ubuntu 10.10 server at home. It has LAMP and openssh. Instead of using sftp or similar to put files on the server I want to just drop the disk in the drive and put them on it that way. The problems I am running in to are,  mount: can't find dvd1 in /etc/fstab or /etc/mtab. I almost got it to work by editing the fstab and trying to add the dvd1 to it. I did get it to read the folders on the disk, but cant see the files in the folders. I'm not sure I am adding the drive to fstab correctly. 

jimmy@server1:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: WDC WD400EB-11CP
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 06.0
       serial: WD-WMAAT4835674
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0000eff7
  *-cdrom:0
       description: CD-R/CD-RW writer
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw
       configuration: status=nodisc
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM SD-M1612
       vendor: Compaq
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1C10
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc

As you can see below the drives aren't listed in fstab.

jimmy@server1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fd3a7b56-739c-4ee4-acee-32851c35b593 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f7b36fbe-37fe-4d08-95c5-ac392aaf747f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


I put this in fstab.

/dev/dvd1  /media/dvd1 udf,iso9660 user,noauto,exec,utf8 0 0

Then I did this:
sudo mkdir /media/dvd1

That got it to read the disk, but I couldn't get to the contents in the folders on the disk. I tried it with different names, such as "cdrom1" and all the others listed for the drive. I have searched for hours on how to accomplish this and couldn't find anything to help me understand what I am doing wrong. So forgive me if I didn't dig deep enough in the forums.
I'm not sure I edited fstab correctly and wound up just taking all of it back off, the fstab edit and removed the dvd1 directory. Any advice would be appreciated.

---

### Post by jramshu on 2011-03-27
Ok. Now I feel kinda ignorant. Instead of looking at the man pages I looked to the Internet first. Can someone please tell me if this is close to being correct.

```
/dev/cdrom      /media/cdrom    auto    rw,user,noauto,exec,utf8 0       0

```I already had a dir named /media/cdrom, duh.

After I added the line to fstab, well with some trial and error with the options, I was able to gain access to the files. Now I just have to go in and put the dvd rom in there.

I would just like to know if this is actually the right way to do it.

Thanks and sorry for seeming to waste yalls time.:(

---


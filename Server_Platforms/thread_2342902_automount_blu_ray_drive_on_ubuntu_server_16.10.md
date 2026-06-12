---
title: "automount blu ray drive on ubuntu server 16.10"
date: 2016-11-11
forum: Server Platforms
---

### Post by steo86 on 2016-11-11
Hello,

I am trying to build a udev rule to mount my blu ray drive automatically if I will insert a disc on my fresh installed "Ubuntu Server 16.10 amd64".
I have done the following

```
sudo mkdir /media/cdrom
```
```
sudo nano /etc/udev/rules.d/90-mountcd.rules
```

```
SUBSYSTEM=="block", ACTION=="change", RUN+="/bin/mount /dev/sr0 -o ro /media/cdrom"
```

```
sudo udevadm control --reload
```

The udev rule is running as I can see in the syslog but I will get an error code 32.

```
Nov  9 14:03:55 testhcp kernel: [  378.854787] VFS: busy inodes on changed media or resized disk sr0
Nov  9 14:04:17 testhcp kernel: [  401.175678] VFS: busy inodes on changed media or resized disk sr0
Nov  9 14:05:28 testhcp kernel: [  471.884735] VFS: busy inodes on changed media or resized disk sr0
Nov  9 14:05:28 testhcp systemd-udevd[2924]: Process '/bin/mount /dev/sr0 -o ro /media/cdrom' failed with exit code 32.
Nov  9 14:05:48 testhcp kernel: [  492.311870] VFS: busy inodes on changed media or resized disk sr0
```

If I will run the mount command manually on the console the drive will get succesfully mount.
The same problem I will have with auto mounting usb drives.
I have installe usbmount and edit the usbmout.conf afterwareds.
```

FILESYSTEMS="vfat ext2 ext3 ext4 hfsplus ntfs ntfs-3g reiserfs"
```

the usb drive will not get mounted and in the syslog I will see this error:

```
Nov  9 14:24:19 testhtpc kernel: [   69.828655] scsi 7:0:0:0: Direct-Access     Kingston DTR30G2          PMAP PQ: 0 ANSI: 6
Nov  9 14:24:19 testhtpc kernel: [   69.829533] sd 7:0:0:0: Attached scsi generic sg3 type 0
Nov  9 14:24:20 testhtpc kernel: [   71.143397] sd 7:0:0:0: [sdc] 122880000 512-byte logical blocks: (62.9 GB/58.6 GiB)
Nov  9 14:24:20 testhtpc kernel: [   71.145441] sd 7:0:0:0: [sdc] Write Protect is off
Nov  9 14:24:20 testhtpc kernel: [   71.145448] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00
Nov  9 14:24:20 testhtpc kernel: [   71.147448] sd 7:0:0:0: [sdc] No Caching mode page found
Nov  9 14:24:20 testhtpc kernel: [   71.147528] sd 7:0:0:0: [sdc] Assuming drive cache: write through
Nov  9 14:24:20 testhtpc kernel: [   71.180967]  sdc: sdc1
Nov  9 14:24:20 testhtpc kernel: [   71.187105] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Nov  9 14:24:22 testhtpc usbmount[2701]: loaded usbmount configurations
Nov  9 14:24:22 testhtpc usbmount[2701]: trying to acquire lock /var/run/usbmount/.mount.lock
Nov  9 14:24:22 testhtpc usbmount[2701]: acquired lock /var/run/usbmount/.mount.lock
Nov  9 14:24:22 testhtpc usbmount[2701]: /dev/sdc does not contain a filesystem or disklabel
Nov  9 14:24:22 testhtpc systemd-udevd[2696]: Process '/usr/share/usbmount/usbmount add' failed with exit code 1.
Nov  9 14:24:22 testhtpc systemd[1]: Starting Stop ureadahead data collection...
Nov  9 14:24:22 testhtpc systemd[1]: Started Stop ureadahead data collection.
Nov  9 14:24:22 testhtpc usbmount[2730]: loaded usbmount configurations
Nov  9 14:24:22 testhtpc usbmount[2730]: trying to acquire lock /var/run/usbmount/.mount.lock
Nov  9 14:24:22 testhtpc usbmount[2730]: acquired lock /var/run/usbmount/.mount.lock
Nov  9 14:24:22 testhtpc usbmount[2730]: /dev/sdc1 contains filesystem type ext4
Nov  9 14:24:22 testhtpc usbmount[2730]: mountpoint /media/usb0 is available for /dev/sdc1
Nov  9 14:24:22 testhtpc usbmount[2730]: executing command: mount -text4 -osync,noexec,nodev,noatime,nodiratime /dev/sdc1 /media/usb0
Nov  9 14:24:23 testhtpc kernel: [   74.047371] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
Nov  9 14:24:23 testhtpc usbmount[2730]: executing command: run-parts /etc/usbmount/mount.d
Nov  9 14:24:23 testhtpc usbmount[2730]: usbmount execution finished
steffen@testhtpc:~$ ls -l /media/usb0
insgesamt 0
```

does anyone have an idea?

---

### Post by jmayoralas on 2016-11-12
> **steo86 said:**
> Hello,
The same problem I will have with auto mounting usb drives.
I have installe usbmount and edit the usbmout.conf afterwareds.
```

FILESYSTEMS="vfat ext2 ext3 ext4 hfsplus ntfs ntfs-3g reiserfs"
```

the usb drive will not get mounted and in the syslog I will see this error:

```
Nov  9 14:24:19 testhtpc kernel: [   69.828655] scsi 7:0:0:0: Direct-Access     Kingston DTR30G2          PMAP PQ: 0 ANSI: 6
...
Nov  9 14:24:22 testhtpc usbmount[2701]: /dev/sdc does not contain a filesystem or disklabel
Nov  9 14:24:22 testhtpc systemd-udevd[2696]: Process '/usr/share/usbmount/usbmount add' failed with exit code 1.
...

steffen@testhtpc:~$ ls -l /media/usb0
insgesamt 0
```

does anyone have an idea?

I don't know the solution, but I'm facing exactly the same problem with usbmount. I get the very same error messages in syslog and works like a charm when mounting from command line.

Same Ubuntu installation.

---

### Post by steo86 on 2016-11-16
No one got usbmount with ubuntu 16.10 working?

---

### Post by coffeecat on 2016-11-17
Not a Multimedia Software question.

*Thread moved to **Server Platforms**.*

I've also edited the thread title to help attract attention.

---

### Post by steo86 on 2016-11-19
I now got away from using usbmount because it doesnt seem to work. I now have added the following lines to "/etc/fstab" to make the automount for my usb and bluray-

> /dev/sdc1   /media/usb0     auto     nofail,auto,x-systemd.automount,x-systemd.device-timeout=2     0 2
/dev/sdd1   /media/usb1     auto     nofail,auto,x-systemd.automount,x-systemd.device-timeout=2    0 2
/dev/sr0    /media/bluray   udf,iso9660     auto,exec,utf8,nofail,x-systemd.automount,x-systemd.device-timeout=2     0 2

In generall this works fine with one small problem.
I have to access the mount points with for example "ls -l" or use "mount -a" first from terminal to trigger the automount over the fstab.
But I don´t want to connect to console first before using the devices on my media center application "kodi".
Is there any way to force fstab if a device is inserted to directly mount it and not wait for a file access to the mount point?

---

### Post by cariboo on 2016-11-19
Do you have automount installed? It is part of the autofs package.

---

### Post by steo86 on 2016-11-20
No is it ubuntu package?
How can I install it?
sudo apt-get install automount?

---

### Post by darkod on 2016-11-20
The answer is contained in the post -> package name = autofs. Try:
```
sudo apt-get install autofs
```

FYI, you can search for ubuntu package names here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---


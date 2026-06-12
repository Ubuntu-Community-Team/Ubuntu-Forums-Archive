---
title: "USB drive: problems mounting"
date: 2006-04-01
forum: Server Platforms
---

### Post by onaquest on 2006-04-01
Just upgraded from SuSE to Ubuntu server.
For some reason, I cannot mount my backup USB drive any longer (I actually managed to do it once or twice right after the install).

Here's what I see in /var/log/messages when I turn on the drive:

```

Mar 31 23:18:16 localhost kernel: [4295656.599000] usb 5-2: USB disconnect, address 6
Mar 31 23:18:21 localhost kernel: [4295661.765000] usb 5-2: new high speed USB device using ehci_hcd and address 7
Mar 31 23:18:22 localhost kernel: [4295661.978000] scsi6 : SCSI emulation for USB Mass Storage devices
Mar 31 23:18:22 localhost usb.agent[6438]:      usb-storage: already loaded
Mar 31 23:18:31 localhost kernel: [4295670.945000]   Vendor: USB-HS    Model: WDC WD2500BB-14G  Rev: 0.01
Mar 31 23:18:31 localhost kernel: [4295670.945000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Mar 31 23:18:31 localhost kernel: [4295670.978000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Mar 31 23:18:31 localhost kernel: [4295670.998000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
Mar 31 23:18:31 localhost kernel: [4295670.999000]  /dev/scsi/host6/bus0/target0/lun0: p1 p2
Mar 31 23:18:31 localhost kernel: [4295671.045000] Attached scsi disk sdc at scsi6, channel 0, id 0, lun 0
Mar 31 23:18:41 localhost scsi.agent[6475]: Attribute /sys/devices/pci0000:00/0000:00:10.4/usb5/5-2/5-2:1.0/host6/target6:0:0/6:0:0:0/type does not exist
```

Then:

```
#mount -t ext3 /dev/sdc2 /mnt/usblin/
mount: special device /dev/sdc2 does not exist
```

The USB drive is listed in /proc/scsi (that's the WDC - first one is a SATA):

```

# more /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Maxtor 7Y250M0   Rev: YAR5
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi6 Channel: 00 Id: 00 Lun: 00
  Vendor: USB-HS   Model: WDC WD2500BB-14G Rev: 0.01
  Type:   Direct-Access                    ANSI SCSI revision: 02

```
```

# more /proc/scsi/usb-storage/6
   Host scsi6: usb-storage
       Vendor: BUFFALO INC.
      Product: USB2-IDE Bridge
Serial Number: 00000701080B
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:

```

But:

```

# ls /dev/s*
/dev/sda  /dev/sda1

```

And fdisk doesn't seem to see it:

```

# fdisk -l

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4678    37576003+  83  Linux
/dev/hdb2            4679        4865     1502077+   5  Extended
/dev/hdb5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        1246    10008463+  83  Linux
/dev/hdc2            1247        1371     1004062+  82  Linux swap / Solaris
/dev/hdc3            1372        3239    15004710   83  Linux
/dev/hdc4            3240       30401   218178765    5  Extended
/dev/hdc5            3240       30401   218178733+  83  Linux

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30514   245103673+  83  Linux

```

Just in case, I did a:
```

update-usbids

```

No change.

Interestingly:

```

# lsusb
Unknown line at line 5924
Unknown line at line 5925
Unknown line at line 5926
Unknown line at line 5927
Unknown line at line 5928
Unknown line at line 5929
Unknown line at line 5930
Unknown line at line 5931
Unknown line at line 5932
Unknown line at line 5933
Unknown line at line 5934
Unknown line at line 5935
Bus 005 Device 007: ID 0411:002a MelCo., Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 04e8:324c Samsung Electronics Co., Ltd ML-1740 Printer
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

Now I'm lost... :-k Any idea/suggestion on what I'm doing wrong here?
Thanks in advance,

---

### Post by Scunizi on 2006-04-01
I have FINALLY found the solution to this problem. It seems to come up quite a bit.  It was really quite easy after I learned a little about how the file system work and how the system mounts things. You have to remember, the system needs a place holder/directory for each device that is mounted. That is accomplished in the media directory. Also everything you type below is case/CASE sensitive. I have 2 internal SATA drives and 1 IDE internal. I also wanted to be able to plug in my 3 USB devices and have them recognized with icons displayed on the Desktop. The 3 devices are... 1gig usb stick, 256m usb stick, 1 256m mp3 player (creative rhomba). I had to do a little editing of the fstab and media directory in order to get everything working correctly. In my case I already had sda1, sdb1,2,3,5, and hda1. The numbers in sdb represent different partitions.

1> Go to the consol and type sudo gedit /etc/fstab (enter) - This will open up your editor. It will ask for your password after the enter.

2> In fstab I added these three lines
/dev/sdc1 /media/usb1 vfat rw,user,fmask=0111,dmask=0000 0 0
/dev/sdd1 /media/usb2 vfat rw,user,fmask=0111,dmask=0000 0 0
/dev/sde1 /media/usb3 vfat rw,user,fmask=0111,dmask=0000 0 0

Now click save at the top of the screen.

If you have multiple partitions on one drive and that drive is labeled sdc, then you would add lines after sdc1 to include sdc2 sdc3 etc.  You get the picture.

The vfat referance above is for Fat32 formatted devices. Anything other than that and you'll have to change the formatting designator and possibly the fmask. dmask=0000 simply means that any user of the system can read and write to the device. If I remember correctly, if you substitute 0000 with 1000 only the logged user who created all this will be able to use the device. Someone may correct me here if I'm wrong. I'm humble.

You'll notice all my usb referances are sdc sdd sde because I already have 2 SATA drives in the machine that are labeled sda & sdb respectively (the numbers represent the different partitions on the harddrives) I you don't have any SATA drives then you should designate sda, sdb, sdc respectively. I made three seperate entries in case I plug in all three devices at the same time otherwise it won't make any differance.


3> Go back to your consol and click "File" "Open Tab". You'll now see two tabs at the top of the consol. Click the second one and you should have an active prompt like "mgarrow@ubuntu:/$". Type cd /media (enter). This will take you to the media folder/directory.
4> Now type
sudo mkdir usb1 (enter) (maybe enter password)
sudo mkdir usb2 (enter) (maybe enter password)
sudo mkdir usb3 (enter) (maybe enter password)
These lines give a place for the drives/devices to attach to. You can use other names if you want. I just did it this way for simpicity.

Now you're done! Restart your machine then plug in one of your usb devices. I may take a moment but the system should recoginze it, mount it and place an icon for it on the Desktop...

I'm about 3 weeks into learning this system from a cold start and really learning to love it between my bouts of frustration with my ignorance. Happy Ubuntu-ing!!!

---

### Post by onaquest on 2006-04-02
Scunizi - thanks for the reply. I'm afraid this isn't the issue here. I have all the mount points created. Actually I have managed to mount this drive in the past, shortly after the install. Just to be double sure, I recreated the mount points under /media and updated fstab.

Still no go. ](*,) 

```

# ls -l /media
total 20
drwxr-xr-x  2 root root 4096 2006-03-25 00:34 cdrecorder
lrwxrwxrwx  1 root root    6 2006-03-24 13:59 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2006-03-24 13:59 cdrom0
drwxr-xr-x  2 root root 4096 2006-03-24 13:59 cdrom1
drwxr-xr-x  2 root root 4096 2006-04-01 21:56 usblin
drwxr-xr-x  2 root root 4096 2006-04-01 21:57 usbwin

#cat /etc/fstab | grep -i usblin
/dev/sdc2               /media/usblin     ext3            noatime                                                    0 0

#mount /media/usblin
mount: special device /dev/sdc2 does not exist

# dmesg | tail -10
[4295661.997000] usb-storage: waiting for device to settle before scanning
[4295670.945000]   Vendor: USB-HS    Model: WDC WD2500BB-14G  Rev: 0.01
[4295670.945000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4295670.978000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[4295670.978000] sdc: assuming drive cache: write through
[4295670.998000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[4295670.998000] sdc: assuming drive cache: write through
[4295670.999000]  /dev/scsi/host6/bus0/target0/lun0: p1 p2
[4295671.045000] Attached scsi disk sdc at scsi6, channel 0, id 0, lun 0
[4295671.065000] usb-storage: device scan complete

```

BTW, running Ubuntu server and no graphical environment. 

Thanks.

---


---
title: "Cant do anything with thumbdrive after crashed WoeUSB flashing"
date: 2019-01-24
forum: Windows
---

### Post by janeharrell on 2019-01-24
Backstory
I wanted to install Windows 10 on one of my PCs. Since that  pc has no optical drives i opted to installing from usb (i had done  that a few years back with windows 7 on the same pc).
So I downloaded the october release iso of windows 10 directly from microsoft.com and flashed it onto the drive using WoeUSB.

What happened
WoeUSB  did it's thing, eventually crashing at the boot loader installation.  Since it wouldn't respond anymore (not even after waiting 6 hours!), i  rebooted the pc.
Ever since then, all reads and writes to the drive fail.

Hardware info
The thumbdrive is this: [https://lupus-imaging-media.de/en/agfaphoto-usb-flash-drive-3-0/](https://lupus-imaging-media.de/en/agfaphoto-usb-flash-drive-3-0/)
Quick specs: USB3.0, 16GB, no write protection switch
Drive is new (~2 weeks), used it max. 5x during its lifespan

What I tried

- gparted
Shows drive as "unallocated space". Trying to format it results in an error saying i need to create a partition table.
Attempting  to create a partition table (tried all options) always freezes gparted  indefinitely. This behaviour is consistent between my laptops (kali,  ubuntu 18.04) and my workstation (fedora29).

- gnome-disks utility
Since  everything but "format" is grayed-out, i tried that. Attempting to  format it to anything results in "Error wiping device: Failed to probe  the device '/dev/sdc' (udisks-error-quark, 0)".

At this point i figured i needed more low-level tools, so first of all i checked lsusb, which looks fine to me

```

lsusb -s 001:006 -v


Bus 002 Device 004: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         9
  idVendor           0x090c Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.)
  idProduct          0x1000 Flash Drive
  bcdDevice           10.00
  iManufacturer           1 
  iProduct                2 USB DISK
  iSerial                 3 17070307007117
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           44
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              126mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst               8
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst               8
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           22
  bNumDeviceCaps          2
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000006
      Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x000c
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   2
      Lowest fully-functional device speed is High Speed (480Mbps)
    bU1DevExitLat           4 micro seconds
    bU2DevExitLat           4 micro seconds
Device Status:     0x000c
  (Bus Powered)
  U1 Enabled
  U2 Enabled

```

However, fdisk -l does not recognize the drive.

Next i tried testdisk (which does recognize the drive)

Selecting  partition table as "Intel [msdos]" gives me options to write or delete  the mbr sector, both of which fail ("Write error: Can't write new MBR  code." / "Write error: Can't clear partition table.")
all options under "analyse" result in nothing but read errors.

using partition table "none" show the entire drive as unformatted, printing errors that boot sectors are unreadable
```

Disk /dev/sdd - 15 GB / 14 GiB - CHS 15200 64 32
     Partition                  Start        End    Size in sectors
   P FAT32                    0   0  1 15199  63 32   31129600

Boot sector
fat32_boot_sector: Can't read boot sector.
Bad

Backup boot sector
fat32_boot_sector: Can't read backup boot sector.
Bad

Sectors are identical.

A valid FAT Boot sector must be present in order to access
any data; even if the partition is not bootable.


```


Dumping the partition table shows it is entirely empty:

```

Disk /dev/sdd - 15 GB / 14 GiB - CHS 15200 64 32
   P FAT32                    0   0  1 15199  63 32   31129600
Boot sector                        Backup boot sector
0000 00000000 00000000   ........  00000000 00000000   ........
0008 00000000 00000000   ........  00000000 00000000   ........
0010 00000000 00000000   ........  00000000 00000000   ........
0018 00000000 00000000   ........  00000000 00000000   ........
0020 00000000 00000000   ........  00000000 00000000   ........
0028 00000000 00000000   ........  00000000 00000000   ........
0030 00000000 00000000   ........  00000000 00000000   ........
0038 00000000 00000000   ........  00000000 00000000   ........
0040 00000000 00000000   ........  00000000 00000000   ........
0048 00000000 00000000   ........  00000000 00000000   ........
0050 00000000 00000000   ........  00000000 00000000   ........
0058 00000000 00000000   ........  00000000 00000000   ........
0060 00000000 00000000   ........  00000000 00000000   ........
0068 00000000 00000000   ........  00000000 00000000   ........
0070 00000000 00000000   ........  00000000 00000000   ........
0078 00000000 00000000   ........  00000000 00000000   ........
0080 00000000 00000000   ........  00000000 00000000   ........
0088 00000000 00000000   ........  00000000 00000000   ........
0090 00000000 00000000   ........  00000000 00000000   ........
0098 00000000 00000000   ........  00000000 00000000   ........
00A0 00000000 00000000   ........  00000000 00000000   ........
00A8 00000000 00000000   ........  00000000 00000000   ........
00B0 00000000 00000000   ........  00000000 00000000   ........
00B8 00000000 00000000   ........  00000000 00000000   ........
00C0 00000000 00000000   ........  00000000 00000000   ........
00C8 00000000 00000000   ........  00000000 00000000   ........
00D0 00000000 00000000   ........  00000000 00000000   ........
00D8 00000000 00000000   ........  00000000 00000000   ........
00E0 00000000 00000000   ........  00000000 00000000   ........
00E8 00000000 00000000   ........  00000000 00000000   ........
00F0 00000000 00000000   ........  00000000 00000000   ........
00F8 00000000 00000000   ........  00000000 00000000   ........
0100 00000000 00000000   ........  00000000 00000000   ........
0108 00000000 00000000   ........  00000000 00000000   ........
0110 00000000 00000000   ........  00000000 00000000   ........
0118 00000000 00000000   ........  00000000 00000000   ........
0120 00000000 00000000   ........  00000000 00000000   ........
0128 00000000 00000000   ........  00000000 00000000   ........
0130 00000000 00000000   ........  00000000 00000000   ........
0138 00000000 00000000   ........  00000000 00000000   ........
0140 00000000 00000000   ........  00000000 00000000   ........
0148 00000000 00000000   ........  00000000 00000000   ........
0150 00000000 00000000   ........  00000000 00000000   ........
0158 00000000 00000000   ........  00000000 00000000   ........
0160 00000000 00000000   ........  00000000 00000000   ........
0168 00000000 00000000   ........  00000000 00000000   ........
0170 00000000 00000000   ........  00000000 00000000   ........
0178 00000000 00000000   ........  00000000 00000000   ........
0180 00000000 00000000   ........  00000000 00000000   ........
...

```

Repairing the boot sector also fails.


As a last resort i tried dd, which fails to write anything at all with the following error message:

```

root@lab:~# dd if=/dev/zero of=/dev/sdd count=32
dd: writing to '/dev/sdd': Input/output error
1+0 records in
0+0 records out
0 bytes copied, 0.0014385 s, 0.0 kB/s

```

changing count to 64, 128, 512 is no different.

In fact, dd cant even read from the drive:

```

root@lab:~# dd if=/dev/sdd  of=/dev/null count=1
dd: error reading '/dev/sdd': Input/output error
0+0 records in
0+0 records out
0 bytes copied, 0.00146952 s, 0.0 kB/s

```

I  tried the above list on a Kali linux laptop (1x usb3 2xusb2), an Ubuntu  18.04 Laptop (1xusb3) and my fedora workstation (4xusb3, 1xusb2) on all  usb ports.

Im at the end of my knowledge, maybe you can help me find a solution I have overlooked?

---

### Post by howefield on 2019-01-24
Thread moved to the "*WIndows*" forum.

---

### Post by janeharrell on 2019-01-24
Are you sure the windows forum is the right place for this?
The  entire process described in the thread was carried out on was ubuntu  18.04, the entire testing is done on various linux distros and no  windows machine was used during any part of this process.
In fact,  the only thing owned by microsoft here is the .iso file that was flashed  to the thumbdrive, which couldve been easily switched out for any cd  iso image considering the context and issue described above.

---

### Post by yancek on 2019-01-24
> The  entire process described in the thread was carried out on was  ubuntu  18.04, the entire testing is done on various linux distros and  no  windows machine was used during any part of this process.

But you are trying to create a bootable usb of the proprietary microsoft windows system to install a windows system. 

> which couldve been easily switched out for any cd  iso image considering the context and issue described above. 		

No, creating and booting a windows iso is an entirely different process than a Linux system.  Linux/Ubuntu developers have no reason to develop a method to create a bootable proprietary windows install usb yet they have done it.  If you can follow simple, detailed instructions, the link below explains how to do this.  You can even skip the installation of grub to the usb and simply put the correct menuentry in the grub.cfg file of your current Ubuntu system to boot it.  Used this myself and it works.

 [http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by ajgreeny on 2019-01-24
I can not help with the Windows installation, but to return the USB drive to normal use you may find that [mkusb]("https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive") is your best answer, assuming you're using Ubuntu.

Download and install mkusb using the launchpad ppa at [https://launchpad.net/~mkusb/+archive/ubuntu/ppa](https://launchpad.net/~mkusb/+archive/ubuntu/ppa)

There is also a section in the main [mkusb]("https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive") page about using it to install Windows though as I say I have no experience of that, so it has to be your trial and error.

---

### Post by janeharrell on 2019-01-24
The windows installation is the source of the issue, not the issue itself. The issue is that the almost new thumbdrive has a zeroed partition table which seems to be impossible to be overriden. I'm sorry if I came across wrong, but a zeroed partition table that cannot be overriden despite the absence of write protection sounds like a hardware (or at least hardware-related) problem to me. Getting an operating installed anywhere is outside the scope of my issue. If my thread was wrongly leading you to believe that this was the issue I had, please advise me on how to edit it to better reflect my intentions.

---

### Post by janeharrell on 2019-01-24
Tried mkusb-nox on the drive - seems to be suffering the same freeze that gparted was bested by.

The output (didnt change for over an hour):
```

***  Unmount the device if mounted  ****************************
 
Name: ata-HFS128G3BMND-3210A  Dev: /dev/sda  Size: 128GB
Name: ata-TOSHIBA_MQ02ABF100  Dev: /dev/sdb  Size: 1000GB
Name: usb-090c_USB_DISK       Dev: /dev/sdc  Size: 15938MB
Live drive: /dev/map
 
---> 1: wipe device USB: 090c_USB_DISK Dev: /dev/sdc Size: 15938MB
Go ahead with (g) or quit with (q). Toggle USB-only with (u).
g
1: wipe device USB: 090c_USB_DISK       Dev: /dev/sdc  Size: 15938MB
 Final checkpoint 
Please check again that it is the correct target device! (y/n)
y
 
Wiping the first megabyte (MibiByte) of /dev/sdc ... :
 
gpt_zap: done
< /dev/zero pv  | dd bs=4096 count=256 of=/dev/sdc
Please wait for sync (flushing file system buffers to the device)
until 'Done' is written ...
1.06MiB 0:00:00 [ 275MiB/s] [   <=>     


```

Tried wipe-1 and wipe-whole-device, same result
One thing to note is that the thumbdrive's led that indicate activity shuts off entirely whenever i try using mkusb on it.

Starting to think it might be magically fried, albeit the usb port working fine for all other usb drives and external usb hdds.

---


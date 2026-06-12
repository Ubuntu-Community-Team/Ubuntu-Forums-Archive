---
title: "mounting USB drive"
date: 2009-09-01
forum: Server Platforms
---

### Post by happyhacker on 2009-09-01
I have plugged in an 60Gbyte drive and the system has recognised it. I want to transfer an hda disk image there for site removal. I used webmin with the following command and details. If anyone can tell me what to do next that would be helpful. I want to be able to just bring the drive in plug it in and later just unplug it without the server objecting. PS the drive was installed by windows so I'm not sure what Ubuntu is seeing in the details below.

Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb6f0730

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3645    29278431    7  HPFS/NTFS
/dev/sdc2            3646        7296    29326657+   5  Extended
/dev/sdc5            3646        7140    28073556   83  Linux
/dev/sdc6            7141        7296     1253038+  82  Linux swap / Solaris
> sudo mount -t ntfs-3g /dev/sdc1 /media/external
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc1 /media/external -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc1 /media/external ntfs-3g force 0 0

---

### Post by lmlypfan on 2009-09-01
The drive was removed improperly from a windows machine. 
All you need to do is force mount the drive with the command it instructed you to use.

```
mount -t ntfs-3g /dev/sdc1 /media/external -o force
```

---

### Post by happyhacker on 2009-09-07
Many thanks, that did it but I now have under media/usb an empty folder and under (new I think) mnt/win the files showing on the USB drive. No dirs or files are shown below these points. I can create a dir in either of these (just to test) and delete it. I know I have files on the USB drive from windows.

In webmin in "Disk network and files systems I have:

/media/usb FUSEBLK SCSI device C partition 1 Yes No

Anyone advise?

---


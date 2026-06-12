---
title: "How to make scanner work on VM of Oracle VirtualBox"
date: 2019-05-18
forum: Virtualisation
---

### Post by satimis on 2019-05-18
Hi all,

Oracle VirtualBox
Host - Ubuntu 16.04
VM - Ubuntu 18.04
Epson scanner 3490
XSane

The scanner is working on Host XSane but unable to work on VM.

On VM:
$ lsusb```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

$ scanimage -L```

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

$ sane-find-scanner```

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.
  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x1d6b/0x0003 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.
  # Not checking for parallel port scanners.
  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```
could not open USB device 0x1d6b/0x0003 at 002:001: Access denied (insufficient permissions)

$ ls -al /usr/share/sane/snapscan/```

total 72
drwxr-xr-x 2 root    root     4096 May 13 21:56 .
drwxr-xr-x 4 root    root     4096 May 13 21:55 ..
-rwxrwxrwx 1 satimis satimis 64000 May 13 21:54 Esfw52.bin

```

On Host
&#10219; cat /etc/group | grep vboxuser```

vboxusers:x:129:satimis

```
User already registered.  

Edit-1
====
$ ls -ald /usr/share/sane```

drwxr-xr-x 4 root root 4096 May 13 21:55 /usr/share/sane

```
$ ls -ald /usr/share/sane```

drwxr-xr-x 4 root root 4096 May 13 21:55 /usr/share/sane

```
$ ls -ald /usr/share/sane/snapscan/```

drwxr-xr-x 2 root root 4096 May 13 21:56 /usr

```

Do I need to change all of them to satimis:satimis ?

Edit-2
Problem solved as follow:
===================

VM VirtualBox Manager
--> Settings --> USB

USB Device Filters
right click the "Blank window"
--> Add Filter From Device
--> select [EPSON Scanner [0110]]
--> OK

Restart VM
Now Epson scanner is working on VM. XSane finds the scanner.

Regards
satimis

---


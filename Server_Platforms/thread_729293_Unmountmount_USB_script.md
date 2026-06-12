---
title: "Unmount/mount USB script"
date: 2008-03-19
forum: Server Platforms
---

### Post by SumnerBoy on 2008-03-19
Hi,

I recently posted about a problem I am having with my Canon MP530 USB scanner. Basically it won't work with the ehci_hcd module (USB2.0) loaded. Therefore in order to scan I have to unload the module, do the scan, and then reload it.

When I unload the module my external USB drive (USB2.0) is, not surprisingly, unmounted/lost. Therefore I wanted to write a script which I can call to enable/disable scanning on my server which will handle unmounting/remounting the USB drive etc.

It needs to do the following...

   ENABLE SCANNING
   1. unmount the external USB drive
   2. unload ehci_hcd module
   3. remount the external USB drive (it will only be mounted as USB1.1 but at least I can still access it etc).

   DISABLE SCANNING
   1. unmount the external USB drive
   2. load ehci_hcd module
   3. remount the external USB drive (will be remounted as USB2.0).

Below is the script I have tried. It is having problems with the unmounting/mounting of the external USB drive. It will unmount ok but then fails to remount after the ehci_hcd module is loaded/unloaded. 

If I run these commands in a shell manually it all seems to work just fine so I am a little confused as to why the script is failing.

Here is the error message I get from mount when running the script...

```
mount: special device /dev/disk/by-uuid/c4bbe385-7f58-417b-a6f6-02bfbf9bff23 does not exist
```

Can anyone see any obvious problems/errors?

My script...

```
#! /bin/sh

# Description: Script to configure Canon MP530 scanner on WEKA.
#              Unloads the USB2.0 (ehci_hcd) module and remounts
#              the Maxtor external USB drive as USB1.1.
#
# Author: Ben Jones <ben@weka.com>
#

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/usr/sbin:/usr/bin:/sbin:/bin
SCRIPTNAME=/etc/scanner
USB2MODULE=ehci_hcd
MAXTORMOUNT=/mnt/maxtor/

# unmount the Maxtor external USB drive
umount $MAXTORMOUNT

case "$1" in
  start)
        # unload the USB2.0 module
        modprobe -r $USB2MODULE
        ;;
  stop)
        # load the USB2.0 module
        modprobe $USB2MODULE
        ;;
  *)
        echo "Usage: $SCRIPTNAME {start|stop}" >&2
        exit 3
        ;;
esac

# re-mount the Maxtor external USB drive
mount $MAXTORMOUNT

:

```

---

### Post by bigredradio on 2008-03-20
The mount command you are using is relying on the entry you have in /etc/fstab. According to the error it appears that device does not exist.

You might want to mount it by giving the device name and mount point. Also, that device name is created by udev. You may need to run udevtrigger or udevstart (don't remember off of the top of my head) so that the device is now available. Also, since you are using the USB1 driver, it may have a new device name. One for USB2 and one for USB1. I am guessing here and someone with more hotplug experience might be able to better answer.

---

### Post by SumnerBoy on 2008-03-23
Thanks for those tips - I think they make sense to me. 

When I do a lsusb I see the external drive on USB Bus 005. When I remove the ehci_hcd module the same drive is shown on USB Bus 003. They both seem to be shown as /dev/sdb1 however, when running fdisk -l.

So I updated my script to run the mount procedure as

   mount -t ext3 /dev/sdb1 /mnt/maxtor

Now when I run the script it will successfully unmount, then unload the ehci_hcd module, but fail to re-mount. If I re-run the script a few times, eventually the mount succeeds. 

The same happens when re-loading the module. It needs to be run 1-5 times until it eventually re-mounts on the different bus. I tried waiting a few mins between un-loading/loading the module to see if it was some kind of delay but this made no difference.

What could be causing this? Why do I need to attempt the mount 1-5 times before it successfully works?

I get mount errors like;

mount: /dev/sdb1 is not a valid block device
mount: special device /dev/sdb1 does not exist
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The first time I run the script I get the 'not a valid block device' message, and then subsequent attempts give the 'does not exist' message. But sometimes I just get the 'wrong fs type'.

Any ideas on this? I am pretty lost here!

---

### Post by bigredradio on 2008-03-23
The device node /dev/sdb1 is being created by udevd. You may need to run udevstart or udevtrigger first. Then put a sleep in your script to wait. I seem to recall there is a delay necessary for the devices to become available.

---

### Post by SumnerBoy on 2008-03-24
Thanks for your help with this BigRed!

I have added the following to my script just prior to re-mounting;

```

udevtrigger --subsystem-match=usb
udevsettle
sleep 5

```

And things seem to be working a lot better now. The USB drive is un-mounted and re-mounted in either USB1.1 or USB2.0.

Thanks again!

---


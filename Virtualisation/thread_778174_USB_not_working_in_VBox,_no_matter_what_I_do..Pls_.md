---
title: "USB not working in VBox, no matter what I do..Pls help"
date: 2008-05-01
forum: Virtualisation
---

### Post by madu on 2008-05-01
Hey guys,

I'm frustrated to the gut with getting the USB working in VBox in HARDY. Everything else works fine.. Weird part is that I dont get any error when opening the 'settings' in VBox.. Every other peripheral is available (on the left side column),general,Hard disks, Serial ports, etc., except for the USB.

I did everything that has been mentioned around. Pls give me a clue.
Here are my files.

**/etc/fstab**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8894b631-aee8-4c38-abf4-247b5212fab0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=a82a1a9c-0996-4cf7-84d4-d510f9d1e6aa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
[B]
/etc/init.d/mountdevsubfs.sh[/B]
> do_start () {
	#
	# Mount a tmpfs on /dev/shm
	#
	SHM_OPT=
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT="-osize=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm $SHM_OPT

	#
	# Mount /dev/pts. Create master ptmx node if needed.
	#
	domount devpts "" /dev/pts -ogid=$TTYGRP,mode=$TTYMODE

	#
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

	## Mount the usbfs for use with Virtual Box
        domount usbfs usbdevfs /proc/bus/usb 
        -onoexec,nosuid,nodev,devgid=124,devmode=664
}


**/etc/group**
> madu: x:1000:madu
vboxusers: x:124:madu,root
usbusers: x:1001:madu

**/etc/init.d/rules/40-permissions.rules**
> # USB serial converters
SUBSYSTEM=="usb_device", GOTO="usb_serial_start"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GOTO="usb_serial_start"
GOTO="usb_serial_end"
LABEL="usb_serial_start"
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
				,GROUP="vboxusers",MODE="0666", GROUP="dialout"
LABEL="usb_serial_end"

Please help me getting this to work. 

Thanks in advance.

Madu.

---

### Post by IncadudeF on 2008-05-02
install your OS in VB

when it tells you if it can configure your screen resolution turn off the os

then turn it back on.

when your desktop is fully set up go to: Devices>InstallGuestadditions

then open it up in the OS your emulating. And install it.

then the mouse should work.

---

### Post by Aearenda on 2008-05-02
The open source edition of VirtualBox doesn't support USB - the personal edition from their website does. So if you installed 'virtualbox-ose' you'll have to unistall it and then follow the instructions on [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) (takes you to a Sun site, but stay with it).

---

### Post by niteshifter on 2008-05-02
Hi,

Assuming you're using the PUEL version of VBox...

This part of /etc/init.d/mountdevsubfs.sh doesn't look right:

```
## Mount the usbfs for use with Virtual Box
domount usbfs usbdevfs /proc/bus/usb
-onoexec,nosuid,nodev,devgid=124,devmode=664
```

If the snippet you posted of the file is a cut 'n paste, that's a malformed line - there's a line break after .../bus/usb. Should be all one line. However, I think you don't need that code present, I'd comment that part out in mountdevsubfs.sh and see what that does for you.

The entry in your fstab (at the end) will handle mounting, that's why I think it doesn't belong.

---

### Post by madu on 2008-05-02
Hey thanks a lot guys...
Yes I am using the OSE.. didnt know it doesnt support USB..! there were so many guides explaining about how to get the USB working but strangely none of them mentioned about OSE not supporting it.. thanks a lot man..

Yes niteshifter.. it is a cut n' paste.. I guess i'll comment that out and see.. probably the problem is the OSE version..

Thanks heaps guys..!!

Madu.

---

### Post by fmartinez on 2008-05-02
I can across the same situation with Vitrualbox when I was using Dreamweaver in a Virtual Windows XP. I had my website on the USB and wasn't able to access through Virtualbox. This is my workaround: 
- I installed SAMBA.
- Set my desktop with a static IP to ensure my network was always connected. 
- Then configured SAMBA to read the path to my USB device and make it accessable through the MSHOME network. 
- Lastly I logged into VBox and accessed that network drive (which was USB) added with "MAP A NETWORK DRIVE" in Windows. 
I don't know if this is exactly what your looking for, but I hope it helps. 
GOOD LUCK!

---


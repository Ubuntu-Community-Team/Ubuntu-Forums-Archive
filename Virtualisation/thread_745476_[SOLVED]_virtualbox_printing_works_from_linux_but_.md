---
title: "[SOLVED] virtualbox: printing works from linux but from virtualbox"
date: 2008-04-04
forum: Virtualisation
---

### Post by keratos on 2008-04-04
hi

I have installed virtualbox (not OSE) and have managed to get the USB printer, an Epson R800 stylus photo, recognised as a "USB filter", have cselected this and yet cannot print anything from inside an XP guest.

The setup is as follows:
I have setup a separate user and enabled them in the vboxusers group. Sucessfully installed XP and then the Guest Additions. Mouse and screen resolution are fine, and XP is "good". From the VritualBox GUI I the USB printer is selectable and active. However, when inside the guest XP VM, the USB printer is not even seen, as though its not there.

After some searching on the forums I found a post that suggests changing the permissions in the "udev" (whatever that is??) as follows:
```

# USB devices
KERNEL=="legousbtower*",	MODE="0666"
KERNEL=="lp[0-9]*", SUBSYSTEMS=="usb",		GROUP="lp"

```
the MODE was previously "0644" and was changed to "0666"

this was ineffectual! still no print.

I have also read some posts suggesting to unplug the printer whilst booting and other to make sure it is plugged in. Also, suggestions to unplug before starting the XP guest VM and other suggestions to ensure its plugged in!!! ALL, VERY confusing.

At the end of the day, the printer is visible in the VirtualBox GUI interface but not visible (in device manager) within the XP guest.

```

$ VBoxManage list usbhost
VirtualBox Command Line Management Interface Version 1.5.6
(C) 2005-2008 innotek GmbH
All rights reserved.

Host USB Devices:

UUID:               d1b24978-a6a2-4469-728a-4a983f8aea26
VendorId:           0x055f (055F)
ProductId:          0x021d (021D)
Revision:           1.0 (0100)
Product:            USB Scanner
Address:            /proc/bus/usb/001/004
Current State:      Unavailable

UUID:               57bb2383-5f13-44f2-b9af-1662aff9a82b
VendorId:           0x09da (09DA)
ProductId:          0x002b (002B)
Revision:           0.1 (0001)
Manufacturer:       A4Tech
Product:            Wireless Battery Free Optical Mouse
Address:            /proc/bus/usb/001/005
Current State:      Unavailable

UUID:               f49a6f89-ffb3-4880-e4b5-7debb2513c8d
VendorId:           0x04b8 (04B8)
ProductId:          0x0007 (0007)
Revision:           1.0 (0100)
Manufacturer:       EPSON
Product:            USB2.0 Printer (Hi-speed)
SerialNumber:       RQ0170410151530090
Address:            /proc/bus/usb/005/004
Current State:      Unavailable

```

I also read the VirtualBox help menus that suggested
```

Debian Etch has the mount command in /etc/init.d/mountkernfs.sh. Since that distribution has no group usb, it is also the easiest solution to allow all members of the group vboxusers to access the USB subsystem. Modify the line 
domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev
so that it contains 
domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev,devgid=85,devmode=664

```
again, innefectual.

Note: When I am inside the XP guest, the USB printer (+ other devices) are listed when I click on the USB icon in the VirtualBox control GUI (bottom right) but the devices are "greyed out". ?? 



Can you help me to diagnose please.

thank you.

---

### Post by keratos on 2008-04-05
[SOLVED]

/etc/fstab, add:
```

none /proc/bus/usb devgid=<vboxusers group id>,devmode=0666 0 0

```

in my case vboxusers group id = 107 so "devgid=107"

---

### Post by orengolan on 2008-04-05
i have similar problem.
my usb devices are disabled.
i modified the fstab but it didn't help.

any ideas?

---

### Post by keratos on 2008-04-06
From where did you obtain the virtual box binaries?

---

### Post by theZoid on 2008-04-22
> **keratos said:**
> [SOLVED]

/etc/fstab, add:
```

none /proc/bus/usb devgid=<vboxusers group id>,devmode=0666 0 0

```

in my case vboxusers group id = 107 so "devgid=107"

Same problem here....scanner works in VB non free, not printer...I've done this many times, but not on Hardy Heron.

My vboxuser id is 120.  Can you give me the exact fstab entry to cut and paste to make sure I've not typo'd it?  Also, did you modify 40-permissions.rules?

thanks!

---

### Post by keratos on 2008-04-24
> **orengolan said:**
> i have similar problem.
my usb devices are disabled.
i modified the fstab but it didn't help.

any ideas?

did you install VirtualBox from the ubuntu repository (using synaptic)?

---

### Post by keratos on 2008-04-24
> **theZoid said:**
> Same problem here....scanner works in VB non free, not printer...I've done this many times, but not on Hardy Heron.

My vboxuser id is 120.  Can you give me the exact fstab entry to cut and paste to make sure I've not typo'd it?  Also, did you modify 40-permissions.rules?

thanks!

if your scanner works then the USB filesystem is mounted and setup correctly. Its a "one size fits all" so far as USB is concerned.

Can you print from ubuntu?

post output of
```

udevinfo -a -p `udevinfo -q path -n /dev/usb/lp0`

```

assuming your printer is /dev/usb/lp0.

check (ls) the /dev/usb directory for possible other printer device names.

---

### Post by theZoid on 2008-04-24
> **keratos said:**
> if your scanner works then the USB filesystem is mounted and setup correctly. Its a "one size fits all" so far as USB is concerned.

Can you print from ubuntu?

post output of
```

udevinfo -a -p `udevinfo -q path -n /dev/usb/lp0`

```

assuming your printer is /dev/usb/lp0.

check (ls) the /dev/usb directory for possible other printer device names.

Thanks Keratos....I fixed it, and wrote my solution here from top to bottom
[http://forum.notebookreview.com/showthread.php?t=242936](http://forum.notebookreview.com/showthread.php?t=242936)
btw, in your earlier post, I think 0666 s/b 0664 in fstab...that's why it didn't work for the other poster above, you should edit that typo for posterity.  thanks again for replying.

PS, check out post linked above for Hardy Heron...it's a conversion of somewhat of the Gutsy procedures which I've done many times.  If you see something that's not needed, please tell me!

---

### Post by keratos on 2008-04-25
No.

0666 is correct.

0664 would remove write 'w' access for world users.

---

### Post by theZoid on 2008-04-25
> **keratos said:**
> No.

0666 is correct.

0664 would remove write 'w' access for world users.

World users?  write access?  Man, you need to explain to explain that one to me and whoever else gets this by googling.  0666 kills the printer for me in Hardy Heron 8.04.  I've set the dev mode 0664 in mountdevsubfs.sh also.  Here's what works for me, please pick it apart if you see something wrong and explain the consequences (I'm not a coder, an accountant :):

Add yourself to the group VirtualBox created during install called "vboxusers" The VB install creates this group, find it, don't add another one.

Create a group named "usbusers" and put yourself in it.

sudo groupadd usbusers
sudo gpasswd -a <yourusername> usbusers

Or do the above in Control Center under 'users and groups'.

Now uncomment the 4 lines below 'Magic to make /proc/bus/usb work' in mountdevsubfs.sh , they will be commented out by default) so it looks like the following:

sudo gedit /etc/init.d/mountdevsubfs.sh

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Now then,

Modify the rules in file "/etc/udev/rules.d/40-permissions.rules"
Change the lines :

From:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

To :

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GROUP="usbusers", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

In Hardy Heron, I had to add the lines at the end of the file (under To: above) as this file is different in Hardy Heron, that is you won't see the 'from' lines above like you will in Gutsy.

The Grande Finale,

add this line:

none /proc/bus/usb usbfs devgid=120,devmode=664 0 0

to your /etc/fstab file. Just make sure that 120 is your vboxusers group (use your own number).

---


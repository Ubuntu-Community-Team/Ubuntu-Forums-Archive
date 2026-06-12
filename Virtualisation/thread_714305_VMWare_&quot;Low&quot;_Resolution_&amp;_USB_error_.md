---
title: "VMWare &quot;Low&quot; Resolution &amp; USB error code 10"
date: 2008-03-03
forum: Virtualisation
---

### Post by frogotronic on 2008-03-03
This was originally posted as a[ post 122 pages into a thread]("http://ubuntuforums.org/showpost.php?p=4440697&postcount=1213"), which I'm sure nobody reads & I didn't know that there was a Virtualization category.

Hi,

I have two problems which I haven't been able to solve:

1) I'm getting a strange error with some programs on VMWare Server 1.0.4 on Gusty Gibbon. Basically the XP program incorrectly interprets the resolution and refuses to run. Please see attached png image. Current issue is with TurboTax2007. There must be a workaround for this issue. I installed VMWare server from Synaptic and have VMWare tools installed (via the VM menu).

2) Can't get USB devices to install correctly. Always ends up with an "Error Code 10 - this device can't start" when I check it with the XP Device manger.

Any suggestions on either of these problems would be appreciated.

- CH

---

### Post by fjgaude on 2008-03-03
Well, from my experience, you don't try to set the video resolution through Windows, but through the Edit/Perferences/Display of vmware server. Click on both items there and everything becomes automatic.

As for the rest, USBs, here's what many have done:

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```
```

    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Then place in the fstab file this line:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Good to add this line into your guest .vmx file using text editor:

```
mainMem.useNamedFile=FALSE
```

You will have full copy, paste from host to and from guest, and USB device handling capability, drives, scanners, printers, etc.

Let us know how you are doing.

---

### Post by frogotronic on 2008-03-03
Thank you!

That fixed the USB problem completely.

Also, When I start the TurboTax2007 in "FullScreen" mode, it fires up and runs and then I can go to a windowed version of VMWare.  I had the Autofit Guest and Autofit Window already checked.  I think this bug has to do with the SVGA II VMWare adapter and how it gives feed back in a non-fullscreen mode.  Anyway, it all works now.

Once again, thanks!

- CH


                         :guitar:


P.S.  How stable is Hardy?  Ready enough for day-today use on production machines?

---

### Post by fjgaude on 2008-03-03
> **cement_head said:**
> 
P.S.  How stable is Hardy?  Ready enough for day-today use on production machines?

Great, happy to have you up and running.

Hardy is stable but not full featured yet. Some important needed things are missing, but I'm sure they will all come together in the last week before formal release, as always happens.

---


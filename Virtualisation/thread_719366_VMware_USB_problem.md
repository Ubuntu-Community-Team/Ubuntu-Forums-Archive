---
title: "VMware USB problem"
date: 2008-03-09
forum: Virtualisation
---

### Post by funiae on 2008-03-09
Hello,

I don't see usb devices in my Ubuntu running in VMWare. I read some posts about, unfortunately it didn't solve my problem. 
The main problem is that when i'm running:

sudo /etc/init.d/mountdevsubfs.sh start

i got message:

Filesystem type 'usbfs' is not supported. Skipping mount.
ln: creating symbolic link `/dev/bus/usb/devices' to `.usbfs/devices': File exists
mount: mount point /proc/bus/usb does not exist

Additional info:
I have already uncomment lines:
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
I have VMWare tools installed

---

### Post by dcstar on 2008-03-10
> **funiae said:**
> Hello,

I don't see usb devices in my Ubuntu running in VMWare. I read some posts about, unfortunately it didn't solve my problem. 
.........

[http://ubuntuforums.org/showpost.php?p=4363424&postcount=4](http://ubuntuforums.org/showpost.php?p=4363424&postcount=4)

---

### Post by funiae on 2008-03-10
It didn't help. I still have message:

Filesystem type 'usbfs' is not supported. Skipping mount.
ln: creating symbolic link `/dev/bus/usb/devices' to `.usbfs/devices': File exists
mount: mount point /proc/bus/usb does not exist

---

### Post by dcstar on 2008-03-11
> **funiae said:**
> It didn't help. I still have message:

Filesystem type 'usbfs' is not supported. Skipping mount.
ln: creating symbolic link `/dev/bus/usb/devices' to `.usbfs/devices': File exists
mount: mount point /proc/bus/usb does not exist

Nowhere in the solution does it say to run that command, why are you doing it?

---

### Post by funiae on 2008-03-14
I have made everything from solution post, unfortunatelly i still don't see any usb device.

I tried to run: sudo /etc/init.d/mountdevsubfs.sh start, and this error message apears.

---

### Post by fjgaude on 2008-03-14
Where and how are you looking for the USB devices?

---

### Post by bluewhale on 2008-03-16
One thought: after altering my installation as recommended by DCStar I had to alter the hardware for this VM> ( I've been running Ubuntu for 2 weeks now. Google is my best friend )  

If you haven't done so start up that VM, go to VM / Settings / then click on +Add near the bottom of that window. A USB Root controller can be found there. After installing it it took a couple of restarts of this XP VM but I'm able to finally use my Memory stick again. \\:D/

---


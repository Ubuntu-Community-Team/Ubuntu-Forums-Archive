---
title: "Virtual Box USB PROBLEM"
date: 2008-01-18
forum: Virtualisation
---

### Post by psychok7 on 2008-01-18
Hi there,i have a usb problem in my virtual box.. i managed to correct ir by typing:

# VBOX=$(grep vboxusers /etc/group | sed 's/vboxusers:x:\(.*\):.*/\1/')
# sudo mount -t usbfs -o devgid=$VBOX,devmode=664,nodev,noexec,nosuid none /proc/bus/usb

my problem is, everytime i star VB i have to do this comands on the console, how can i make this comands run automatically everytime my  ubuntu starts??
cheers

---

### Post by fjgaude on 2008-01-18
I don't know much about VBox but in VMware Server you have to do two things in Gutsy 7.10:

Uncomment lines 42-45 lines starting with #mkdir -p /dev/bus/usb/.usbfs

```
gksudo gedit /etc/init.d/mountdevsubfs.sh

    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

```

Than if necessary, add this line to your fstab file in /etc:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

That should do it for USB drives, scanners, printers, etc.

Let us know how you do.

---

### Post by psychok7 on 2008-01-18
> **fjgaude said:**
> I don't know much about VBox but in VMware Server you have to do two things in Gutsy 7.10:

Uncomment lines 42-45 lines starting with #mkdir -p /dev/bus/usb/.usbfs

```
gksudo gedit /etc/init.d/mountdevsubfs.sh

    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

```

Than if necessary, add this line to your fstab file in /etc:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

That should do it for USB drives, scanners, printers, etc.

Let us know how you do.


well did that and it didnt work...the codes i put in the beginning work for sure, it just that i dont know how to make it start everytime my computer starts.do you?

---

### Post by fjgaude on 2008-01-18
I'm far from any expert but I'd put your two commands in a script and then give it a name. Then add that file to the init.d.

Someone here has got to know how to do this.

OTOH, gosh, there are lots of folks using USB devices in VBox that has not had to do what you are doing.

You did reboot after you did what I suggested?

---

### Post by psychok7 on 2008-01-18
sorry dude, i forgot to reboot. it actually works, and i didnt need to edit the fstab.. thanks :)

---

### Post by psychok7 on 2008-01-18
by the way i tried vmware workstation, and virtual box is much more faster then vmware. if u havent tried give it a try

---

### Post by fjgaude on 2008-01-18
Okay, wonderful... the fstab addition has been needed by some when using USB flash drives. It seems to be some kind of race issue with the scipts that makeup the startup of Ubuntu. It's an overkill but needed for these kinds of flash drives.

Thanks for hanging in there and achieving success... so sweet.

---


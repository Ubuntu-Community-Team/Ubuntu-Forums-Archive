---
title: "VMware installation"
date: 2008-02-22
forum: Virtualisation
---

### Post by kxr1der on 2008-02-22
When i go to add/ remove applications it tells me that it wont install vmware cuz its not supported in my country or something (im in th US) is there anyway around this?

---

### Post by fjgaude on 2008-02-22
What kind of computer do you have? Are you trying to install the Player? Are you using 64-bit Ubuntu?

I have always used the vmware site, vmware.com, to get my vmware server binaries. It easy to unpack into a directory and then simply follow instructions with the vmware-install.pl file.

---

### Post by maestrobwh1 on 2008-02-22
Um, or just use VirtualBox.  It's free and pretty much does the same thing.

---

### Post by TheLions on 2008-02-22
or dwn workstation and be Jack Sparrow!

---

### Post by kxr1der on 2008-02-23
Well I am currently using virtual box but it won't sync my iPhone so I want to try vmware and maybe it will work

---

### Post by HermanAB on 2008-02-23
VMware can be difficult to install, but I prefer it over Virtualbox, mainly because Win2003 doesn't work on Virtualbox.

VMware is OK with Windows XP and it is easy to install VMware Tools in XP (Get VMware Tools from an evaluation version of VMware Workstation).

I found that to install VMware Tools on a Linux VM, I always need to install the kernel source, compile and install it first, which is a PITA, but then it works pretty good.

BTW, I finally got Virtualbox to work properly on my Eee PC.  The only way I could get networking to work was in NAT mode with DHCP:  [http://aeronetworks.ca/eeepc-mdv-howto.html](http://aeronetworks.ca/eeepc-mdv-howto.html) and [http://aeronetworks.ca/eeepc-howto.html](http://aeronetworks.ca/eeepc-howto.html)

---

### Post by fjgaude on 2008-02-23
> **kxr1der said:**
> When i go to add/ remove applications it tells me that it wont install vmware cuz its not supported in my country or something (im in th US) is there anyway around this?

The Player isn't for 64-bit. Here's what I suggest:

   1. Get latest version, 1.0.4, of vmware server from vmware.com website. Log-in and get at the same time your free license number.

   2. Install linux headers matching your kernel version, xinetd, and build-essential using apt-get or Synaptic, if they are not already on your system.

   3. Unpack the software

   4. Then run

 ```
sudo ./vmware-install.pl
```

   5. follow the guide using mostly the defaults, then

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

Then place  in the fstab file this line:

```
usbfs /proc/bus/usb usbfs auto 0 0 
```

You will have full copy, paste from host to and from guest, and USB device handling capability, drives, scanners, printers, etc.

Let us know how you are doing.

---

### Post by kxr1der on 2008-03-04
It seems like no virtual machine will recognize an Iphone so im just gunna have to continue dual booting.

---


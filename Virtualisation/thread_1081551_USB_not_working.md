---
title: "USB not working"
date: 2009-02-26
forum: Virtualisation
---

### Post by MickSulley on 2009-02-26
Hi,

My PC runs Ubuntu 64 bit Intrepid with VirtualBox 2.1.4 and within that I have XP Pro.  I have a Plustek slide scanner connected via USB, on the VirtualBox setup I have created a filter for the scanner, but I cannot see in within XP.  The USB icon at the bottom right says 'No USB devices attached' even though it is plugged in an switched on.

Any idea why it does not work?

Mick

---

### Post by smani on 2009-02-26
Have a look at [http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html](http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html) - you will not find the section to uncomment in intrepid, instead, just add the text.

---

### Post by bodhi.zazen on 2009-02-26
With the latest version of Virtualbox you do not need to do that.

You do need the PUEL version of virtual box and not the OSE.

With the guest off, on the virtual box gui fron end, select your Windows VM and then double click on the usb tab.

Activate your usb device, plug in your usb device, an dadd it to the list,

Re boot the guest.

If that does not work, test a flash drive. 

If the flash drive also fails, we need to lok at your usb device settings.

If the flash drive works, but, the scanner does not, that is different.

Often if the usb device does not work in linux it will not work in windows guests.

---

### Post by MickSulley on 2009-02-26
Tried all that and it still does not work.  I have plugged in a flash drive and added it, the VirtualBox window now says USB device filters 2 (2 active), but when I open up XP the icon still says no USB devices attached, and the flash drive does not show in explorer

Any other ideas?

Mick

---

### Post by bodhi.zazen on 2009-02-26
What version of VirtualBox are you using ?

You need the PUEL edition (USB does not work in OSE).

---

### Post by MickSulley on 2009-02-28
My VirtualBox is 2.4.1, not sure if it is PUEL or not, how can I tell?

---

### Post by bodhi.zazen on 2009-02-28
> **MickSulley said:**
> My VirtualBox is 2.4.1, not sure if it is PUEL or not, how can I tell?

How did you install VirtualBox ? If you downloaded a .deb from the web site , that is the PUEL edition. If you installed it from Synaptic (or apt-get, or the Ubuntu repositories) then it is the OSE

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by MickSulley on 2009-03-01
To be sure I have just downloaded it again from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
I downloaded Ubuntu 8.10 ("Intrepid Ibex") AMD64 and reinstalled.  I then rebooted and it is still the same, USB flash and my scanner show in the setup screen but they are not there in XP.  When I plug in the flash it shows in Ubuntu, I have also unmounted in Ubuntu but it still does not show in XP.

Any other ideas?  Could there be something really basic that I have missed?

Thanks

Mick

---


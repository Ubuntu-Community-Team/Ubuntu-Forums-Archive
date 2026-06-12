---
title: "USB not working in Vmware on ubuntu?"
date: 2007-12-16
forum: Virtualisation
---

### Post by saltydog on 2007-12-16
Hi all,

I have just installed vmware-server in my Gutsy and it is working quite nice. One issue: it seems that the usb port is not detected. If I insert a pendrive, it is not seen by the virtual guest. Going to VM->Removable Devices->USB Devices->.. I find nothing, the menu is empty.

---

### Post by toastytaco on 2007-12-16
Is VMware running in root...if it is not u can run it with 'gksu' or 'sudo' an and try it that way..

---

### Post by saltydog on 2007-12-17
I tried running it as root, but no success. The USB-pen is not detected. The menu VM->Removable Devices->USB Devices is empty.

---

### Post by illbashu on 2007-12-18
you should read this [thread](http://ubuntuforums.org/showthread.php?t=626118)

---

### Post by fjgaude on 2007-12-19
Here's the ticket to ride:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Uncomment lines 42-45 starting with #mkdir p....

That should do it. Feisty had them uncommented but not Gutsy.

---

### Post by saltydog on 2007-12-20
Thank you very much. It is working now.

---

### Post by alina.bolero on 2008-02-29
I second that!  Thank you sooooo much for the fix!  Massive kudos.

---

### Post by SonWon on 2008-07-13
I followed this however my usb is still empty, any ideas?

Thank you,
SonWon

---

### Post by SonWon on 2008-07-13
Got it, add the USB Controller to the VM by editing the settings.

:)

---

### Post by marcon00 on 2008-09-04
fjgaude : worked like a charm ..

---

### Post by fjgaude on 2008-09-04
Good to know that as things change things don't change. <smile>

---

### Post by tml240 on 2008-10-01
I did this then my wireless is not detected.... USB works fine though.

Is there any way to make both work at the same time? 

Thanks

---

### Post by mojavelinux on 2008-12-26
> **fjgaude said:**
> Here's the ticket to ride:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Uncomment lines 42-45 starting with #mkdir p....

That should do it. Feisty had them uncommented but not Gutsy.

That did it, thanks! Note that I did have to shut down the guest operating system (Windows XP) and start it again. But immediately my VM console recognized that there were USB devices.

---

### Post by mojavelinux on 2008-12-26
Please note that if Windows XP crashes when you plug in a USB 2.0 device, you may need to upgrade your Virtual Hardware Version, which you should see somewhere in the VMWare Console (varies by version). In the Web Console you should see it in the right hand menu.

---


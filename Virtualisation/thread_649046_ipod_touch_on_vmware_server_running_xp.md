---
title: "ipod touch on vmware server running xp"
date: 2007-12-24
forum: Virtualisation
---

### Post by zshift on 2007-12-24
hey all, i have an issue here:

i have an ipod touch, im running ubuntu. gusty gibbon 7.10, i have vmware server 1.04, and i have xp pro installed as my main virtual machine. When I plug in my ipod touch i receive a message asking me if i want to import photos. none are found, of course. in vmware server, i go to menu option vm > removable devices > usb, and theres a grayed out "apple inc. ipod" option that cannot be selected. my usb pendrive works fine, as well as my memory card reader built into the computer. im trying to use itunes to sync/recover, etc. any ideas?

---

### Post by fjgaude on 2007-12-24
You might try adding this to your fstab file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

That has helped some with USB drives.

---

### Post by popch on 2007-12-26
I think that this is an issue with VMWare's USB support. As far as I know, VMWare only supports USB version 1.1.

VMWare's web site could be a better place to find out if the iPod works in a VM.

---

### Post by fjgaude on 2007-12-26
> **popch said:**
> I think that this is an issue with VMWare's USB support. As far as I know, VMWare only supports USB version 1.1.

VMWare's web site could be a better place to find out if the iPod works in a VM.

I have several USB 2.n devices working with VMware guest. 

Yes, let's check VMware web site for info on iPod.

---

### Post by popch on 2007-12-26
> **fjgaude said:**
> I have several USB 2.n devices working with VMware guest.  (...) 

So did I, in VMWare Workstation 5.x. They did walk but not run, i.e. they worked but were dreadfully slow.

---

### Post by StianH on 2007-12-28
I've got pretty much the same setup and I'm unable to give the guest OS access to the iPod. Couldn't find anything useful on the website either.

For some reason Ubuntu kind of detects the iPod as a camera, and asks to import photos. Perhaps this is part of why it will not work in VMware?

**Update**: I'm not really shure why, but all of a sudden today, I plugged in my iPod to charge it (which I've had no trouble with in Linux), I started my XP virtual machine, and decided to just give it a go, and there it was available in the VM -> Removable devices -> USB.

Of course, it is still only available as a USB 1 device, but it's a good start :) I went to be last night thinking I'd have to arrange for a dual boot :D

---

### Post by fhlipZero on 2008-01-01
I have seen this plenty of times since the iPod Touch came out. Do you have iTunes installed on the virtual machine. Windows XP/Vista thing you have plugged in a camera with pictures unless you install itunes which apparently carries along drivers for the ipods.

---

### Post by StianH on 2008-01-02
Yes of course iTunes is installed. ACtually XP detects that a iPod has been hotplugged, and some "bubbles" popup lettming me know this. Also there's a message saying that I've plugged a high speed USB device in a low-speed port.

iTunes doesn't seem to like the fact that the iPod is plugged into a USB1.1 port, because it does not acknowledge the ipod

---


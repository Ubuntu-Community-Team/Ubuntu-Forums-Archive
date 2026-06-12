---
title: "Virtual Server Ed. install. Update via USB dongle?"
date: 2011-10-20
forum: Virtualisation
---

### Post by Swerve1000 on 2011-10-20
Hi,

I have Ubuntu 11.04 as a host machine, and Ubuntu Server Edition running in VirtualBox.

The only internet connection I have is via a USB 3G wireless dongle. 

The host machine worked fine with it straight out the box, but I want to use it update the server installation. 

How can I add it to the servers repo? I'm stuck with what network settings to use in virtualbox and should/do I need to mount the usb dongle (the server only has a terminal). I figure then add it to the sources.list file. 

Could anyone tell me how to go about doing this? I only need to update it and install a couple of programs, then can put it back to how it is now.

Thanks very much.

---

### Post by mrhobbeys on 2011-10-20
Personal opinion is that you are better off updating via the VB's normal connection (if I even understand what you are asking). 

If you need to mount the USB though you need to have the extensions pack installed for VB. 

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

VirtualBox 4.1.4 Oracle VM VirtualBox Extension Pack

You need to get the correct version than getting the USB to capture in the VB is a matter of "magic" you need to add it to the VB via the USB menu then you have to unplug and replug and restart in some strange order that I have never bothered to remember because I do everything I can to avoid needing to use a USB on VB these days. Anyways if I have completely misunderstood what you need or you want my best guess at the procedure you need to take to get the USB connection to work let me know.

---

### Post by Swerve1000 on 2011-10-21
Thanks for that, I didn't know about the extension pack.

---

### Post by CharlesA on 2011-10-21
The VM should have a setting for "NAT" that will share the host's connection.

Shouldn't have to mess with anything.

---


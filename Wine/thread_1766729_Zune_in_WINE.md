---
title: "Zune in WINE?"
date: 2011-05-24
forum: Wine
---

### Post by Phaze08 on 2011-05-24
Has anyone gotten Zune to work in Wine? I've tried but it doesnt even try to load up the program. I understand that this is a major microsoft program but I already got a brand new Zune HD for my birthday and would like to be able to use it on Ubuntu. Between that and my vpn/vnc, I am unable to use Ubuntu at this time, but if I get those working, I could go full Ubuntu. I've ran other programs in Wine just fine but zune doesnt even try to run, just gives an error message that I cant recall as I am not on Ubuntu at this time. Anyone know anything about this?

---

### Post by Tweak42 on 2011-05-25
> **Phaze08 said:**
> Has anyone gotten Zune to work in Wine? I've tried but it doesnt even try to load up the program. I understand that this is a major microsoft program but I already got a brand new Zune HD for my birthday and would like to be able to use it on Ubuntu. Between that and my vpn/vnc, I am unable to use Ubuntu at this time, but if I get those working, I could go full Ubuntu. I've ran other programs in Wine just fine but zune doesnt even try to run, just gives an error message that I cant recall as I am not on Ubuntu at this time. Anyone know anything about this?

Judging by the wine appdb track record I don't think it will be working anytime soon.  
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5741](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5741)

I use the Zune software running on VirtualBox winXP instance using the USB passthru to connect to my Zune enabled phone and it works fine.

---

### Post by I_ated_it on 2011-07-29
> **Tweak42 said:**
> Judging by the wine appdb track record I don't think it will be working anytime soon.  
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5741](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5741)

I use the Zune software running on VirtualBox winXP instance using the USB passthru to connect to my Zune enabled phone and it works fine.

Can you explain how you did this?

I recently bought a HTC arrive windows phone and have Zune installed in Windows 7 virtually but I cant get it to recognize my phone.

---

### Post by Tweak42 on 2011-07-30
> **I_ated_it said:**
> Can you explain how you did this?

I recently bought a HTC arrive windows phone and have Zune installed in Windows 7 virtually but I cant get it to recognize my phone.

You must have the extensions pack installed.
[http://www.virtualbox.org/manual/ch01.html#intro-installing](http://www.virtualbox.org/manual/ch01.html#intro-installing)

Then you add USB filter in the virtual machine settings.
[http://www.virtualbox.org/manual/ch03.html#settings-usb](http://www.virtualbox.org/manual/ch03.html#settings-usb)

As long as the phone is recognized by ubuntu (run lsusb in terminal to list detected usb devices), it should be detectable in the virtualbox usb filter settings.  Add a filter for the phone and checkbox so it's enabled.  Once windows is booted, it should detect the phone is connected.  Disabling the filter is equivalent to pulling the cable.

---

### Post by I_ated_it on 2011-07-30
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 003: ID 045e:04ec Microsoft Corp. **
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Ubuntu recognizes the device but when I go to add a usb device filter in the VirtualBox settings it shows no devices available.  I tried entering the Vendor ID and Product ID manually but it still doesnt recognize the phone.

Was your phone automatically detected when you set up your filter?

---

### Post by I_ated_it on 2011-07-30
I figured it out, it turns out I didnt have administrative access to the vboxuser account.

If anyone else has a similar issue the link below should help.

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---


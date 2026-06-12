---
title: "Windows 8 in virtualbox"
date: 2014-05-01
forum: Virtualisation
---

### Post by Mazate on 2014-05-01
Howdy... my wife is griping again because she can't use itunes in Ubuntu and now wants her windows 8 back.  Is installing windows in virtualbox any easier than it used to be.  Historically I've had trouble installing anything in virtualbox that was on a usb drive, which my windows 8 installation is.  Any insight would be appreciated.

---

### Post by tfrue on 2014-05-01
It was always easier for me to have the .iso on my HDD and then go to the Storage settings on my new VM in VirtualBox and use the IDE disk drive to point to the .iso on my HDD. So when it boots, it will automatically load it like it's a cd in the drive.

Chris

---

### Post by Mazate on 2014-05-01
Preferably I'm going to need USB access, not only for installing windows but also for connecting the iphone to the computer for itunes synchronization.

---

### Post by tfrue on 2014-05-02
Good luck, I was trying to do that as well, but I was unable to get pass the Linux OS. When I would connect the phone to the computer, the iPhone would ask if I trust this computer, and of course I said yes, then it would load for a second and prompt me again if I trusted this computer. So I was unable to add a filter in VirtualBox for the phone since I wasn't even able to get it connected to the computer. If you find a fix, let me know because I don't have a Windows machine for my wife to install iTunes and sync her phone and library. 

Thanks, 
Chris

---

### Post by at_first_light on 2014-07-16
It will be easier to install Windows 8 from an iso file, but you can install it from a usb. It's been a while since I used vitualbox (I mostly use VMware Player now adays). Just boot up the virtual machine, connect the usb, then restart the virtual machine, enter the vm's quick-boot menu, choose to boot from removable media, and it should boot into the usb installer. 

In order to get full usb support on VirtualBox you will need to install the extension pack.

Alternatively you might consider dual-booting Windows 8 with Ubuntu?

---

### Post by baranfoto on 2014-07-16
very good articles
thanks and thanks and thanks:popcorn:
[bazitime]("http://www.bazitime.com") and [thinava]("http://www.thinava.com")

---


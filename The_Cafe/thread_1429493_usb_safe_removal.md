---
title: "usb safe removal"
date: 2010-03-14
forum: The Cafe
---

### Post by AbyssRock on 2010-03-14
hi,  was wondering if there's a way to safely disconnect a usb device from computer, I ask this because in windows when you disconnect a usb pen with the safe removal, the pen light then turns off, while I tried removing the pen with ubuntu and the light was still on ?

---

### Post by ssam on 2010-03-14
either right-click on the usb disk on you desktop, or in the side bar in the file browser. (you might see options 'unmount', 'eject', 'safely remove', they will all make the usb drive safe to remove)

---

### Post by Psumi on 2010-03-14
> **ssam said:**
> either right-click on the usb disk on you desktop, or in the side bar in the file browser. (you might see options 'unmount', 'eject', 'safely remove', they will all make the usb drive safe to remove)

Only one of them, though, will make the USB Drive shut off its light (if it has one.)

---

### Post by dragos240 on 2010-03-14
If you want to do it the hard way (works on all distros):
Have root's password
Make sure your in the wheel group

su -c "umount /media/disk"

---

### Post by madjr on 2010-03-14
> **AbyssRock said:**
> hi,  was wondering if there's a way to safely disconnect a usb device from computer, I ask this because in windows when you disconnect a usb pen with the safe removal, the pen light then turns off, while I tried removing the pen with ubuntu and the light was still on ?

hey

when you **unmount** then its safe to remove even if the light is on (its just a light)

i got 3 pendrives with lights and have been unmounting them for years without problems

**unmount = safe**

---

### Post by koenn on 2010-03-14
> **dragos240 said:**
> If you want to do it the hard way (works on all distros):
Have root's password
Make sure your in the wheel group

su -c "umount /media/disk"

we have a wheel group now ?

---

### Post by chriswyatt on 2010-03-14
Here's a program you might find useful, it adds an icon to your notification area to let you safely eject media, similar to the Windows one, except it's faster and better :D

[http://launchpad.net/ejecter](http://launchpad.net/ejecter)

I'm quite lazy and only tend to safely remove drives when I've just been using them, it does some delayed writing after something's been written to the disk I think.

---


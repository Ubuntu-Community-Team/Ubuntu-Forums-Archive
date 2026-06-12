---
title: "[SOLVED] InnoTek VirtualBox XP USB issue"
date: 2008-10-07
forum: Virtualisation
---

### Post by metalmaniac248 on 2008-10-07
i recently managed to install XP in InnoTek Virtualbox on my Hardy Machine


it runs brilliantly except XP does not detect any of my USB devices such as Flash drives, or My external HDD, however it does destect and use my USB keyboard and Mouse,


i have enabled USB in the settings menu


any ideas?


thanks

---

### Post by howefield on 2008-10-07
What version of Virtualbox are you using ?

The version in the repository is the OSE (Open Source Version) and doesn't have usb support, the version on the virtualbox website PUEL (Personal Use & Evualation Licence) does have USB support although you will have to enable it once installed.

---

### Post by metalmaniac248 on 2008-10-07
i instaled it from the deb of the innotek website

---

### Post by howefield on 2008-10-07
It isn't INNOTEK that maintain Virtualbox anymore, hasn't been since about version 1.5, Sun now develop it and it is on version 2.0.2 

Try running this command to set up USB assuming you have the PUEL version.

```
echo "none /proc/bus/usb usbfs devgid=$(grep plugdev /etc/group | sed 's/plugdev:x:\(.*\):.*/\1/'),devmode=664 0 0" | sudo tee -a /etc/fstab
```

---

### Post by metalmaniac248 on 2008-10-07
i ran the command and restarted my virtual box yet still no luck

---

### Post by metalmaniac248 on 2008-10-08
i fixed the USB issue by going to devices and selecting the device i want to use

now i hav a new issue i am trying to create a bigger virtual Hard drive for my virtual XP, however i get an error whenever i create one larger than 2GB

---

### Post by bodhi.zazen on 2008-10-08
> **metalmaniac248 said:**
> i get an error whenever i create one larger than 2GB

And that error would read .....

---

### Post by metalmaniac248 on 2008-10-09
sorry

i have fixed that error by just selecting dynacially expanding hard drive 

all is well now

---

### Post by Merk42 on 2008-10-11
Well I have an issue with the USB in the PUEL version of Virtualbox 2.0.2.  While it detects my mouse and keyboard it won't detect my webcam. How do I go about fixing that? I even tried that command that howefield posted.

---

### Post by b0b138 on 2008-10-11
Under the details tab for the machine, click on usb. Then over on the right click the button with the green plus sign to add usb devices.

---

### Post by Merk42 on 2008-10-12
> **b0b138 said:**
> Under the details tab for the machine, click on usb. Then over on the right click the button with the green plus sign to add usb devices.

Oh that did it, I hit the wrong button to add the usb devices, I was hitting the blue one.

---


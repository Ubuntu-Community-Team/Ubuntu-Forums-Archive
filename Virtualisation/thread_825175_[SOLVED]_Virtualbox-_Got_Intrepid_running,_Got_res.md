---
title: "[SOLVED] Virtualbox- Got Intrepid running, Got resolution sorted, no sound or usb ?"
date: 2008-06-10
forum: Virtualisation
---

### Post by philinux on 2008-06-10
Any help appreciated.

Big noob to virtual stuff though.

Done this and rebooted.
 sudo gedit /etc/init.d/mountdevsubfs.sh

---

### Post by Victormd on 2008-06-10
What version of virtualbox did you install? From the repos? If so, you won't be able to get usb working from there... you have to install from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI").

---

### Post by philinux on 2008-06-10
Version 1.6.2 from their site.

---

### Post by Victormd on 2008-06-10
I'm feeling really stupid now because I had USB working just fine with my virtualbox, but it's been a while since I've used it and now I can't anymore... my flash drive doesn't even show up under the Devices menu...

---

### Post by philinux on 2008-06-10
What about sound?

---

### Post by Victormd on 2008-06-10
hummm... let me check...

Nope... crapped out too... Not really sure what to tell you now...
Guess I'll have to join in on trying to figure this one out, even though I don't use it anymore and was almost removing it... hehehe

---

### Post by Victormd on 2008-06-10
Just did this and it worked fine!
[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

The first step alone didn't do it for me but after the second one, everything (USB related) is working...
now to sound...

---

### Post by philinux on 2008-06-10
Sorry not for me.

lsusb reports nothing

lspci does not show sound card

---

### Post by Victormd on 2008-06-10
... guess you'll have to wait for someone more experienced to come and help. I don't recall ever having to do any tweaking to get USB on virtualbox (guest additions worked fine) and now, the link worked no problems (had to reboot though) so can't really say anything else... sorry

---

### Post by philinux on 2008-06-10
Got sound now - you have to select it at startup.

Usb now shows unknown device.

---

### Post by Victormd on 2008-06-10
It depends on the sound device you select... I had alsa selected and don't know why it didn't work...

---

### Post by philinux on 2008-06-11
Selected pulse audio and it works, now how to get usb sorted then

---


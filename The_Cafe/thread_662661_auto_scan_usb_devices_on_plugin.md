---
title: "auto scan usb devices on plugin"
date: 2008-01-09
forum: The Cafe
---

### Post by EscArtist on 2008-01-09
Hello,

I would like to install some antivirus on my ubuntu box and have it scan any usb device for viruses automatically when i plug it in. is this possible and how?

Regards

---

### Post by OffHand on 2008-01-09
> **EscArtist said:**
> Hello,

I would like to install some antivirus on my ubuntu box and have it scan any usb device for viruses automatically when i plug it in. is this possible and how?

Regards

Why would you?

---

### Post by EscArtist on 2008-01-09
we are running windows workstations in the company i work for and many of the people need to use usb devices when leaving the office for installations or deployment of software.... 

i would have one machine running ubuntu + anti virus act as a safe zone between the outer world (clients) and out windows network. before leaving the office everybody will scan the usb devices and after coming back also...

i would like to have it automatically to simplify it for my colleges and since they have never used linux.

---

### Post by OffHand on 2008-01-09
Cool idea! Unfortunately I do not know how you can do this. There are a couple of virus scanners for Linux around but automating the scanning might be tricky. Good luck.

---

### Post by madeinbrazil on 2008-03-30
I'd like to know this too.

I've found that on System > Preferences > Removable Drives and Media there is an option to run automatically a program when USB is plugged. But, what shall I enter? BTW, I'm using ClamTK.

---

### Post by pseudo-random on 2008-03-30
Add something like ```
clamscan /media/USBDEVICE
```
In order to ensure the usb device gets mounted in the same spot each time you'll need to add it to your /etc/fstab.

---


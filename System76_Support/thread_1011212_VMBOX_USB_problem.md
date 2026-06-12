---
title: "VMBOX USB problem"
date: 2008-12-14
forum: System76 Support
---

### Post by daci007 on 2008-12-14
hello
i have problem in vmbox in ubuntu,i have windows xp in the vmbox work great but the problem i can't access to the USB drive,when i try to mount it from vmbox,show me this:
"Not permitted to open the USB device, check usbfs options"
any ideas??

---

### Post by howefield on 2008-12-14
Are you talking about Virtualbox  and are you using Intrepid.?

You might need to add the following to your fstab

```

none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0
```

where XXX is the group id of your vboxusers group.

---

### Post by thomasaaron on 2008-12-15
Here's what worked for me under Hardy. I've not tested it with Intrepid yet. You'll need to scroll down to the part dealing with USB support.

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

Also, in Hardy, I had to install Sun's version for that tutorial to work. The version in the repositories would not support USB.

---

### Post by howefield on 2008-12-15
Is there meant to be a link in there ?

---

### Post by thomasaaron on 2008-12-15
Yes, sorry. I added the link.

---


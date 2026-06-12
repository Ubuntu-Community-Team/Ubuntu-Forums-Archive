---
title: "scsi host4: runtime PM trying to activate child device host4 but parent..."
date: 2016-10-13
forum: Ubuntu Development Version
---

### Post by VMC on 2016-10-13
I noticed this message on every boot since latest kernel. Goggling didn't revel anything until recently.

You can read about some c file usb fixes here:
[http://www.spinics.net/lists/linux-usb/msg147006.html](http://www.spinics.net/lists/linux-usb/msg147006.html)
[http://www.spinics.net/lists/linux-usb/msg147006.html](http://www.spinics.net/lists/linux-usb/msg147006.html)
and here
[https://patchwork.kernel.org/patch/9262153/](https://patchwork.kernel.org/patch/9262153/)

To check if you have this:
```
grep child /var/log/syslog
```

I know I'm not alone here, and since it's an upstream matter, little can be done outside of recompiling the usb c files as mentioned in the above links.
I'm just curious why no one else has mentioned it. At first I thought it was just my setup.

---

### Post by VMC on 2016-10-13
I found this bug report on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1629714](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1629714)

---


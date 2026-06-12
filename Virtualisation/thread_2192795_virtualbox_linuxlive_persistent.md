---
title: "virtualbox linuxlive persistent"
date: 2013-12-09
forum: Virtualisation
---

### Post by tendouser on 2013-12-09
I am running lubuntu 13.10 with portable virtualbox but i see that data is not been stored when i set persistent mode at the boot menu.
Any help?

---

### Post by bashiergui on 2013-12-09
Are you logging in as guest?

---

### Post by tendouser on 2013-12-10
[http://www.linuxliveusb.com/help/guide/using-lili](http://www.linuxliveusb.com/help/guide/using-lili)

** Be aware that persistence CAN'T be used in VirtualBox.

---

### Post by tendouser on 2013-12-11
What is the point in virtualize with virtualbox portable but not storing in casper-rw?????

---

### Post by bashiergui on 2013-12-11
I had never heard of virtualbox portable until this thread. Sounds like it's not the tool you need for what you want to do. What exactly do you want to accomplish? Have a portable OS on a flash drive that's persistent? See if this fits your needs:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by tendouser on 2013-12-11
Is there any virtualisation software that I can use lubuntu as guest OS and using as persistent?

---

### Post by tendouser on 2013-12-11
Note that I can boot and use it as persistent from USB drive but not virtualizing.

---

### Post by bashiergui on 2013-12-11
If you want a lubuntu persistent pen drive: [http://askubuntu.com/questions/168246/why-isnt-persistence-working-on-lubuntu-12-04-live-usb](http://askubuntu.com/questions/168246/why-isnt-persistence-working-on-lubuntu-12-04-live-usb)

Or do you want it to be a virtual machine? If so then why don't you export an .ovi from virtualbox each time you're done. Save it on the pen drive. Then import it into virtualbox the next time you need it.

---

### Post by tendouser on 2013-12-11
what is an .ovi file?

---

### Post by bashiergui on 2013-12-11
Something I made up apparently. Virtualbox creates .ovf files. Here's the documentation on importing & exporting vms:
[https://www.virtualbox.org/manual/ch01.html#ovf](https://www.virtualbox.org/manual/ch01.html#ovf)

---


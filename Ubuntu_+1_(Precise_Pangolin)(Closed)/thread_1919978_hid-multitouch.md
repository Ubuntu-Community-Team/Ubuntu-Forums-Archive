---
title: "hid-multitouch"
date: 2012-02-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by teh603 on 2012-02-03
Anyone got a good guide for getting hid-multitouch working, on any system really? My Dell Duo has been gathering dust because the ACPI doesn't seem to work with a kernel below 3.2, but if I do go with the newer kernel the touchscreen refuses to work, even with the driver installed as per the manufacturer's instructions.

---

### Post by ashindeed on 2012-03-27
I have the same issue, I followed steps list on [http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html]("http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html"), but my touchscreen fails to work under 12.04! For now, I am using 11.10. Hopefully, the issue will be sorted out by release date.

P.S. I have a Quanta touch screen

---

### Post by teh603 on 2012-03-28
Might want to check my bug on launchpad; the workaround is to add an echo line to your rc.local and reboot. It won't seem to work if you try typing the echo line on the Ubuntu command prompt, even prefaced with sudo; it seems to have to be run as root, but for some reason it works when you add it to the rc.local.

---

### Post by ashindeed on 2012-03-28
Will try that! As you mentioned i did try to run it using Sudo/root with no luck. The problem is MT_CLS_* is not available for my setup (Quanta touchscreen)

---

### Post by ashindeed on 2012-03-30
I tried everything I can, nothing seems to work. My device is recognized but does not work in 12.04 but it does 11.10

So i installed oneiric kernel on precise. Working well so far. No multi-touch though.

---


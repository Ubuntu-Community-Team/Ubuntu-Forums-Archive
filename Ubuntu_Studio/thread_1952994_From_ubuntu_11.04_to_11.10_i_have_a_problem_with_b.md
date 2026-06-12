---
title: "From ubuntu 11.04 to 11.10 i have a problem with boot option? u_u"
date: 2012-04-05
forum: Ubuntu Studio
---

### Post by alchimisto on 2012-04-05
Hi ! :)

When i upgraded my ubuntu from 11.04 to 11.10 i didn't found windows XP in the boot choices u_u can you help me?

I'm here, and i'm waiting for you :)

---

### Post by alchimisto on 2012-04-05
No body knows? :(

---

### Post by alchimisto on 2012-04-05
My boot info:

[http://paste.ubuntu.com/916149/](http://paste.ubuntu.com/916149/)

Can anybody help me? :-({|=

---

### Post by jejeman on 2012-04-05
Did you tried to update grub mannualy?
```
sudo update-grub
```
you are missing /boot.ini in the boot report

    Boot files:        /boot.ini /ntldr /NTDETECT.COM

---

### Post by alchimisto on 2012-04-07
> **jejeman said:**
> Did you tried to update grub mannualy?
```
sudo update-grub
```
you are missing /boot.ini in the boot report

    Boot files:        /boot.ini /ntldr /NTDETECT.COM

I didn't work, but when a repared Boot.ini and tryed with Boot repair, my problem was resolved... thanks anyway ^^

---


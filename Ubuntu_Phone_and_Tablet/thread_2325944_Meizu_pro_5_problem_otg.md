---
title: "Meizu pro 5 problem otg"
date: 2016-05-26
forum: Ubuntu Phone and Tablet
---

### Post by mily2 on 2016-05-26
Hi, I tried connect a pen drive, card reader with Micro SD and USB  Mouse-keyboard, but didn't work. The USB type C to Micro USB adapter  works, because the phone charge through Micro USB port. 

Pen drive and card reader led are off; and fdisk -l command line not recognize.

Has somebody tried this? This is a bug? 

Thanks

---

### Post by mily2 on 2016-05-28
I suspect that the adapter does not support OTG, but has anyone tried this feature, please?

---

### Post by donquichot2016 on 2016-06-03
I guess the cable is the problem, as all those USB devices work fine on my phone (Bq Aquaris E5). Does **dmesg** say anything about the connected devices?

---

### Post by mily2 on 2016-06-04
Thanks donquichot2016.[B]
dmesg[/B] doesn&#8217;t say nothing, neither **dmesg | -i usb** or **lsblk**.

---

### Post by mily2 on 2016-08-04
The cable was the problem. Today I tested OTG OK (pen drive and mouse-keyboard IR) with new cable.

---


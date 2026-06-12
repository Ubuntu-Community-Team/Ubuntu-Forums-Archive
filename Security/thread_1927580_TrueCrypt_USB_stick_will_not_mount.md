---
title: "TrueCrypt USB stick will not mount"
date: 2012-02-18
forum: Security
---

### Post by 0011235813 on 2012-02-18
Hello all,
I have recently encrypted one of my USB drives with TrueCrypt. When I plug in the stick, Ubuntu does not recognize it. However, TrueCrypt can recognize it. But here's the problem; when I click "select device" and click on my USB stick (I encrypted it all), and then type in the password, I get an error saying "password incorrect or not a TrueCrypt volume". Does anyone know what's wrong with it?

If not, is there anyway I can make the system recognize it so I can format the stick and have it usable again?

Thanks.

---

### Post by gordintoronto on 2012-02-18
With the stick plugged in, run this command: sudo gparted

Caution: gparted will probably point at your hard drive initially, there is a drop-down item in the top-right to change to the USB stick. Then you can right-click on it, select unmount, select format, click on "apply."

---

### Post by 0011235813 on 2012-02-19
> **gordintoronto said:**
> With the stick plugged in, run this command: sudo gparted

Caution: gparted will probably point at your hard drive initially, there is a drop-down item in the top-right to change to the USB stick. Then you can right-click on it, select unmount, select format, click on "apply."

Hmm... I'll try it with KDE Partition Manager, since I don't have GParted installed.
Thanks, I was able to format it and it works now.

---


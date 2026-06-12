---
title: "Vbox Problems"
date: 2010-06-10
forum: Virtualisation
---

### Post by w0Rm210 on 2010-06-10
Well i was digging through a huge box of my moms old CD's and found an install disc for windows 98 i wanted to check it out so i popped it in and ran it through vbox it installed like normal then it said computer will now restart when it restarted it just started the install again. And this isen't just with winXP it's with windows 3.1 ISO i found. And also fedora OpenSUSE and a bunch of others same problem over and over. What's going on with it?

---

### Post by mal205 on 2010-06-11
Did you unmount the CD before you did a re-start?

---

### Post by w0Rm210 on 2010-06-11
> **mal205 said:**
> Did you unmount the CD before you did a re-start?


No but that still dosen't explain the other linux distro problems.... I was just using their ISO images XP was the only one that was on CD.

---

### Post by mal205 on 2010-06-13
Once the install in VBox has completed you need to reconfigure the Virtual Machine to boot from the install location, not the CD or the CD Image.

If you don't, it'll just rerun the install.

---


---
title: "External USB HDD"
date: 2012-10-29
forum: Ubuntu Studio
---

### Post by Big_Kiwi on 2012-10-29
Hi All
it's been a while but I recently downloaded and installed Ubuntu 11.10 on my laptop and upgraded to 12.10. I have a 2.5 external HDD (formally the internal drive for this laptop till it crashed) I have put the drive in to a External USB case os I can retrive the data stored on the drive but UBUNTU can not see the drive, My question is do I need to install a progam to allow me to see the drive, and if so where can I download it from?

I have installed "GParted Partition Editor" but still can not see the USB HDD any advise would be welcome Thanks Again

---

### Post by jejeman on 2012-10-30
See if 
```
lsusb
```
shows the drive.

---

### Post by danelwillis on 2012-10-30
it could be a simple problem like mounting the usb try mounting in terminal  "mount /dev/sda1" the sda1 might change depending if you have other usbs inserted into your computer**[B]**[/B]****

---

### Post by sgx on 2012-10-30
Good time to use a puppy linux, to back up any needed data,
and then do a clean install. Delete any old partition(s)
then create / partition, and   /home partition, then install
the ubuntu of choice.

[http://www.macpup.org/](http://www.macpup.org/)  this Puppy is less than 200 meg,
burn the iso to CD, then boot from cd into ram, and pmount will let you access the drive.
Cheers

---

### Post by Big_Kiwi on 2012-11-02
thanks for all those tips, but I have only one Question (this may be silly) but how do I access the terminal, I can see it is installed but how do I activate it,

---

### Post by jejeman on 2012-11-02
Not shure what version of ubuntu you are using.
If Ubuntu ctrl+alt+t opens terminal emulator
If Ubuntu Studio open from aplication menu Terminal emulator

---

### Post by Big_Kiwi on 2012-11-03
I would like to thank all for your help with this matter but the problem seems that it may not all be software as there seems to be a fault with my external HDD case, have to get my hands on another and then see how it goes

Again thanks to all:guitar:

---


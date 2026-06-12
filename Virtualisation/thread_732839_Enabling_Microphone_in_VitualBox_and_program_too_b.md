---
title: "Enabling Microphone in VitualBox and program too big to fit in memory"
date: 2008-03-23
forum: Virtualisation
---

### Post by amrith on 2008-03-23
Gutsy being my Host OS and Win XP the guest.
I face these issues in my Virtual XP:

1.There is no option to enable microphone to have a voice chat ( though I can hear them as there is Audio setting in Virtualbox).
How to enable microphone in Virtualbox?

2.I downloaded Gtalk and tried installing but I got this error : " program too big to fit in memory " 
Tried increasing the base memory ,tried downloading the program again but still the problem persists.
(I was able to install yahoo messenger)

My config: 

Intel Dual Core 3.0 Ghz
Motherboard:Intel 946GZ 
RAM:1 GB
HDD:250 GB
Ubuntu 7.10

Many thanks.

---

### Post by amrith on 2008-03-23
Typo : Gutsy being my Host OS and Win XP the Guest.

---

### Post by amrith on 2008-03-23
Bump !

---

### Post by ruibernardo on 2008-03-23
Did you installed the "VirtualBox guest additions" (or something like that) in the guest?.

---

### Post by amrith on 2008-03-24
Yes I have installed Guest Additions.

---

### Post by amrith on 2008-03-25
bump!

---

### Post by robertor on 2008-10-10
nobody know how to enable the mic?
I have the same problem.
Roberto

---

### Post by emanamini on 2010-08-29
I have same problem 
is there any way to fix this problem
please answer

---

### Post by TheFu on 2010-08-30
I do not know how to fix this issue, but have you checked the device on the host OS and tried to get passthru working?  If it is a USB device (often, internal devices are), then enabling the USB passthru should do it.

If you have normal sound working, check out the sound mixer app for your install. `alsamixer` is what mine uses.

`lshw` and the ubuntu sound troubleshooter may be helpful.

Sorry, I'm not any real help.

---

### Post by BrandyBear on 2010-08-31
You might need to check GTalk to see if it is compatible with virtual box:popcorn:

---


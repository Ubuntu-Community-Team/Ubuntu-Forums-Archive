---
title: "Best for Compatibility"
date: 2007-05-12
forum: The Cafe
---

### Post by bren21 on 2007-05-12
Okay, I have been having many issues trying to get some of my hardware to work on Ubuntu (specifically my scanner). Ubuntu is the only Linux distro I have tried, and I do like it, and I really hate Windows, but I also need my scanner to work. I have had such problems with other hardware, but I managed to get most of them fixed through the various tutorials posted. However the scanner just will not budge. So I was wondering if there are any other distros of Linux that are more compatible with hardware and such. I really do NOT want to go back to windows, however I might have to.

---

### Post by a12ctic on 2007-05-12
What scanner do you have? If its made by lexmark your probobly out of luck, they are one of the least caring companies around.

---

### Post by Adamant1988 on 2007-05-12
I have a deskjet F335 that's cheap and offers basically out of the box complete functionality with Ubuntu (just load up the PSC-1200 driver and go).  If you need to replace your scanner, I highly suggest this one as a cheap replacement.

---

### Post by bren21 on 2007-05-12
I have an Epson Perfection V350.

---

### Post by bren21 on 2007-05-12
I was just looking around at distrowatch.com, and according to it Mepis and KNOPPIX both have very good hardware support. Has anyone tried these before and could perhaps let me know their pros and cons in your own opinion?

---

### Post by Adamant1988 on 2007-05-12
> **bren21 said:**
> I was just looking around at distrowatch.com, and according to it Mepis and KNOPPIX both have very good hardware support. Has anyone tried these before and could perhaps let me know their pros and cons in your own opinion?

Mepis is based on Ubuntu, and Knoppix does have good hardware support. 

Some hardware just doesn't work with most distros at all, or any of them, you may potentially have such a piece of hardware.

---

### Post by a12ctic on 2007-05-12
Your printer will be as well supported in ubuntu as it is in any other linux distribution, I doubt you'll have much luck in other distros if it wasn't supported in ubuntu. Google is your friend. Try to figure out if your printer is supported in linux/unix at all!

---

### Post by bren21 on 2007-05-12
Well, it is supposed to be supported by iscan however I have never been able to get it to work

---

### Post by reclusivemonkey on 2007-05-12
Have you tried this link?

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

---

### Post by DoctorMO on 2007-05-12
I wish SANE would get it's act together. we need serious focus on scanning and printing (gutten-print) projects and I'm always hopeful that Ubuntu devs will pour some love into them (or just fork them).

---

### Post by bren21 on 2007-05-12
> **reclusivemonkey said:**
> Have you tried this link?

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

Yep, haven't been able to get it to work.

---

### Post by Extreme Coder on 2007-05-12
Did you try using Kooka?(it comes with KDE) Sometimes my scanner wouldn't work on XSane, but would work just fine on Kooka.

Extreme Coder

---

### Post by diacos on 2007-06-27
Well, i have an Epson V350, and followed emperors advice posted [here]("http://ubuntuforums.org/showthread.php?t=20992&highlight=epson+perfection+v350")
I've noticed some strange symptoms:
iscan colapses when scan option is clicked, preview works ok
Scanner can't be seen by xsane as user, works ok as root user
(sudo xsane) I have no idea why does this happen.

---

### Post by julian.coccia on 2009-03-04
> **diacos said:**
> Well, i have an Epson V350, and followed emperors advice posted [here]("http://ubuntuforums.org/showthread.php?t=20992&highlight=epson+perfection+v350")
I've noticed some strange symptoms:
iscan colapses when scan option is clicked, preview works ok
Scanner can't be seen by xsane as user, works ok as root user
(sudo xsane) I have no idea why does this happen.


Hi, the V350 does not work with xsane. You need to install iscan and live with it :/

---


---
title: "Install goes fine on laptop, but not on desktop"
date: 2012-04-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Cecil on 2012-04-22
First off, some system specs:

Intel DZ68BC Motherboard
Core i5 2400
8GB Corsair Vengeance (passed memtest)
2x Geforce GTX 560 1GB

Basically, Ubuntu 12.04 beta 2 installed fine on my laptop, and is working great. However, when I attempted to install on the above desktop, it loads into a black screen with a blinking cursor in the upper left corner. It'll read the CD for a while, then just sit there, never progressing past this black screen. I then tried installing it inside Windows using WUBI, but same thing, upon rebooting it gives me the message that installation will continue, but then stop at a blinking cursor below the message, never progressing beyond that screen.

---

### Post by Quackers on 2012-04-22
It may be because of 2 x graphics card. Try disabling one temporarily.

Maybe try nomodeset first
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Cecil on 2012-04-23
Using nomodeset worked, thanks! :)

---

### Post by Quackers on 2012-04-23
Excellent! 
Happy Ubuntuing :-)

---


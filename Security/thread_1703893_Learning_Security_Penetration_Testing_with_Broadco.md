---
title: "Learning Security Penetration Testing with Broadcom Driver"
date: 2011-03-09
forum: Security
---

### Post by duvalfan25 on 2011-03-09
I am somewhat new to Ubuntu and Linux. I have used Linux before but only for a few trivial tasks that I was taught how to do for my work a few years ago. However, I am trying to learn penetration testing/detection at home to get a head start for my computer engineering degree I am currently pursuing. I just download Wubi installer for windows and am trying to learn what people call "hacking" computer stuff. But Ive read that a lot of the penetration testing tools for Linux do not work well or at all with a Broadcom wireless driver. I have a Broadcom 43xx driver. Is this correct? If so, what is the best thing I can do to fix this issue without buying a new computer? Thanks!

---

### Post by skraps on 2011-03-09
There are mods for the RaLink drivers, some of the best cards are the atheros, ornico, prism2 based chipsets. Im actually playing with kismet, air-ng tools set(google aircrack-ng), iw etc at this moment.

Im playing with  a tew-424ub has a rt chipset(20$ adapter), right now, suposodly it can do the injection but not prmisousmode, but i was reading at one point that there is some modified kernel drivers capable of sniffing.

---

### Post by cariboo on 2011-03-09
I'd suggest you have a look at [Backtrack]("http://www.backtrack-linux.org/"), there many howto's available, and you can install it on a usb device.

---

### Post by wojox on 2011-03-09
I use bcm4312 on a laptop and needed to purge the repo's driver and download the b43 from the linux-wireless site and patch it. 

You should also consider dual booting. Especially if your going to become a computer engineer. :P

---


---
title: "Forgot administrative password"
date: 2009-07-20
forum: Security
---

### Post by Xeginy on 2009-07-20
I bought this computer a few weeks ago, and was never told the administrative password.  By the time I found out I needed one to download updates and install software, the person I had bought the computer from had vanished and I haven't been able to get a hold of him.  Does anybody know how to change/reset the administrative password?  I have Ubuntu 8.1 running right now.  I can't change it in Grub; I've already tried.  Does anyone know of any other way around this?  I would really like to be able to get the most out of this computer.

---

### Post by lisati on 2009-07-20
The administrative password in Ubuntu is usually the same as the one you use to log in with. Feel free to let us know if that helps (or not, as the case may be)

---

### Post by aysiu on 2009-07-20
> I can't change it in Grub; I've already tried. Can you be more specific?

What exact steps did you take and what error messages or behavior did you get in return?

---

### Post by Xeginy on 2009-07-20
Yeah, when I looked the Timeout is set to 0, so I can't make any changes.  And I can't change the Timeout number since I don't have the administrative password, so... you see my dilemma.

The most common bit of advice I've gotten is to install a fresh copy of Ubuntu 9.04, which is fine, since I have an external CD drive and a copy of the CD, but when I boot up my computer with the CD in the drive, it doesn't do anything except recognize the CD is there and then just goes to my normal desktop page.  When I try to open the CD, it tells me that I need an administrative password.  Am I trying to install it the wrong way or something?

---

### Post by aysiu on 2009-07-20
Boot up a live CD.

Mount the Ubuntu installation with it (just go to Places and select the drive and it'll be automatically mounted).

Instead of just browsing straight there, though, press Alt-F2 and type ```
gksudo nautilus
``` Then go to the mounted partition and modify the Grub menu.

It'll probably be /media/disk/boot/grub/menu.lst

It's just a text file. You can then change that from *timeout 0* to *timeout 10*.

Reboot without the live CD and you can enter recovery mode.

---


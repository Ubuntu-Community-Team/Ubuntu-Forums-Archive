---
title: "Plymouth actually working for anyone?"
date: 2010-04-07
forum: The Cafe
---

### Post by chris4585 on 2010-04-07
Yes, well I've installed the 10.04 lucid beta on my laptop which has an nvidia card and on a desktop which has a ati card, neither of them have actually worked with plymouth as of yet.  Just wondering out of those testing the beta, does plymouth work for you?

---

### Post by NightwishFan on 2010-04-07
This thread might be right up your alley:
[http://ubuntuforums.org/showthread.php?t=1416872](http://ubuntuforums.org/showthread.php?t=1416872)

---

### Post by shazbut on 2010-04-07
3 Machines:
Nvidia GF4-4200: Noveau driver: works / Nvidia driver: doesn't work
ATI x300: radeonhd driver: works / fglrx: not available
Intel GMA4500: Works, boots a bit quick to see much though.

---

### Post by Dobbie03 on 2010-04-07
No probs at all, just had to edit the resoloution.

---

### Post by chris4585 on 2010-04-07
> **NightwishFan said:**
> This thread might be right up your alley:
[http://ubuntuforums.org/showthread.php?t=1416872](http://ubuntuforums.org/showthread.php?t=1416872)

Thats a pretty large thread, I guess I will have something to do tomorrow.  

Thanks

---

### Post by tica vun on 2010-04-07
It works on my server and netbook (both with intel GMA 450), but doesn't on my desktop with an nvidia Geforce 8800 GTS 512 and v190 nonfree drivers.

---

### Post by Dobbie03 on 2010-04-07
On my other PC tp get plymouth to work with nvidia drivers I just followed the instructions here:

[http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html#more](http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html#more)

---

### Post by 3rdalbum on 2010-04-07
The nice Plymouth works on my Intel-based netbook and my Nvidia-based desktop with Nouveau. I get an uglier Plymouth when I use the proprietary Nvidia driver and the Nouveau driver is blacklisted.

In theory you could have Nouveau driving the nice Plymouth, and then Nvidia driving the display after that, for the best of both worlds. But Nouveau needs to be blacklisted in order to manually install the Nvidia driver.

---

### Post by bash on 2010-04-07
Wouldn't this thread be better suited in the Lucid Testing Forum than in the Community Cafe?

---

### Post by iRiUX on 2010-04-07
Doesn't work on mine at all, Kubuntu 10.4, ATI 4570, open-source drivers. Isn't it getting late for this? Will they manage to fix this within three weeks and also finish their other work?

---

### Post by Chromagnum on 2010-04-07
**Nvidia FX5500:**

-Plymouth works but video playback 720p stutering, using Totem, VLC and XBMC. (Nouveau enabled, restricted driver deactivated)

-Restricted driver works but ugly splash screen and Unable to load X Server Display Page. But, screen resolution is perfect and smooth video playback 720p.

---

### Post by andamaru on 2010-04-07
I've only tested it on my quadro fx 3500, but when I used it on fedora it worked with my geforce go 6100 and the intel graphics card in my aspire one

---

### Post by phrostbyte on 2010-04-07
It doesn't work with Nvidia or ATI proprietary drivers because they do not support Kernel-mode setting. However, you should still see a splash screen, just one that is significantly uglier.

---

### Post by Psumi on 2010-04-07
I get this instead: [http://ubuntuforums.org/showthread.php?t=1407091](http://ubuntuforums.org/showthread.php?t=1407091)

---

### Post by chris4585 on 2010-04-07
Perhaps a moderator could move this thread to the appropriate place.  Thanks everyone for the input.

I'm not going to attempt to fix the issue, I'm going to see if the updates will fix it.  It seems the proprietary and the nvidia drivers from the repositories don't work as well as the Nouveau drivers.  I don't know about the ATi front end.

---


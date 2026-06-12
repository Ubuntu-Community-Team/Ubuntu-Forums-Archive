---
title: "How many times have you broken X-server, how did you do that, and how did you fix it?"
date: 2007-10-24
forum: The Cafe
---

### Post by PmDematagoda on 2007-10-24
As the title suggests, this thread is to find out how many times people have broken their GUI's, how they did it and how they solved it.

So, to start out, I will begin.

I broke my X-server 3 times on Feisty.

Once was when I installed VMWare using Automatix, I fixed it just by removing it, may this be a lesson for me to never use Automatix.

The second time was when I was messing with my OS too much and I deleted a few crucial files. I fixed them by just installing them again.

The third time is a complete mystery:), but I solved it by installing the Nvidia drivers again and reconfiguring X, I think the problem came up because of the second time I broke X.

That is it(For now;)). I am planning on breaking it again as fast as possible:) as I now have Gutsy to act as the "Stable" system which will probably save the day when my poor old 7.04 installation breaks out of exhaustion:D.

---

### Post by hessiess on 2007-10-24
once when i was new to linux

---

### Post by Sunflower1970 on 2007-10-24
Recently:
Had trouble with the 2.6.20-16 kernel with Feisty...no matter how many different ways I tried to fix it would work, ended up reinstalling, and staying with 2.6.20-15 on one computer...

Under Edgy, I broke it so many different ways and fixed it so many different ways I can't even remember them all

---

### Post by muecker on 2007-10-24
Running a Thinkpad T60 with ATI X300 video.  Upgrading to Gutsy I could not get X to come up with the xorg.conf I had used for the last year with Dapper, Edgy and Feisty.  I tried many different things and was able to get dual screens working with Xinerama, but that was not a good solution.  I then tried to upgrad to ATI's 8.40.4 driver and that made things much worse.  Now I could not get X to work even when I reverted back to the 8.37.1 version provided by Gutsy.

Yesterday ATI released the 8.42.3 driver and it works great in Gutsy (at least for me).  The only thing I have found missing is the libGL.so.1 so I symlinked to libGL.so.1.2, which is a Mesa driver.  It works but it not up to the full performance.

---

### Post by Paul820 on 2007-10-24
Never. If my computer is working, as it has been perfectly with feisty and gutsy, then i don't mess with anything. :)

---

### Post by PartisanEntity on 2007-10-24
I must have broken it at least 10 times when I started using Ubuntu, Dapper was the version I was using back then :)

---

### Post by Bannor on 2007-10-24
lets see 5+

first install nvidia card wouldn't work, then I finnally got the driver and fixed it, but then I filled up all the space on the computer and needed to reinstal.  Of course by theat time I forgot how to add the driver.  So I just pulled the card and used the onboard card.  but when I upgraded to Gutsy I added it back in because gutsy has the drivers, but since I installed gutsy with the onboard card it didnt' install the right drivers so I tryied a complete reinstall ... that did go so wel.

then of coarse their is my nvidia laptop I had better luck with that since I used gutsy right away and the vesa driver worked until I could get around to installing nvidia

---

### Post by infoseeker on 2007-10-24
Don't remember exactly, but it was switching from a 'generic' kernel to a '386' kernel, or something similar.  Was some time back (Feisty days).

---

### Post by EdThaSlayer on 2007-10-24
I have broken it quite a few times. Most of the time it was through using the proprietary ATI drivers, but a dpkg-reconfigure fixes that. Other times it was because of the installation of a certain important program.

---

### Post by angkor on 2007-10-24
5+

Back in the days it used to be broken every other day :D Usually it was fixed by 

a)removing the nvidia drivers
b)reinstalling the nvidia drivers
c)dpkg-reconfiguring the xserver
d)messing in the xorg.conf
e) a strange and random combination of the above

Those were the days *sighs* Nowadays I only need to reinstall the drivers after a kernel upgrade. Not much trouble anymore

---

### Post by Crashmaxx on 2007-10-24
I've lost count, but most of them were on breezy and from trying to install compiz. Haven't had a single issue for a long time now.

---

### Post by FuturePilot on 2007-10-24
I haven't broken it anytime recently. But when I first started with Ubuntu I must have broken it like 20 times.

---

### Post by tenmillionmilesaway on 2007-10-24
Loads and Loads, but not since Edgy im liking the stability of the newer releases :)

---

### Post by Scruffynerf on 2007-10-24
> **angkor said:**
> 5+

Back in the days it used to be broken every other day :D Usually it was fixed by 

a)removing the nvidia drivers
b)reinstalling the nvidia drivers
c)dpkg-reconfiguring the xserver
d)messing in the xorg.conf
e) a strange and random combination of the above

Those were the days *sighs* Nowadays I only need to reinstall the drivers after a kernel upgrade. Not much trouble anymore

Exactly my experience. Biggest pet peeve. So much so, I've a sticky note with the dpkg voodoo stuck on the side of my compouter. It was horrible, horrible with Edgy, Feisty was much better, not tried Gutsy, I'm just going to wait for Heron.

---

### Post by -grubby on 2007-10-24
never. I don't fix anything if its not broken

---


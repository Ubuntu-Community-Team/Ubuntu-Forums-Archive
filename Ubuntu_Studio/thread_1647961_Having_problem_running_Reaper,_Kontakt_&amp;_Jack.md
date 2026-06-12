---
title: "Having problem running Reaper, Kontakt &amp; Jack"
date: 2010-12-18
forum: Ubuntu Studio
---

### Post by moebek on 2010-12-18
Hi guys, 

I have Ubuntu Desktop 10.10 32 bit version. I have installed wineasio and registered it, jack, Reaper and Kontakt. 

All the softwares run properly with no error but I do not get any sound. Read through threads and articles (including davehayes reaper guide) but was not successful.

Can you guys kindly help me out here? I am still new to Ubuntu.

My sound card is Creative Xtremegamer. If you need me to post any information to help setup, just guide me and I will be willing to do so. 

Thanks

---

### Post by Pablo_F on 2010-12-18
Hi, 

Yes, we need some info on your hard-soft audio configuration. Run this in a terminal, upload the output to alsa-project and give us the URL:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Also, tell us the jackd command you are using. In a terminal:

cat ~/.jackdrc


Cheers, Pablo

---

### Post by moebek on 2010-12-18
> **Pablo_F said:**
> Hi, 

Yes, we need some info on your hard-soft audio configuration. Run this in a terminal, upload the output to alsa-project and give us the URL:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Also, tell us the jackd command you are using. In a terminal:

cat ~/.jackdrc


Cheers, Pablo

Ok here it is:

Alsa : [http://www.alsa-project.org/db/?f=7e8194032f1699c7d4d1df69b28cc20b08d6d632](http://www.alsa-project.org/db/?f=7e8194032f1699c7d4d1df69b28cc20b08d6d632)

Jack : /usr/bin/jackd -m -dalsa -dhw:0 -r48000 -p64 -n3

---

### Post by Pablo_F on 2010-12-18
Hi,

1. First of all, if you have the time check jackaudio.org thoroughly but do not try to understand it all at a glance.

2. I know this is not an obvious thing to do but it is strongly recommended that you should use card names instead of card numbers in the jack setup. You only have to enter "hw:XFi" instead of "hw:0" in the "interface" field. (alternative: see 5.). You cannot see this trick in the drop down menu so you have to write it down (without the quotes). Alsa card numbers not consistent out of the box is a cause of fustration in new jack users. Fix the problem by naming by name. 

3. Then, **if you are not using** the **onboard** card at all, **disable it in the BIOS**. Computers tend to overuse the things they see. 

4. However, at the moment you posted you had hw:0 as an interface in the jack setup, which was the xfi card but not jackd running. I think it should be fine if you had started jack, as long as you are using the right 1/8" physical jack output, which normally should be the green one. You know you can use alsamixer, right?  Check it anyway.

5. You also can use different devices for capture and playback, even with the same card. 

6. Another thing, sorry for editing again. You are pushing jack way too much for starters. 2 periods per buffer is the normal thing. 3 is rarely needed with a PCI card, afaik. Then you are overdoing with 64 frames per period. This is very low latency, unnecesarily low for any use (related to music) that I can imagine. Increase it a lot. Don't get fooled by latency numbers and trust your ears above your eyes.

Cheers, Pablo

---

### Post by moebek on 2010-12-18
Changed device name as you said, and pushed up the frame rate to 256. 

IT WORKED!!

Thank you so much Pablo :p

---


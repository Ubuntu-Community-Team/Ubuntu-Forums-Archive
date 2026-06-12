---
title: "Any progress with Realtek drivers for wireless?"
date: 2013-04-12
forum: Ubuntu Development Version
---

### Post by tjeremiah on 2013-04-12
A couple of weeks ago I installed 13.04 to test it out on my machine. When logging in my wireless wouldnt connect to any wireless network. The problem is that after every kernel update or fresh install I would have to install the right drivers for my wireless adapter. With the new kernel presented in 13.04, I was unable to do so. The driver simply wouldn't compile. I installed the latest headers, build essentials, etc and it just wouldnt work. A user here had a similar problem. Also, I would always follow these instructions [http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/](http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/) and they have worked in 12.10. A couple of weeks have went by and I would like to know if for those who had trouble with Realtek wireless drivers in the past with 13.04, I would like to know if those issues have been resolved by now.

---

### Post by kurt18947 on 2013-04-12
Nothing from RealTek AFAIK.  There is a fix in the last post of this thread:

[http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs](http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs)

I haven't tried that fix.  I suspect RealTek will release an updated driver around or after 13.04's release date.  I saw something about an  effort to fix the driver in the mainline kernel but I don't have a link.

---

### Post by ronacc on 2013-04-12
I have a realtek 8185 chipset in my test box and no problems with it .

---

### Post by ppjdee on 2013-04-12
I know mine currently does not work. But I haven't tried any fixes for it yet either. Just waiting on them to release a new driver.

---

### Post by tjeremiah on 2013-04-16
> **ronacc said:**
> I have a realtek 8185 chipset in my test box and no problems with it .

with Kernel 3.8?

---

### Post by jjhiza on 2013-04-18
Hey guys, I'm new to the forums, but this thread caught my eye. I purchased a Toshiba L855-S5273 laptop back in December, with the following specs:

Processor - Intel® Core™ i7-3630QM CPU @ 2.40GHz × 8
Graphics - Intel® Ivybridge Mobile
Memory - 6GiB
OS Type - 64 bit

I'm only posting my specs to serve as a barometer for some of you who are having issues with Wi-Fi; My laptop has the Realtek 8188ce drivers, and Ubuntu is the ONLY distro that my Wi-Fi works on right out of the box (including the live CD/DVD). To date, I've tried Linux Mint 14.1, Debian 7, openSUSE 12.3, and Linux Mint Debian Edition, and none of them will recognize my router. Ubuntu 12.04, 12.10, and now 13.04 have ALL worked perfectly on my hardware, and have done so immediately. The only issue I have with 13.04 is the fact that Cinnamon doesn't work 100% (Cinnamon Settings won't open), but wireless has been fine. 

Hopefully, any of you who have a setup similar to mine, can have the kind of success I've had with Ubuntu, and just maybe, my success with an installation, using Realtek drivers will encourage someone to take the plunge.

---

### Post by Rukiri on 2013-04-18
What wireless adapter do you have? If it's the AE1000 it should work out of the box, but AE3000 you need to compile the driver.

---

### Post by tjeremiah on 2013-04-24
as of today I still cant find a solution. This is with current updated 13.04. Google searching does nothing to help me. Hopefully tomorrow a solution will pop up.

---

### Post by tjeremiah on 2013-04-27
SOLVED with this post. [http://ubuntuforums.org/showthread.php?t=2092934&p=12621449#post12621449](http://ubuntuforums.org/showthread.php?t=2092934&p=12621449#post12621449)

---

### Post by marcinlos on 2013-04-28
Well, in my case (8188ce) it was enough to remove __devinit/__devinitdata stuff (removed in linux 3.8) to get it to compile. Hopefully I haven't broken anything badly. I definitely cannot reccomend this approach, but it seems to work for me, for now at least.

---

### Post by artjermyn on 2013-05-01
marcilos,
what exactly did you remove and from where?

---


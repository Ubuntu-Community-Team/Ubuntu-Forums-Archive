---
title: "Windows 7 cannot Install, 'missing driver...' - Gazp9"
date: 2013-08-08
forum: System76 Support
---

### Post by Steven Bell on 2013-08-08
I have the Gazp9,


Whenever I try to install Windows 7, and click "Install Windows" it immediately displays 'that the dvd driver is missing and asking me to browse for it'


How do I Install Windows 7 please?


P.s. Installing via USB and I don't have a DVD drive.

---

### Post by prodigy_ on 2013-08-08
This is probably caused by SATA configuration in BIOS. If your SATA ports are in RAID or ACHI mode, you might need to download additional drivers from your motherboard vendor website and put them on a USB stick (or make your own Win 7 installation DVD with those drivers integrated).

Alternatively you can change BIOS configuration (switch the SATA port your DVD drive connected to to IDE mode).

---

### Post by isantop on 2013-08-08
This almost sounds like a faulty installation medium. How did you create a bootable flash drive from the Windows ISO?

---

### Post by Steven Bell on 2013-08-08
I'll go and check it, 

maybe because I used 'k3b' and 'winusb' application via ubuntu (I may have probably done something silly), I have now downloaded the Microsoft Windows 7 USB program via Windows, and will give that a try... And will let you know :)...

---

### Post by isantop on 2013-08-08
Windows ISOs are very different from Linux ISOs, and have to be written differently from them if you're writing to USB.

---

### Post by Steven Bell on 2013-08-08
I just noticed that my username has been changed to my full name and I cannot change it back, have already notified support...??? OMG!

---

### Post by QIII on 2013-08-08
Hello!

With regard to your username, please start a thread in the Resolution Centre and the Admins will help you sort it out.

---

### Post by Steven Bell on 2013-08-08
Yes you're right, I have already done so, thanks (through support at the ubuntu one site)... I think I rushed the new ubuntu re-login phase...

---

### Post by Steven Bell on 2013-08-09
Success!!!

My media was of course the problem (phew), windows installed just fine :D (multiboot).

How I solved this kind of problem you wonder, [http://wintoflash.com/home/en/](http://wintoflash.com/home/en/), I used this freeware on windows, (it comes with spam software, bars and advertisements) they deserve a donation!

Unetbootin, winusb etc. did'nt do it, and so many other programs I tried, I am indeed impressed with this software, very different approach, they only needed the windows files and not necessarily the image, works with scratched media, lol...

---

### Post by jaime3 on 2013-08-18
> **Steven Bell said:**
> Success!!!

My media was of course the problem (phew), windows installed just fine :D (multiboot).

How I solved this kind of problem you wonder, [http://wintoflash.com/home/en/](http://wintoflash.com/home/en/), I used this freeware on windows, (it comes with spam software, bars and advertisements) they deserve a donation!

Unetbootin, winusb etc. did'nt do it, and so many other programs I tried, I am indeed impressed with this software, very different approach, they only needed the windows files and not necessarily the image, works with scratched media, lol...


Did Window 7 detected all you're hard drive? I am thinking about getting this laptop that you have. How does it run Window 7 vs ur Linux os? I have a Acer and Ubuntu is slower then Window and Ubuntu slower then Window 7. Ty

---

### Post by Steven Bell on 2013-08-22
> **jaime3 said:**
> Did Window 7 detected all you're hard drive? I am thinking about getting this laptop that you have. How does it run Window 7 vs ur Linux os? I have a Acer and Ubuntu is slower then Window and Ubuntu slower then Window 7. Ty

It detected all drives perfectly...

It runs Windows 7 and all others OS's the old fashioned traditional way, in other words PERFECTLY!!!

When it starts you can enter, BIOS setup OR choose to boot from the other devices...

Both Windows and Linux ran at the exact same flawless speeds, both booted within seconds, both in my mind ran without any feeling of hesitation, as if the notebook was designed for both worlds.

I multibooted with Windows 7, Kubuntu 13.04 and ubuntu 13.04 and the drivers supplied work perfectly well!

I would recommend this notebook to you...

The problem I had was a 'me' problem, because my Windows 7 media was not in perfect original working order...

I got the IPS Matte screen, and its worth it!

I'm not a big fan of unity and I normally think it's ugly and bulky, BUT on a screen this size and high resolution, it actually looks pretty spectacular and not bulky at all as it normally appears that I've found on lower resolutions.

:)

---

### Post by jaime3 on 2013-08-23
> **Steven Bell said:**
> It detected all drives perfectly...

It runs Windows 7 and all others OS's the old fashioned traditional way, in other words PERFECTLY!!!

When it starts you can enter, BIOS setup OR choose to boot from the other devices...

Both Windows and Linux ran at the exact same flawless speeds, both booted within seconds, both in my mind ran without any feeling of hesitation, as if the notebook was designed for both worlds.

I multibooted with Windows 7, Kubuntu 13.04 and ubuntu 13.04 and the drivers supplied work perfectly well!

I would recommend this notebook to you...

The problem I had was a 'me' problem, because my Windows 7 media was not in perfect original working order...

I got the IPS Matte screen, and its worth it!

I'm not a big fan of unity and I normally think it's ugly and bulky, BUT on a screen this size and high resolution, it actually looks pretty spectacular and not bulky at all as it normally appears that I've found on lower resolutions.

:)


Do you play Urban Terror? If so what is the FPS under Linux?

---

### Post by Steven Bell on 2013-08-23
I don't play that game, actually I've never played any game's since Amiga (like 20+ years), BUT I got 10 of the latest games for windows 7 to try,
I bought only 4gb of ram, and most games seemed fine on 'normal' and low settings, and only a few on very high, very mixed performance for me
BUT THIS IS NO WAY OF REVIEW QUALITY - I did read online that games ran well set on low for HD graphics in the past, but I believe this one is better than it predecessors 
Because I am no way a gamer, and obviously to me I have absolutely no experience in knowing what to look for.

It think I will have to get an external mouse, and wondering if people play games fine on a touchpad?
Not bad to me as this was just going to be a workstation in the beginning,
Price wise, it's a real bargain for my uses.
For games Il'd love the Bonobo Extreme of course :)

Hope someone else who does play games can comment on this gazp9 model...

---

### Post by jaime3 on 2013-08-24
> **Steven Bell said:**
> I don't play that game, actually I've never played any game's since Amiga (like 20+ years), BUT I got 10 of the latest games for windows 7 to try,
I bought only 4gb of ram, and most games seemed fine on 'normal' and low settings, and only a few on very high, very mixed performance for me
BUT THIS IS NO WAY OF REVIEW QUALITY - I did read online that games ran well set on low for HD graphics in the past, but I believe this one is better than it predecessors 
Because I am no way a gamer, and obviously to me I have absolutely no experience in knowing what to look for.

It think I will have to get an external mouse, and wondering if people play games fine on a touchpad?
Not bad to me as this was just going to be a workstation in the beginning,
Price wise, it's a real bargain for my uses.
For games Il'd love the Bonobo Extreme of course :)

Hope someone else who does play games can comment on this gazp9 model...

LOL yea that Bonobo Extreme is crazy laptop have you seen the powersupply? It's huge like crazy huge. Anyway's thanks for you're opinion. Ever did VM on you're laptop under linux? How it run? Oh but you only have 4gb of
ram well its very possible to run VM. Give us more information when you run latest games. I want really to stay with one os which Ubuntu on this laptop that you have and use virtual box or vmware and run probably xp and Window 8 in it for program that cant run on wine. I wont worry much about games but would like that able to play Urban terror and other open source on the lappy without running dual boot. Frame per second is higher on Windows. But I'm tired of Windows due to security. But I doubt I can sneak away without using Window. Window just work perfect. Oh how high can u go on youtube without video lag? Ty

---


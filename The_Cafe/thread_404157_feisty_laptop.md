---
title: "feisty laptop"
date: 2007-04-08
forum: The Cafe
---

### Post by ufonpu on 2007-04-08
Could Feisty for laptop be downloaded on Apr 19?
Which aspects does it improved for laptops?
I have a lot of problems in Engy such as screen resolution, wireless card ,refresh rate etc.  Even I did just like others told in the forums but only a few of them solved.
HOPING FOR FEISTY SUPPORTING MY NOTEBOOK!!!

---

### Post by tscook on 2007-04-08
I am replying from a Feisty laptop that is working absolutely perfectly.:popcorn: :guitar: :lolflag:

---

### Post by kombinator on 2007-04-08
Feisty fixed a ridiculous number of problems with my Toshiba.  I'm anxious to see if the final release does anything above and beyond that.

Either way, for me Feisty is amazing and Edgy was an amazing pain. :lolflag:  :popcorn:

---

### Post by SishGupta on 2007-04-08
my thinkpad t42 is supported perfectly for the first time in feisty.

I havent tried svideo out though, which i think may be the only thing that still doesnt work..

maybe ill try right now.

---

### Post by MeneM on 2007-04-08
Thinkpad T43 here, totally happy with it.

Perfect productivity tool with Ubuntu!

---

### Post by Hallvor on 2007-04-08
Xubuntu Feisty on an Acer Travelmate 2310. Solved many problems, especially the wifi. Works perfectly.

---

### Post by girishv on 2007-04-08
Hi,

S video worked perfectly on my thinkpad Z60. The only problem is restarting the X :)

girish

---

### Post by ufonpu on 2007-04-08
Hello!
   I think that showing our device lists will be more helpful to others.
   A list of your CPU, motherboard, video card, wireless card is enough.

MINE
  AMD Turion TL-52 1.6GHz
  nVIDIA c51
  nVIDIA GeForce Go 6150
  BCM 4311 /802.11a/b/g

---

### Post by Gargamella on 2007-04-08
what about boot time? It isn't very long here in Edgy, but my WinXP is faster ;(

---

### Post by bionicyeti on 2007-04-08
I was running Edgy on a Dell D520 and the only issues I had were with my Broadcom Wireless drivers. I just finished the upgrade to Feisty and the only problem I had was with the Broadcom Wireless drivers. :(

The fix was the same for both.

---

### Post by PartisanEntity on 2007-04-08
does feisty have native support for wpa encrypted wifi networks yet?

---

### Post by mech7 on 2007-04-08
WPA works for me fine instantly..

---

### Post by Koori23 on 2007-04-08
I'm running Feisty on a Toshiba Satellite Pro A105.. Wireless/touchpad.. Everything works great.

---

### Post by PartisanEntity on 2007-04-08
> **mech7 said:**
> WPA works for me fine instantly..

sorry just to clarify, we are talking about wpa-psk right? so they included wpa-supplicant and network manager in feisty?

---

### Post by helliewm on 2007-04-08
Works perfectly on a Packard Bell C3300. Although I did upgrade the RAM from 286mb to 1 GIG and Hard Disk from 40 Gig to 120 gig some time ago. Not that the Hard Disk makes any difference.

Helen

---

### Post by mikeoh on 2007-04-08
On a Acer Travelmate 2304 everything works except frequency scaling of the CPU.  This was working in Edgy but the speedstep-centrino module is no longer built with the default kernel in Feisty and the acpi-cpufreq module that replaces does not work for me. 

Apart from this everything else works just fine including wifi.

---

### Post by ronniet on 2007-04-08
Got **Xubuntu** Feisty (final beta) on my Compaq nx9005, works fine, even with my Cable & Wireless wifi card!  :D

---

### Post by macogw on 2007-04-08
> **bionicyeti said:**
> I was running Edgy on a Dell D520 and the only issues I had were with my Broadcom Wireless drivers. I just finished the upgrade to Feisty and the only problem I had was with the Broadcom Wireless drivers. :(

The fix was the same for both.

I thought bcm43xx was supposed to be installed by default and then you just needed to apt-get install bcm43xx-fwcutter to extract the firmware for the card.  Am I wrong about that?


WPA has always worked with a bit of fiddling.  I don't think wpa-supplicant used to be installed by default, but in a bug report I recently saw someone surprised that wpa started working after blanking the /etc/network/interfaces (it was being blanked as a workaround for something else), but that's how I've always seen it said to do in howtos.  That's just kinda how you make wpa control go to network-manager, I guess.  It's worked for me since Dapper.  So, if you can't get WPA working with network-manager, comment out everything in that file except for the lines referring to lo

---

### Post by FuturePilot on 2007-04-08
Beryl/Compiz hates my GeForce 2 Go:(

---

### Post by darkhatter on 2007-04-08
feisty doesn't load on my laptop it just crashes :sad:

I haven't tried the beta so things may be differerent

Gateway mx3410

---

### Post by teet on 2007-04-08
> **macogw said:**
> I thought bcm43xx was supposed to be installed by default and then you just needed to apt-get install bcm43xx-fwcutter to extract the firmware for the card.  Am I wrong about that?


You are correct.  Although that's the way things have been since dapper drake (to my knowledge).

Hint:  Go into /lib/firmware and copy all of the files that begin with 'bcm43xx' to your /home directory (if it's on a separate partition) or to a flash drive or something.  Then when you do a clean install of feisty, all you have to do to get your wireless working is copy those files back to /lib/firmware.

This saves A TON of hassle (especially if you ONLY have a wireless connection and can't easily download fwcutter).  I have done this on my upgrade form dapper to edgy and then again from edgy to feisty.  It works.

-teet

---

### Post by bran on 2007-04-08
only a couple quibbles with the beta here on my Acer aspire 9400:  QuickCam comunicate does not work for me as it seems to for everyone else and I can not get the walpaper plugin to install in beryl

---

### Post by macogw on 2007-04-08
> **teet said:**
> You are correct.  Although that's the way things have been since dapper drake (to my knowledge).

Hint:  Go into /lib/firmware and copy all of the files that begin with 'bcm43xx' to your /home directory (if it's on a separate partition) or to a flash drive or something.  Then when you do a clean install of feisty, all you have to do to get your wireless working is copy those files back to /lib/firmware.

This saves A TON of hassle (especially if you ONLY have a wireless connection and can't easily download fwcutter).  I have done this on my upgrade form dapper to edgy and then again from edgy to feisty.  It works.

-teet
Well I doubt it's on my computer.  I have Intel wireless so I don't have to do any work at all :D

Why isn't Broadcom firmware in by default?  Intel firmware is binary blobs too, but it's included by default.

---

### Post by palmerthegeek on 2007-04-09
Were any of you fellow edgy to feisty users docking and undocking your laptops?  I have a couple of weird "issues" with my dell d610.

---

### Post by Nolander on 2007-04-15
hi all

ive ran dapper, edgy and feisty on my IBM thinkpad t21 and my sister t41. ive also installed feisty on a couple of acers and had no problems..... so far

Nolander

---

### Post by insane_alien on 2007-04-15
fixed some problems on my R50e that i didn't even realise i had till they were fixed :P

although, i did bork my windows partition installing it. that was my fault though, i picked the wrong disk to install to(i meant to install to an external disk)

---

### Post by Mathiasdm on 2007-04-15
> **macogw said:**
> Well I doubt it's on my computer.  I have Intel wireless so I don't have to do any work at all :D

Why isn't Broadcom firmware in by default?  Intel firmware is binary blobs too, but it's included by default.

Because Broadcom doesn't allow Ubuntu to distribute the firmware?
If they say it's not allowed... Then sadly, it's not allowed.

---


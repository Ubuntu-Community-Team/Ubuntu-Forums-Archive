---
title: "Did you have to mod your computer?"
date: 2006-10-04
forum: The Cafe
---

### Post by alecjw on 2006-10-04
Did you have to mod your computer at all to make Ubuntu work on it? Eg. Did you have to buy a more compatiable wirless card etc?

I didn't. Everything worked straight away (except my wireless card, which I neeeded bcm43xx-fwcutter for)

---

### Post by bigken on 2006-10-04
the only thing that does not work out of the box on my inspiron 9200 is the wifi led not a big issue :-D

---

### Post by Dinerty on 2006-10-04
> **bigken said:**
> the only thing that does not work out of the box on my inspiron 9200 is the wifi led not a big issue :-D

I'm on the 9300 and it does not work either, not really bothered though

---

### Post by bigken on 2006-10-04
> **Dinerty said:**
> I'm on the 9300 and it does not work either, not really bothered though

You can get it to work look[ here]("http://www.ubuntuforums.org/showthread.php?t=200017")

---

### Post by Kateikyoushi on 2006-10-04
Seems the X505 was designed for edgy, worked out of the box. ;)

---

### Post by aysiu on 2006-10-04
I hope this poll puts to rest the myth that "Linux isn't free because you have to replace *all* your Windows hardware with Linux-compatible hardware."

---

### Post by Anonii on 2006-10-04
Everything worked perfectly, except 5:1 surround <:

---

### Post by henriquemaia on 2006-10-04
Everything worked ok.

---

### Post by Lord Illidan on 2006-10-04
I just had to work a bit with drivers and stuff.

---

### Post by raublekick on 2006-10-04
> **Dinerty said:**
> I'm on the 9300 and it does not work either, not really bothered though

exact same problem on my 9300... but really isn't a big deal! the bluetooth light works fine though.

---

### Post by Dinerty on 2006-10-04
> **bigken said:**
> You can get it to work look[ here]("http://www.ubuntuforums.org/showthread.php?t=200017")

thank you indeed, I will do this tomorrow !

---

### Post by alecjw on 2006-10-04
> **aysiu said:**
> I hope this poll puts to rest the myth that "Linux isn't free because you have to replace *all* your Windows hardware with Linux-compatible hardware."

Yep. That's why I made this poll.

---

### Post by rfruth on 2006-10-04
It just worked (plug & pray in M$ speak)

---

### Post by PatrickMay16 on 2006-10-04
When I installed ubuntu on this machine, everything worked except 3D accelleration with my ATI Radeon 9000 which I had at the time. It was enabled, but the computer would lock up whenever I tried to use it; like when I was using a 3D screensaver or using Mupen64.

I since got an Nvidia card, but if anyone is interested here's the fix for the problem I had been having. I put this in the device section of the xorg.conf file:

Option "AGPMode" "4"

---

### Post by Polygon on 2006-10-04
with breezy my wireless card wouldent work. But then i got a new one and it worked perfectly. has worked fine ever since.

and same thing, my sound card didnt work in breezy out of the box, but in dapper it did.

im not counting installing video card drivers.

---

### Post by John.Michael.Kane on 2006-10-04
The rig i'm using was built for linux so no hardware issues. unless you count a defective mouse.

---

### Post by xXx 0wn3d xXx on 2006-10-04
Everything but my wifi card (Broadcom 4138) required me to extract the needed firmware plus the bcm43xx kernel module will only work with network-manager for me.

---

### Post by xinix on 2006-10-04
I researched all the parts I put into my ubuntu box before ordering them.  Everything pretty much worked as expected.  Suspend didn't for a while but in edgy it works just fine.

---

### Post by NetworkGuy on 2006-10-04
Had to change /etc/modprobe.d/options and add a line for the correct acx firmware for my wireless card.  Also had to tweak my xorg.conf to allow my ATI card to work better as well as setup my scrolling mouse and turn off the touchpad on my Thinkpad.

Other than that, no problems.

---

### Post by jimrz on 2006-10-05
everything on my homebuilt desktop worked out of the box on breezy + dapper + edgy (live cd only, so far)...same on my ThinkPad T42, except that it's ATI Radeon mobility 9600 128Mb vid card is not supported for hardware acceleration by any linux drivers that I have been able to find (and this is no big thing since I do not use that box for gaming and card runs the things I do use it for nicely whith the available drivers) and the wireless does not come up on edgy (but I'm told that it is only broken on the beta live cd and works on an installed edgy beta, still going to wait at least till the release candidate appears before doing full install).

---

### Post by DarkN00b on 2006-10-05
I had to install firmware for my usb wireless-b dongle and tweak my xorg.conf for my i855 graphics to get 3d acceleration.  Everything worked wonderfully "out of the box".

BTW, this kicks the crap outta WinXP. I had to download many drivers the last time I installed that monstrosity.

---

### Post by angkor on 2006-10-05
Only a little. I had to buy a specific (non-broadcom) bluetooth dongle to get my bt headset to work with skype and other messengers.

---

### Post by bukwirm on 2006-10-05
Everything worked except the modem, and I don't need it anyway.

---

### Post by Mathias-K on 2006-10-05
I had to install a PCI ethernet card to get internet access on my desktop, ASRock 939DualSATA2-based machine, because the onboard LAN chip would disable by connection from time to time.

---

### Post by argie on 2006-10-05
My internal modem didn't work OOB, but i don't use it so haven't tried fixing it.

The rest, I was on the internet in <25 mins from putting in CD including one reboot to write down the ip and dns settings from the old windows.

Only problem is no direct rendering with the via card, but that's not much of an issue.

---

### Post by Klaidas on 2006-10-05
> **aysiu said:**
> I hope this poll puts to rest the myth that "Linux isn't free because you have to replace *all* your Windows hardware with Linux-compatible hardware."

It might put up a myth "Linux supports existing hardware for free.. if your time has no value" :-D

I can smell the flames coming my way ;)

---

### Post by aysiu on 2006-10-05
> **Klaidas said:**
> It might put up a myth "Linux supports existing hardware for free.. if your time has no value" :-D

I can smell the flames coming my way ;)
But that's a different myth altogether that has nothing to do with hardware.

I generally agree with the sentiment, but I think the expression is poor. It's not that time has "no value." In fact, you do have to *invest* a lot of time to install and configure a non-native operating system (non-native to your Windows-preloaded computer, non-native to you who have probably used Windows for over a decade), but it is not that time has no value.

If you do have **no time** to spare, I wouldn't advise installing a Linux distro, though. Even if it detects all your hardware, you'll still have to learn how to do things in a different way.

It'd be like saying "Learn a foreign language only if your time has no value."

Yes, keep speaking your native language if you have no time to learn a second language, but...

---

### Post by beercz on 2006-10-05
Just ACPI and power management issue (it's not working correctly) on my HP Compaq nx7400 laptop.  Everything else is OK.

---

### Post by bonzodog on 2006-10-05
I built my AMD64 300+ for linux, so all the hardware attached to it Just Works. It's mostly Nvidia chipsets, with and AMD proc, and Nvidia GPU. The printer, likewise, was bought *after* checking hardware compatability - bought an Epson Stylus Photo R200.

---

### Post by machoo02 on 2006-10-05
I have a ThinkPad R52, and everything that I've tried and use regularly has worked great out of the box.

---

### Post by Compucore on 2006-10-05
Mne works fine on a old Aptiva over here with the exception of the PCI modem that is a soft modem. I normally prefer a true internal modems or external depending if there are any soaces keft inside the machine.

Compucore

---

### Post by ubuntu_demon on 2006-10-07
I voted no "everything worked for me". Everything which is important to me works.

My printer doesn't work perfectly but it works good enough (Canon S300).

My scanner (Canon D646U) doesn't work but I don't need it much and I'm going to spend some more time on it someday.

I had some small problem that Dapper recognized my /hda as /hde ("mounting root filesystem bug") but :
- it's fixed for Edgy
- I got a new SATA harddrive which is my primary harddrive of my P4. Dapper had no problems with it.

---

### Post by Omnios on 2006-10-07
Every thing worked right out of the box with my new monitor. Previosly I had a bad KDM monitor that needed tweeking.

---

### Post by Abstract on 2006-10-07
I had to buy a router, I don't know if that counts as a mod.

---

### Post by Old Pink on 2006-10-07
I needed bcm43xx-fwcutter, and am still unable to get my Lexmark printer/scanner working. :(

---

### Post by TeeAhr1 on 2006-10-09
I wouldn't say "have to" in the sense of needing to modify something to make it work, but "have to" in the sense of "I've got a problem and I can't stop!" ;)

---


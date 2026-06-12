---
title: "Constant Bsod Problem - Need Help"
date: 2009-01-24
forum: Windows
---

### Post by Royajm on 2009-01-24
Hi all! I hope that you can help me with my problem.
I just bought a new computer about a week ago and I started having these Bsod:s, both ingame (GTA4 and other) and on desktop.

My specs:
Mobo: Asus P5Q-E
Processor: Intel Core 2 Quad Q9550
Video card: Sapphire Radeon HD 4870 (1Gb)
RAM: 2x2Gb DDR2 Kingston HyperX CL7 (1066MhZ? 7-7-7-20?)
PSU: Chieftec APS-500S (500W)
OS: Windows XP Service Pack 3 (Finnish Edition)

These errors do vary almost every time. Usually they are something like: IRQL_LESS_OR_EQUAL, or something like PAGE_FAULT_IN_NONPAGE_AREA. Usually they include a driver or a filenime, which may cause the problem, but they do not always include it.
Me and my friend have troubleshooted this a few days already and we've tried the following:

1. Booting with only 1 RAM (tried in both channels.)
2. Attaching the PSU's 8pin connector (first it didn't reach, so I used the 4-pin connector, now since there's no difference I use the 4-pin.)
3. Reinstalling windows.
4. Installing newest drivers.
5. Downgrading the BIOS to the 0803 version (I read, that it would have better support for QXXXX-processors and have better RAM support too.)
6. Temperatures seem to be o.k.
7. Tried to adjust the RAM-clocks and latency from BIOS.
8. There doesn't seem to be any relevant information about this in the Event Viewer.
9. I haven't run the Memtest86+, but I did run the Windows Server 2008 memory diagnostic tool and it didn't find problems (I tried S2K8, because I heard that XP can't handle 4Gb of RAM that well.)
10. The sound drivers were quite tricky to install so that there would remain no conflicts, but I somewhat managed to do that.

Would a minidump help solving this? I can upload the few last ones if needed.

---

### Post by bgerlich on 2009-01-24
Probably caused by wrong ram voltage or timing settings, it's possible that autodetect in BIOS is not working well. Try setting it by hand.

Are you overclocking your CPU?

---

### Post by Royajm on 2009-01-24
> **bgerlich said:**
> Probably caused by wrong ram voltage or timing settings, it's possible that autodetect in BIOS is not working well. Try setting it by hand.

Are you overclocking your CPU?
Thanks for the quick reply. I already tried that though (section 7). I set the voltage to 2.0V, latency to 7-7-7-20 and clocks to 1066MhZ instead of AUTO. EDIT: And I'm not overclocking, other settings are as factory defaults except the memory.

---

### Post by bgerlich on 2009-01-24
Is this your ram? [http://www.valueram.com/datasheets/KHX8500AD2K2_4G.pdf](http://www.valueram.com/datasheets/KHX8500AD2K2_4G.pdf)

If so, have you tried setting the voltage to 1.85, or voltage to 1.80 and timings to 6-6-6-18 ?

If none of the settings work I would return the mobo as faulty on account, that it doesn't detect the ram settings properly.

---

### Post by Royajm on 2009-01-24
> **bgerlich said:**
> Is this your ram? [http://www.valueram.com/datasheets/KHX8500AD2K2_4G.pdf](http://www.valueram.com/datasheets/KHX8500AD2K2_4G.pdf)

If so, have you tried setting the voltage to 1.85, or voltage to 1.80 and timings to 6-6-6-18 ?

If none of the settings work I would return the mobo as faulty on account, that it doesn't detect the ram settings properly.

Yes, that's my RAM. And no, actually I've only tried AUTO settings and the ones I mentioned earlier. I'll try switching to those settings asap, thanks for helping. EDIT: o.k. Now I'm running on the 1.80 voltage and 6-6-6-18 latency, the BIOS jumped over 1.85, only 1.84 and 1.86 were allowed, so is it okay to use 1.86? Sorry I'm quite new to tweaking ram settings, so I don't know if 0.1V would matter. :p

---

### Post by YeOK on 2009-01-24
Make sure your bios is up to date. My current ASUS motherboard had RAM issues until fixed by an update (Only certain types of RAM though). 

One of those error messages could also point to a bad device driver, you should make sure they are updated too.

---

### Post by Royajm on 2009-01-24
> **YeOK said:**
> Make sure your bios is up to date. My current ASUS motherboard had RAM issues until fixed by an update (Only certain types of RAM though). 

One of those error messages could also point to a bad device driver, you should make sure they are updated too.

Hi and thanks for the reply. I'm quite sure that the drivers are the newest ones, though I wouldn't fully rely on it.. Is there some sort of a driver fetcher/downloader/locater of some kind that could recognize if I had old ones?

---

### Post by bgerlich on 2009-01-24
Well, the timings in the ram reference sheet are for 1.80 or somewere in between 1.85 and 2.00, so if the first value doesn't work or you want the timings to be a bit higher, experiment with a voltage settings from the 1.85 - 2.00 interval.

**EDIT:**
> **Royajm said:**
> Is there some sort of a driver fetcher/downloader/locater of some kind that could recognize if I had old ones?

Sorry, windows is not Ubuntu, it won't fetch newest drivers tested with a particular system version from a repository;)

---

### Post by Royajm on 2009-01-24
Haha I've noticed that :p Btw Ubuntu live-cd doesn't crash the system (at least on my short test period) And as a update, the 1.80 voltage and 6-6-6-18 settings still did bsod :( now trying with the 1.86 voltage..

---

### Post by tsali on 2009-01-24
> Sorry, windows is not Ubuntu, it won't fetch newest drivers tested with a particular system version from a repository


Actually, it will. Windows Update is a repo of sorts. I've had several driver updated this way.

---

### Post by bgerlich on 2009-01-24
> **tsali said:**
> Actually, it will. Windows Update is a repo of sorts. I've had several driver updated this way.

Can you add repos to Windows Update? That's what I meant :)

---

### Post by Royajm on 2009-01-24
A little update, no voltage or latency settings seemed to help. Still getting BSODs. I'm now running memtest86+ and waiting to see results. Any help is still welcome. EDIT: Okay this seems quite desperate, I got a bsod during XP Pro installation.. So I guess that means it's a hardware problem? I guess that I'll have to get myself a new... mobo?

EDIT2: New update.. Not given up just yet, I made a fresh XP install once again, installed all drivers straight from web, not from cd. I updated the BIOS to the newest one and I believe I've done something right since I got no BSOD's on my desktop in about an hour, but badaboom I did get one in Gta 4.. some error with ati3duag.dll dunno if it's the ati graphics or hdmi sound driver yet though..

EDIT3: I've ran memtest86+ for thirteen hours straight, from a ubuntu live cd. No errors whatsoever. Still getting bsods because of ati3duag.dll. I've removed the old graphic drivers and installed the new in safe mode many times and still nothing, tried both catalyst 8.9 (which came with the Sapphire) and with the newest one: 8.12. I don't really have a clue, please help me :p

---


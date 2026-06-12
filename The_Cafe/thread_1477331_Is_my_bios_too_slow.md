---
title: "Is my bios too slow?"
date: 2010-05-08
forum: The Cafe
---

### Post by dragos240 on 2010-05-08
It takes 15 to 20 seconds. Too slow for me. My netbook has a 5 second bios. It's faster than my disktop bios T_T.

---

### Post by swoll1980 on 2010-05-08
> **dragos240 said:**
> It takes 15 to 20 seconds. Too slow for me. My netbook has a 5 second bios. It's faster than my disktop bios T_T.

I hate my BIOS it's an award BIOS, and it takes about 15-20 seconds as well. It takes as long to get through the BIOS as it does to boot Ubuntu/Win 7

---

### Post by dragos240 on 2010-05-08
> **swoll1980 said:**
> I hate my BIOS it's an award BIOS, and it takes about 15-20 seconds as well. It takes as long to get through the BIOS as it does to boot Ubuntu/Win 7

Mine's an award bios too!

---

### Post by Ylon on 2010-05-08
Look after "quick boot" feature in bios's menu. It's not normal that modern bios take such time (probably is active the ram check)

---

### Post by swoll1980 on 2010-05-08
> **Ylon said:**
> Look after "quick boot" feature in bios's menu. It's not normal that modern bios take such time (probably is active the ram check)

I can't find any options on my BIOS for quick boot.

---

### Post by Ylon on 2010-05-08
> **swoll1980 said:**
> I can't find any options on my BIOS for quick boot.

What it do for taking such long time? It's just black screen or it does something?

---

### Post by CharlesA on 2010-05-08
I think most of the machines I have here get thru the BIOS in 5-10 seconds unless there is a problem.

I've got both Award and AMI BIOSes.

They are all set for quick boot. (aka no memory testing)

---

### Post by dragos240 on 2010-05-08
I want my bios to take 5 seconds or less. Can someone reccomend a good board. I will be building my second desktop computer at the end of 2010. My first was my server! I really want some good specs for my next computer, and lots of processing power. My current tower holds a max of 2 64 bit CPUs and a whopping 2gB of ram! I need a new tower. A Micro ATX board would be nice. What website is best for new computer parts?

---

### Post by tom66 on 2010-05-08
Rant: A modern BIOS shouldn't even take 5 seconds. All it needs to do is detect disks and load the 512 byte MBR (480 bytes of which is executed) into RAM... that should take a couple hundred milliseconds really. Other features such as network booting and hardware detection might slow it down but those should be optional extras. Memory hardly ever fails, and when it does, a quick memory test is unlikely to detect it (as it is often a single row or even a single bit that has failed), so why even bother with the memory test? So why are BIOSes so slow?

---

### Post by chriswyatt on 2010-05-08
Try turning off floppy disk (if there is an option and if you don't use it) and changing the boot order so that hard drive comes before floppy disk and CD-ROM drive.* Only problem with this is that you have to change it back if you want to boot from a CD.

I can imagine CD booting could slow it down a bit as it has to wait for the CD to spin-up.

---

### Post by sydbat on 2010-05-08
> **dragos240 said:**
> I want my bios to take 5 seconds or less. Can someone reccomend a good board. I will be building my second desktop computer at the end of 2010. My first was my server! I really want some good specs for my next computer, and lots of processing power. My current tower holds a max of 2 64 bit CPUs and a whopping 2gB of ram! I need a new tower. A Micro ATX board would be nice. **What website is best for new computer parts?**[http://www.memoryexpress.com/](http://www.memoryexpress.com/)

They ship everywhere.

---

### Post by CharlesA on 2010-05-08
> **sydbat said:**
> [http://www.memoryexpress.com/](http://www.memoryexpress.com/)

They ship everywhere.

Nice site. I use [http://www.newegg.com](http://www.newegg.com) and [http://www.amazon.com](http://www.amazon.com) mostly.

The two machines I haven't had any problems with that seem to boot up really quick are using Gigabyte mobos.

---

### Post by standingwave on 2010-05-08
Prompts me to set up RAID every time (even when I had only one drive) and I have to wait ten seconds for it to time out.

---

### Post by CharlesA on 2010-05-08
> **standingwave said:**
> Prompts me to set up RAID every time (even when I had only one drive) and I have to wait ten seconds for it to time out.

Should be able to disable that in the BIOS.

Change the setting from RAID to AHCI or IDE.

---

### Post by MechaMechanism on 2010-05-09
I think that BIOS that take a long time as a normal mode of operation are designed to give users time to read and hit the right key.  I have an HP computer with 4 separate key options and it takes quite a while to get past it on fast boot.  Just be glad you don't have a server or workstation computer.  Oh God, I remember one workstation I had with ECC Registered RAM plus RAID and golly gee must have took half a day to bring up.

---

### Post by standingwave on 2010-05-09
> **CharlesA said:**
> Should be able to disable that in the BIOS.I thought so too. Researching, it appears that  other users have the same complaint.

---

### Post by Shazaam on 2010-05-09
standingwave...
I have an older Soyo Dragon board that runs SATA drives through a raid/scsi screen in order to be detected. But it only adds 2-3 seconds to the bios load time.
When was the last time you updated your bios? Flashing your bios is not for the faint of heart (especially if your power goes out during the flash) but it can be done safely if you follow the directions to the letter.
Things to shut off/enable in your bios...
1. Enable "Fast Boot" (may be called something else for your board).
2. Turn off previously mentioned floppy seek.
3. Turn of any oem logo screens.
4. Disable WOL (Wake on Lan), wake on keyboard/mouse (unless you hibernate/suspend your pc).
5. Disable Serial/Parallel/Game ports if you don't need them.
6. My board has 6 usb ports. Disable the ones you don't need.
7. In your boot order screen, make the hard disk(s) first in the order, cd-dvd/rom second.
There are other settings that are specific to certain motherboard/bios brands. Try the manufacturers website for more info.

---

### Post by standingwave on 2010-05-09
> **Shazaam said:**
> When was the last time you updated your bios?Computer's only a year old but I'm not going to reflash just for this. And I'm probably exaggerating on the length of the prompt. It feels like ten seconds but is probably closer to four or five. I'd feel pretty stupid if I wound up screwing up my BIOS just to shave a few seconds off the boot.

---

### Post by chriswyatt on 2010-05-09
I've never had a firmware or BIOS update go wrong and I've done it countless numbers of times.  Seems like a reasonably safe operation to me though I'm nervous about running these BIOS updates that run from inside Windows.

I remember reading somewhere that it's good to update your BIOS about every 6 months.

---

### Post by chriswyatt on 2010-05-09
Though I'm a risk-taker in nature and I'm also obsessive about keeping things up-to-date.  This person has a more level-headed opinion :)

[http://ask-leo.com/do_i_need_to_regularly_update_my_bios.html](http://ask-leo.com/do_i_need_to_regularly_update_my_bios.html)

---

### Post by TheLions on 2010-05-09
> **chriswyatt said:**
> I've never had a firmware or BIOS update go wrong and I've done it countless numbers of times.  Seems like a reasonably safe operation to me though I'm nervous about running these BIOS updates that run from inside Windows.

I remember reading somewhere that it's good to update your BIOS about every 6 months.

don't flash your BIOS unless you REALLY need to.. that thing is very dangerous, especially when manufacturer puts the faulty BIOS file on their for you motherboard on support page :)

---

### Post by CharlesA on 2010-05-09
If it works, don't mess with it. That is the rule of thumb when you deal with the BIOS and anything else that is currently working.

Manufaurers even state to not flash the BIOS if it is currently working fine.

---

### Post by Tux_Master on 2010-05-10
Hi guys! I´m having the same problem with my notebook [Acer eMachines E725]("http://www.lapspecs.com/wiki/acer+emachines+e725"). 

I have dualboot on it: Ubuntu Karmic and Windows 7. Had no problems until I installed Ubuntu. Now it takes between 30 seconds and 2 minutes to get to the grub. When I have installed Ubuntu on it, had no problems for the first couple of weeks, the problem showed up later. So I flashed my BIOS, and the problem wasn´t solved. After that I deleted Ubuntu, and worked fine with windows. And than I installed Ubuntu again, and the problem was back again. So i deleted Windows, and again nothing was solved. So, I put Windows back.

I don´t know what to do any more, but I know that I don´t want to delete Ubuntu. I´d rather delete Windows if that would solve the boot up problem. But it won´t. The problem is in Ubuntu. I haven´t tried with any other distro, but Ubuntu, so I don´t know if the problem is just Ubuntu, or any GNU/Linux. 

Please, help..:confused:

---


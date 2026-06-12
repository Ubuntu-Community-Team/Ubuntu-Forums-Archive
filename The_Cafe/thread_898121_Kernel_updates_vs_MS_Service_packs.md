---
title: "Kernel updates vs MS Service packs"
date: 2008-08-22
forum: The Cafe
---

### Post by lsutiger on 2008-08-22
I was sent an email from cnet today that had the subject of service packs for Vista and the reservation of actually installing these 'fixes'.

I know I must be stirring up a pot here, but I think my concern is valid here.

The question I have is this: How many of you are worried about installing kernel updates in Ubuntu?


The reason I ask is this: I run Ubuntu 8.04 on a production machine at work. I CAN NOT have ANY down time. I run a Virtual Box with WinXP or certain tasks (which I plan on converting to Linux tasks soon) that are critical to information sharing. There is now way in the world that I can risk a major problem show it's face while working. From what I have read here on this forum, the kernel updates have caused many problems to many people. 

So all in all I just want some input, see a debate here, and let me have your say. 
Was 8.04 not ready for prime time? Are you having problems every time there is a kernel update? What should the community do in order to make sure an early release does not make it to the public before it's time? Etc...
Thanx for all of the replies!

---

### Post by lucho64 on 2008-08-22
I would hold on to Gutsy. The Hardy upgrade on my laptop broke internet connectivity. Besides, they decided to take out the perfectly good and stable, no frills, xmms player :mad:
I think that just because a program is not being patched daily it doesn't mean it's dead. It might mean it is so good at what it does and so stable that it doesn't need fixing. How many times totem or some of the other fancier players choke and died while good old xmms just kept churning along? My point is that that should be a bigger part of the equation when planning a release, stability.

---

### Post by mrsteveman1 on 2008-08-22
MS service packs actually compare more to Ubuntu upgrades, like 7.10> 8.04. In other words, large changes to most of the system, not just the kernel.

I have seen hardy freeze a few times but i think it was the b43 driver (it does like to spit out some crash data a lot on rmmod, especially when firmware isn't loaded into the chip).

On the other hand I get the feeling that the Ubuntu (or debian) devs are doing more work than should be necessary and perhaps that might impact kernel update stability. For instance, the hardy kernel is now almost 3 full releases behind mainline. That means in order for it to remain secure and stable, the Debian or Ubuntu devs have to backport fixes, which in some cases is very difficult or impossible if entire subsytems have changed or are missing. 

Maybe I'm naive, but i would assume it would be easier to just use the newer kernel, than to selectively force newer stuff into an older kernel, and i'm still not quite sure why this is the way things are done.

---

### Post by kostkon on 2008-08-23
I had between 10 to 20 (I don't have an exact number) kernel updates from the time I was running 7.04 (I have upgraded to 8.04 since) and never had any problems (really!). Not any problems with the rest of the updates (hundreds of them) either so I can say that for me, based on statistics, Ubuntu has a relatively secure and reliable update system.

Furthermore, I upgraded from 7.04 to 8.04 (7.04 -> 7.10 -> 8.04) and the procedure worked flawlessly.

I have read from various sources that Ubuntu Server Edition is valued for its high uptime capabilities.

That's all I wanted to say. :)

---

### Post by Sef on 2008-08-23
Moved to Community Cafe.

---

### Post by Barrucadu on 2008-08-23
I've had no kernel problems whatsoever :)

---

### Post by billgoldberg on 2008-08-23
I had one kernel update in hardy (I think it was 2.6.24.18) that broke my internet connection.

I switched back to 2.6.24.17 (still installed, just picked it from the grub list) and a few updates later, it was fixed.

That's the only problem I ever had with a kernel update.

---

### Post by billgoldberg on 2008-08-23
> **lucho64 said:**
> I would hold on to Gutsy. The Hardy upgrade on my laptop broke internet connectivity. Besides, they decided to take out the perfectly good and stable, no frills, xmms player :mad:
I think that just because a program is not being patched daily it doesn't mean it's dead. It might mean it is so good at what it does and so stable that it doesn't need fixing. How many times totem or some of the other fancier players choke and died while good old xmms just kept churning along? My point is that that should be a bigger part of the equation when planning a release, stability.

I'm using xmms on hardy.

There are .deb files on the internet for it.

The only thing I didn't get working due to dependacy issues was xmms-infopipe. 

It's also to bad conky has no xmms support anymore, but without infopipe it wouldn't really matter anyway.

Audacious is no replacement for me. It opens each song in a new player (wtf!?) and is slow as hell on my 3.00ghz dualcore (wtf!?).

---

### Post by Polygon on 2008-08-23
if you dont want any downtime, DONT UPGRADE. IF IT ISNT BROKEN, DON'T FIX IT

anyway, the only problems with kernel updates that i have seen:

way back in what..breezy? ubuntu released a nvidia driver upgrade that made it so ubuntu would crash x, dumping a lot of non technical people into the command line

and also recently, in the PROPOSED repo, the 2.6.26.20 kernel upgrade would not even boot. But since it got released to the propsed repo first, about 100+ people were like "Its not booting!" and they fixed the problem before it got released mainstream =)

i would trust kernel updates over MS updates any day. mostly because i have had soundcard and wireless card updates come through windows update and when they install, they blue screen the computer and then it cant boot up again (blue screens on boot) because of bad drivers. I had to go into safe mode and deactivate the hardware to get my computer to boot again. Yeah, like im going to ever trust something coming through windows update ever again

---

### Post by crazyfuturamanoob on 2008-08-23
I have never had any problems with kernel updates on ubuntu, except once a program couldn't run with the new kernel I just updated, only with the old one. But you can change the kernel version to use at bootup menu, right?

---

### Post by JP1990 on 2008-08-23
i love my new version of Ubuntu actually i love the only version of Ubuntu i have ever used 8.04 it rocks compared to xp a life of no virus's = peace and quite :)

---

### Post by SunnyRabbiera on 2008-08-23
Micrsoft updates, ugh far more annoying as they are so constant and irritating.
I am glad that with linux if a newer kernel doesnt work a older kernel is always kept around just in case... cant do that in windows :D

---

### Post by public_void on 2008-08-23
With any major update wait. Let others try it first, if they have problems it will be flagged somewhere, most likely this forum.

---

### Post by mips on 2008-08-23
> **billgoldberg said:**
> I had one kernel update in hardy (I think it was 2.6.24.18) that broke my internet connection.

I switched back to 2.6.24.17 (still installed, just picked it from the grub list) and a few updates later, it was fixed.

That's the only problem I ever had with a kernel update.

Yeah, I always thought the older kernel was available in the GRUB list to eliminate problems of downtime should a new kernel not work.

---

### Post by FuturePilot on 2008-08-23
Only once. A kernel update broke suspend but it was quickly fixed.

SP3 totally borked XP.

---

### Post by SunnyRabbiera on 2008-08-23
> **FuturePilot said:**
> Only once. A kernel update broke suspend but it was quickly fixed.

SP3 totally borked XP.

SP2 borked my XP

---

### Post by kavon89 on 2008-08-23
I always run into a problem with my video drivers on a kernel update. On every kernel update, I have to go visit my handy dandy text file with specific instructions that make the Nvidia driver install work, and it's no ordinary instructions like cd here and ./ that, theres a couple special things you have to do.

For a while before I put together instructions for myself that made everything work, I dreaded another kernel update and specifically unchecked anything related to kernel stuff if I wanted to delay having to go through all that 640x480 mess again.

Hopefully 8.10 fixes my issue. :s

EDIT: Yes I know all kernel updates come with the new header files and all that for Nvidia, but none of those worked originally for my system.

---

### Post by RiceMonster on 2008-08-23
Never had a problem with a kernel update.

---

### Post by Dremora on 2008-08-23
They've fried my system before, but that was on Fedora.

Fedora's overall package quality is fairly unreliable, even normal updates can often brick something.

Ubuntu is generally much more reliable, in four years I've only had one problem with an official Ubuntu kernel, it was minor, and fixed within a couple weeks.

---

### Post by mintochris on 2008-08-23
One update was released before virtualbox had updated their packages, and so I lost my VM's for a week or so, but other than that it's been plain sailing.

---

### Post by PurposeOfReason on 2008-08-23
Normal updates always have worked, not so much with the RC's but that's my fault.

---


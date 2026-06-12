---
title: "Eureka! An XBOX 360 running Ubuntu"
date: 2007-08-18
forum: The Cafe
---

### Post by izanbardprince on 2007-08-18
After sitting here all day alternating between a soldering gun, a hair dryer, and a cigarette, I've managed to get Ubuntu running on my XBOX 360, it does "see" all three cores, and 384 megs of RAM, with the rest of it running the video card in framebuffer mode.

It's surprisingly fast and stable, I have it hooked up to my 21"  eMachines LCD monitor, my Microsoft USB keyboard, and my Microsoft optical mouse, my Philips 2.1 speakers and subwoofers, and I have 80 gigs of my 120 gig hard drive partitioned off for Linux.

---

### Post by init1 on 2007-08-18
Nice.

---

### Post by original_jamingrit on 2007-08-18
Awesome.

Nothing says "Stick it to the man" like Linux on (what's supposed to be) a purely Microsoft machine.

---

### Post by Epilonsama on 2007-08-18
Now try to run your video card in anything but frame buffer, anyway nice one question could you still use it to play xbox 360 games?

---

### Post by starcraft.man on 2007-08-18
Why? I mean I didn't get the people putting Linux on PS3s... why did you want it on a 360?

---

### Post by dfreer on 2007-08-18
> **starcraft.man said:**
> Why? I mean I didn't get the people putting Linux on PS3s... why did you want it on a 360?

Because you *can* ;)

---

### Post by izanbardprince on 2007-08-18
> **Epilonsama said:**
> Now try to run your video card in anything but frame buffer, anyway nice one question could you still use it to play xbox 360 games?

Yes, I have it switched, I can boot it up in Linux, or with the XBOX dashboard, I signed into XBOX Live and held my fingers, it signed in and my account is still active. (knock on wood)

---

### Post by DeadSuperHero on 2007-08-18
With the PS3, it's alot easier to install Linux. They practically give you an option to install it.
But on an Xbox 360, well, it's Microsoft.
Therefore, it's an achievement.

---

### Post by init1 on 2007-08-18
> **dfreer said:**
> Because you *can* ;)
Exactly. :D

---

### Post by Darth Trix on 2007-08-18
> **dfreer said:**
> Because you *can* ;)

...and because you should.

---

### Post by Polygon on 2007-08-18
the xbox 360 only has like 380 mb of ram? what?

How does it play games like freaking gears of war with only THAT MUCH RAM?

and you might want to write up exactly what you did and post it on the net somewhere, im sure other people would be very interested on how to do this

---

### Post by izanbardprince on 2007-08-18
> **Polygon said:**
> the xbox 360 only has like 380 mb of ram? what?

How does it play games like freaking gears of war with only THAT MUCH RAM?

and you might want to write up exactly what you did and post it on the net somewhere, im sure other people would be very interested on how to do this

The 360 has 512 megs of unified system/video RAM.

Also Gears of War has lots of load screens, when it plays a cutscene and makes you walk around real slow and you hear the disc drive spinning WAY UP, thats how they hid the loading screen.

---

### Post by tcpip4lyfe on 2007-08-18
very cool

---

### Post by Anthem on 2007-08-19
> **Polygon said:**
> the xbox 360 only has like 380 mb of ram? what?

How does it play games like freaking gears of war with only THAT MUCH RAM?
It doesn't have to run a DE.

---

### Post by 3rdalbum on 2007-08-19
> **Anthem said:**
> It doesn't have to run a DE.

Or an X server, or drivers for many hardware devices.

I wasn't even aware that there was still a way to bypass Microsoft's security features after all the involuntary firmware updates - good work!

---

### Post by happy-and-lost on 2007-08-19
Wanna help me put Debian on my Nintendo DS? ;)

---

### Post by tigerpants on 2007-08-19
My question would not be "why install linux on a 360" but "why buy a 360 in the first place"?

Its the most awful console ever made. And that includes anything made by Atari. And its made by Microsoft. *shudder*

---

### Post by proalan on 2007-08-19
brilliant, all you need now is to release a linux distro specifically for the xbox360, that would put a big grin on the global linux community.

---

### Post by peterbrewer on 2007-08-19
I'm curious, did you build your own ubuntu install cd using kernel patches from [http://www.free60.org/wiki/Main_Page](http://www.free60.org/wiki/Main_Page) or did you use a different method.

---

### Post by izanbardprince on 2007-08-19
> **tigerpants said:**
> My question would not be "why install linux on a 360" but "why buy a 360 in the first place"?

Its the most awful console ever made. And that includes anything made by Atari. And its made by Microsoft. *shudder*

The 360 is a pretty good console actually, it beats going out and buying a $3,500 PC to play games on.

Take Halo 2 for Vista, or Oblivion, do you even know how much it would cost to get halfway decent performance on a PC?

To run Oblivion on a sub-$1,000 PC, you'll need to run it on Ultra Low Quality just to even get it to start up, and then it will be on 640 x 480 resolution with all the effects turned off, and look even shittier than those shots of a guy running DOOM 3 on a dual Voodoo 2 setup.

---

### Post by wishyjr on 2007-08-19
wow, i've been waiting to hear someone do this for ages. Can you post a screenshot or video of it running? can you give us a quick run down whats involved in doing it?

cheers

wishy

---

### Post by izanbardprince on 2007-08-19
I'm in the process of writing a detailed how to, I'm also trying to find out how to make the changes so Microsoft can't reverse them or ban an XBOX Live account later on with an update, so far it's working, I used some off the shelf parts from Radio Shack, totalling about $27 for the components, less the soldering gun which I already had, and a pair of fingernail clippers and a hair dryer (the ROM you need to access is covered in glue, the heat will soften the glue and let you use a diluted acetone mix to strip it off.

Anyway, I don't want to release too many details til I feel I have a foolproof solution, for fear that Microsoft will kill this off before it gets off the ground.

I'm also looking for ways to run the Linux kernel without running it on top of a Hypervisor, enabling direct hardware access, and possibly somewhere later down the road, full 3d video acceleration.

---

### Post by jgrabham on 2007-08-19
Blasfemy :D

---

### Post by Dimitriid on 2007-08-19
I don't really see the point, pc hardware is cheap right now you can build an awesome system with $399. As for the games I just do not like what supporting Microsoft ( or Sony for that matters ) means and he games well, lets just say that not impressed is an understatement.

---

### Post by g2g591 on 2007-08-19
great job!!!

---

### Post by shynko on 2007-08-19
I get putting it on a xbox as part of the whole linux on a microsoft only thing but I think it would be real cool if you could get it on a wii :)

---

### Post by Tuna-Fish on 2007-08-19
> **izanbardprince said:**
> The 360 is a pretty good console actually, it beats going out and buying a $3,500 PC to play games on.

Take Halo 2 for Vista, or Oblivion, do you even know how much it would cost to get halfway decent performance on a PC?

To run Oblivion on a sub-$1,000 PC, you'll need to run it on Ultra Low Quality just to even get it to start up, and then it will be on 640 x 480 resolution with all the effects turned off, and look even shittier than those shots of a guy running DOOM 3 on a dual Voodoo 2 setup.

This is a joke. From a local computer store:
```

1  	PNY GeForce 8800 GTS 320 Mt, PCI-E  	274 € 
1	MSI P35 NEO-F 	97 € 
1 	Antec Sonata III 	110 € 	
1 	LG 18x DVD+/-RW Dual Layer (GSA-H44N) 	27 € 	
1 	Western Digital AV (250 Gt, 7200 RPM, serial-ata II) WD2500AVJS 	61 € 	
2 	1 Gt, 800 MHz DDR2 	40 € 	
1 	Intel Core 2 Duo E4400 	112 € 	
  	Total	760 € 

```
Than will run pretty much every game on the market smoothly on 1680x1050 res with high settings. Swap the 8800GTS for a 8800GTX, and it will literally rival the 3500$+ ubergaming rigs on performance. gaming is all about the graphics card, screw the rest.

The top alieware/whatever gaming rigs are so full of air I still quite don't get it. These days, you just buy a 150€+ graphics card and you can run all the games well. the reason the prebuilt sub-1000 computers suck at games is because they have some ridiculously crappy graphics card with a 128-bit mem interface on ddr2 or something. Spend 150$ on a radeon 1950 pro and you instantly turn them into an ok gaming rig, put in a g8800 instead and you got a kickass rig.

---

### Post by Depressed Man on 2007-08-19
Not to mention for Oblivion you can use mods (and likely Halo 2 unofficially). There are people hacking around with it already to get it to run (pretty well except for some crashes like at the end credits) on Windows XP. 

Though the only real issue I have with the 360 (I'm getting one myself later on Black Friday if there's a good deal) is its reliability.

---

### Post by izanbardprince on 2007-08-19
> **Dimitriid said:**
> I don't really see the point, pc hardware is cheap right now you can build an awesome system with $399. As for the games I just do not like what supporting Microsoft ( or Sony for that matters ) means and he games well, lets just say that not impressed is an understatement.

$399 will get you a really nice processor, minus the rest of the system

---

### Post by Tuna-Fish on 2007-08-19
Only, there is no need to get anything better than the worst core duo for a processor if all you want to do is play games. You have to get a pretty high end graphics card just to strain a E4300 to it's limits.

---

### Post by Depressed Man on 2007-08-19
You don't even have to get an Intel Core 2 Duo. You could just get one of the AMD dual cores. They're not as efficient as the Intel Core 2 Duos but they'll still get the job done (with minor performance loss). 

Though compared to the 360 *shrugs* who knows. It may still be better.

---

### Post by kdarkentity on 2007-12-13
Godly!, this is something i've been interested in doing for quite some time now, especially because i have an older xbox 360 beaten to hell but still works fine just sitting in a drawer. 

Could you possibly send me a how to to my email?

[email]kdarkentitiy@yahoo.com[/email]

thanks.

---

### Post by NonPermissive on 2007-12-13
> Why? I mean I didn't get the people putting Linux on PS3s... why did you want it on a 360?
Um, not to mention the obvious advantages of more  computers (in essence, free, if you already have the console), plus the just-plain-hardcore processing power of the PS3, and...

> *Because you can :)*

---


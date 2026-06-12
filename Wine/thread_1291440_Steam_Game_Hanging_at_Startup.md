---
title: "Steam Game Hanging at Startup?"
date: 2009-10-14
forum: Wine
---

### Post by gh4ever on 2009-10-14
[http://bugs.winehq.org/show_bug.cgi?id=10487](http://bugs.winehq.org/show_bug.cgi?id=10487)
I've posted on this bug, but it looks like no one has or is going to reply anytime soon.
Any fixes?
Steam community disabled, compiz disabled, just about everything I can think of disabled.

---

### Post by castlefox on 2009-10-14
Your using the latest version of wine right?

What video card are you using? Driver?

---

### Post by gh4ever on 2009-10-14
Thanks for the quick response.
Yes, latest version of wine (I believe, anyways), 1.1.31. From the Wine's official repos.
gh4ever@Eric-laptop:~$ lspci |grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960
Integrated Graphics Controller (rev 03)

[FONT=Verdana]I'm pretty sure that's the command, anyways.
Intel driver package from synaptic is 2.6.3 (package xserver-xorg-video-intel).
[/FONT]

---

### Post by gh4ever on 2009-10-15
Oh, just so you know, I'm Eric in the bugpost.

EDIT: Another bit of information, I copied my steamapps folder to keep all of the savegames/files/maps I already had. I'm downloading HL2 via steam in wine right now, I'll let you know how it works out.

---

### Post by MaindotC on 2009-10-15
I've been trying to get CS to work on wine and it just isn't working no matter how I slice it.  I tried Jaunty, and after reading threads saying my Gigabyte GA-MA785GM-US2H card had a lot better video support in Karmic I installed and still no luck.  I get the following output after CS freezes, quits after about 30 secs, then goes back to desktop:
```

Unhandled exception: wait failed on critical section 0x7bc932a4
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc3adf0
Process of pid=0042 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000c 
	00000020    0
	0000000e    0
	0000000d    0
0000000f 
	00000010    0
0000001d 
	00000022    0
	00000021    0
	0000001f    0
	0000001e    0
00000039 
	00000043    1
	00000029    0
	0000001c    0
	00000037    0
	00000038    1
	00000035    1
	00000033    1
	00000034    1
	00000009    1
	00000023    0
	00000030    0
	0000002f    0
	0000002c    0
	0000000b    0
	00000015    0
	00000013    1
	0000001b    0
	00000017    0
	00000011   15
	00000047    0
	00000046    0
	00000044    0
	00000041    0
	00000040    0
	0000003f    0
	0000003e    0
	0000003d    0
	0000003c    0
	0000003b    0
	0000003a    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'
x@x:~/Desktop$

```

---

### Post by gh4ever on 2009-10-15
After some more googling around, it seems that Intel graphic cards (what I have, probably you too, strAlan) are notoriously bad with their Linux drivers. Apparently it's gonna be fixed in Karmic, though.
[http://blogs.techrepublic.com.com/opensource/?p=975&tag=nl.e011](http://blogs.techrepublic.com.com/opensource/?p=975&tag=nl.e011) (and other sources).
I guess I'll see if the problem persists in 2 weeks XD.

---

### Post by castlefox on 2009-10-16
Oh you are using 9.04 ?

I am also looking forward to 9.10

---

### Post by beastrace91 on 2009-10-16
You can upgrade to 9.10 now if you would like - it is decently stable. Haven't had any issues with it thus far :)

~Jeff

---

### Post by MaindotC on 2009-10-16
beastrace91 can you try running CS or any steam-based game in wine and let us know the results?  I tried 9.04 and 9.10 and CS freezes on startup!

---

### Post by gh4ever on 2009-10-16
Yeah, I was planning on upgrading early, too. I guess this gives me a good reason to do it XD.

---

### Post by MaindotC on 2009-10-16
In reply to your previous post, I have an ATI chipset, not an Intel.  I can't believe Intel's have a history of bad video drivers but at least a few people have suggested as much.  Let me know when you upgrade and how it goes.  I'd really like to get CS working!

---

### Post by krazyleaf on 2009-10-16
I've been trying to run my games through steam as well with no luck. I was thinking on going back to 8.04. since 9.04 isn't really working for me (ATI drivers that is) the version itself is fine.

---

### Post by MaindotC on 2009-10-16
> **krazyleaf said:**
> I've been trying to run my games through steam as well with no luck. I was thinking on going back to 8.04. since 9.04 isn't really working for me (ATI drivers that is) the version itself is fine.

See I'm in a weird situation because I have the ATI x850 (per my sig).  I'd really like to upgrade to Jaunty or even Karmic, but the x850 is no longer supported by ATI (what they refer to as "legacy support structure"), so if I install any further versions, I've got a card that can't get a driver working for it because of x.org versions and other dev stuff that's way above my head.  So I bought a new mobo, ram, all that stuff - a Gigabyte GA-MA785GM-US2H, and it turns out the onboard video, an ATI HD4200, doesn't have a driver that will work fully (3D and all that) on 8.10 and below (at least none that I found - if I'm wrong please feel free to suggest!).  So I tried 9.04 but CS crash/freezes on start, and then I read in another thread that this mobo ran Karmic beautifully so I tried 9.10, but I'm running into the same problems.  Video is just so sensitive :(

I can't leave my previous machine that has the x850 ATI card until I can get CS working on my new machine - that is the key to all happiness in my life :)  I can't install 8.04 because I won't have the proper graphics support, but I can't use 9.04+ because CS keeps crashing :(

We'll see if anything changes with the full release.

---

### Post by MaindotC on 2009-10-16
Update - if you run CS w/o the propritary driver installed, and thus Karmic will revert back to the open-source Radeon driver, CS will work.  Unfortunately it's very choppy and slow and I was able to get into CS to change video settings to "Software" and "D3D" but "Software" is very rough cartoon-like and D3D was just plain slow :(  I re-installed the proprietary driver hoping "hey I got CS to work and switch to the proper resolution so maybe that'll help" but it still freezes :(

---

### Post by asdfoo on 2009-10-16
> **strAlan said:**
> Update - if you run CS w/o the propritary driver installed, and thus Karmic will revert back to the open-source Radeon driver, CS will work.  Unfortunately it's very choppy and slow and I was able to get into CS to change video settings to "Software" and "D3D" but "Software" is very rough cartoon-like and D3D was just plain slow :(  I re-installed the proprietary driver hoping "hey I got CS to work and switch to the proper resolution so maybe that'll help" but it still freezes :(

I had an x850, it was a joke on Linux, worse performance than my 9800 pro that I had purchased several years earlier.

I sold it on ebay and bought a geforce 8 instead, cs and other games then started working, problem solved.

---

### Post by MaindotC on 2009-10-16
My x850 works just fine in Hardy.  CS works, great FPS, and I run 1600x1200 res.

---

### Post by asdfoo on 2009-10-17
> **strAlan said:**
> My x850 works just fine in Hardy.  CS works, great FPS, and I run 1600x1200 res.

Ah ok.  When the x850 was released, this was not the case, it had massive slowdowns in native opengl programs compared to older cards.

---

### Post by gh4ever on 2009-10-17
Ok, my Karmic install didn't go all to well...basically ruined my computer. Luckily I had a backup of my home folder....
Hopefully the upgrade will work in a couple of weeks.
Using methods found around the web, it seems that the graphics card I have supports OpenGl. I have checked and yes, it is (and was) installed. I haven't tried reinstalling my steam games yet, but can the graphics card still be a problem even if it does support OpenGl?

---

### Post by MaindotC on 2009-10-17
gh4ever, I'm getting a lot of help running CS on Karmic.  I know you said you had a problem, but my thread is [http://ubuntuforums.org/showthread.php?t=1293110](http://ubuntuforums.org/showthread.php?t=1293110) - it actually was a thread about the ATI HD4200 integrated graphics card but I got someone w/ the exact same setup as me that advised me on installing Steam and running CS.  He says it's working fine for him.  [My post #19](http://ubuntuforums.org/showpost.php?p=8119694&postcount=19) is a step-by-step log of how I'm going about it.  Right now I'm installing Steam so we'll see if I get CS working fully or not.  Fingers crossed!

---

### Post by gh4ever on 2009-10-18
Oh, never-mind, you've got an ATI card. I've got an Intel card with Jaunty; apparently I'm lucky to even have my system going. I think I'll wait it out until Karmic's released.

---

### Post by gh4ever on 2009-10-30
Ok, updated to Karmic, still nothing.

---

### Post by MaindotC on 2009-10-30
I know this is probably a dumb question but I have to ask: do you have the [latest Intel drivers](http://is.gd/4IgTQ) for the 965?  If not, in the multimedia & audio thread there's a sticky for comprehensive Jaunty Intel Graphics Performance thread.  Probably work the same for Karmic.

---

### Post by gh4ever on 2009-10-30
I got the newest one in the repositories, but there's a newer one on the Intel website.
I'm currently downloading this one:
[http://edc.intel.com/Software/Downloads/IEGD/#overview](http://edc.intel.com/Software/Downloads/IEGD/#overview)
.
Also, thanks for the quick reply!

---

### Post by gh4ever on 2009-10-30
Ok, when I downloaded the Linux version, it still gave me an exe....
So right now I'm trying the sticky you mentioned at [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
.

---

### Post by MaindotC on 2009-10-30
I'm following Intel's directions for getting drivers for this mobo - I can't believe how complicated this is...

Found [this](http://www.intel.com/support/chipsets/sb/CS-025753.htm).  Did you download and run that or whatever that site does?

Ok, followed the link for the System Update Utility and it seems to be web-based.  That's about as far as I can go b/c I'm not Intel-based. Did you try running that?

---

### Post by gh4ever on 2009-10-30
I've given up on the official Intel website; they have VERY little to no support for linux. That link you gave me says it only works on windows in the fine print....
In the other link you gave me (the one involving updating adding new repositories for jaunty), I made sure I used the Karmic equivalent and the repository works fine. There's a libgl1-mesa-glx AND a libgl1-mesa-swx11 that can't be installed at the same time. Which one should I use?

---

### Post by gh4ever on 2009-10-30
Well, I used the glx one, and it worked! Thank you so much! I really owe you big.
Well, in summary, follow the directions at [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582).

---

### Post by MaindotC on 2009-10-30
Hey np - I'm glad it worked for you :D  Unfortunately you're now practically obligated to f-add me so I'm going to send a request.

---

### Post by gh4ever on 2009-10-31
Ok, I spoke too soon....
I was trying Team Fortress 2, and it actually loaded, which was farther than I had ever gotten. I then quit and posted here. I tried the game again, though, and it would crash when connecting to a server or changing my "loadout". I tried Day of Defeat: Source, and that didn't start at all. I disabled sound in wineconfig, and Day of Defeat loaded, except whenever I connect or make a server it looks like there are holes in the ground (like, missing textures or something) and it goes unplayably slow. I have -dxlevel 80 -novid in the launch options and Compiz disabled.
It feels like there's only one thing I'm missing now, but I can't figure out what it is.

---

### Post by gh4ever on 2009-10-31
Ok, I found a set of settings to let sound work while playing. I'm gonna try and start a local game right now....
Edit: Nope, still laggy.

---

### Post by MaindotC on 2009-10-31
> **gh4ever said:**
> Edit: Nope, still laggy.

:(  You know I'm kind of in a similar situation w/ my on-board graphics. This dev of xorg-edgers is trying really hard to put 3D support for the open-source raedon driver (before it's supposed to be included in April) and for the most part it works but it's choppy/laggy.  I thank the devs of xorg-edgers because they're really going above and beyond.  

However, I really want to move from my old hardy machine (that runs CS perfectly) to the Karmic machine so I'm just going to shell out $150 and get a decent vid card at my next paycheque.  I hate the fact that I can't fully utilise what I have already, but on-board video is really more of a backup.  I'd put my x850 into the karmic machine but the driver isn't supported.  Find a decent vid card - there are some video card rating lists on toms hardware.  Or, you can play Urban Terror in the meantime :D

---

### Post by gh4ever on 2009-10-31
Yeah, kudos to the people over at xorg-edgers. Too bad it still doesn't go as fast as on windows....
Ah well, a new graphics card isn't a bad thing :).

---

### Post by gh4ever on 2009-10-31
Hey, could I get those games to work on VirtualBox? I used to play them on an XP machine that's slower than the one I'm using now, and I'm trying my best not to dualboot.

---

### Post by MaindotC on 2009-11-01
I installed Steam in a copy of XP Pro and it ran beautifully, graphics-wise.  Hopefully you can gather from my signature the type of specs I have and compare them to yours.  The only thing is the mouse (in my case a trackball) seems to be interpreted strangely in the VM because it moves my aim about...for lack of a better term...aimlessly.  It probably would work better if I enabled my usb trackball in the USB settings of VBox but I use the OSE edition which currently does not have USB support :(  Give it a try - 10 GB should be enough for XP with CS installed.

---


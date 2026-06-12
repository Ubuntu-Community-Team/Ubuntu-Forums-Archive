---
title: "Inquire about studio setup?"
date: 2010-02-28
forum: Ubuntu Studio
---

### Post by orin zolis on 2010-02-28
Hi I have been using ubuntu 9.10 for a little while now for everyday stuff, but I am wanting to deck out my laptop for music production in 7.1 surround sound using fl studio and various vst plugins, I have read the tutorial of installing packages for fl, but whilst doing this as a test run on my everyday pc I somehow encountered an audio driver hickup and it seams as though the alsa driver isnt there anymore i've looked for updates but nothing seams to fix it, so before I go messing around with my laptop I wanna get a few things straight.

can anyone that know's, suggest a sound card for 7.1 mixing capabilities that has been confirmed to work with any modle of Linux.

I am willing to buy support from the canonical store but dont want to waste any money if there isnt any confirmation that the set up I am after is possible, I have heard that VST support is now stable is this true that all vst plugins work via wine now. and are midi controllers/harware synths supported aswell, I have a korg ms20 and am thinking of getting a Korg M50.

any feedback is much appreciated
 
thanks
ryan

---

### Post by Bakerconspiracy on 2010-03-01
Hey,

This is an issue with linux I've been waiting for a while to have progress. I feel music production (or video production) on a linux machine is not quite up to par with Mac (or windows in the case of FL).

With wine, the only program that I have been even remotely able to install and use is Reason, but even that seems to have latency issues. Honestly, I have lost all hope of being able to produce music easily or comprehensively on linux - I still use my macintosh for that :(

Have you looked into the alternative LMMS?  [http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)  It has a FL feel, but I'm not sure if it contains a surround sound feature. I'm pretty sure you can load VSTs into it as well. Maybe this will help a little bit. Also, have you tried installing the "Ubuntu studio" software package? Sorry I can't answer any of the FL questions directly, but just know you are in for some long nights getting a program like FL to work completely.

Good luck,

Let me know if you come up with anything.

---

### Post by hxcobd on 2010-03-01
As someone who has used linux on-the-side for audio production for about 5 years now, here's what I can tell you, in a nutshell, about audio production in linux:

- It WILL require a ton of tweaking
- It WILL require a ton of Terminal use

- Your Windows VSTs largely will NOT work properly, especially not without a TON of tweaking
- If your Windows VSTs are particularly large or complex, such as VSTis with huge sample banks, definitely don't count on them working at all

- Trying to run entire DAWs under WINE is generally pretty futile. If you CAN get them to work, run stable, and run fast, it's because you tweaked them a LOT.

The entire situation regarding trying to run audio programs or plugins from Windows under linux, to me, is a "don't even bother." It's a TON of effort and you'll almost never get the same performance you would by just dual-booting into Windows.

Now, that said, audio production in linux itself has come a long way, and really is worth persuing, even without using WINE or Window programs/plugins at all.

Renoise, EnergyXT, Hydrogen, Ardour, LMMS, QTractor, Rosegarden, Muse, Reborn... There are a TON of audio applications with native linux binaries or compilable source code.

There are a lot of plugins as well, in Linux VST, LV2, DSSI, and LADSPA format.

Not every linux host supports every plugin type, either, but that's similar to Windows anyway.

On a positive note: if you're WILLING to do the tweaking and testing necessary, native linux audio software can perform at RIDICULOUS speeds, even on subpar systems. I get latencies MUCH lower in linux than I do in Windows. Granted, I spent literally 10-15 hours alone just tweaking my audio setup, but now, it's good to go forever, all I do is open JACK, check my settings, hit Start, and I'm good to go!

It's worth pursuing, but you have to be willing to work hard, learn, and possibly change your workflow. If you're not willing to do all 3 of these things, it's probably not for you.

---

### Post by orin zolis on 2010-03-03
well there's only a couple of plug ins that I really use now days, and maybe some othes that I may buy but tottals about 3 vst's atm that I use, woul,d canonical support help me tweak them to work properly in wine on flstudio.

I have downloaded ubuntu studio package on a freshly installed ubuntu 9.10 and the sound works again.

if I run windows in a virtualbox and install fl on there can I get the drivers for a sound card to work from there. or do I need to download and tweak them for Linux aswell?

thanks both of you for the comments above.

---

### Post by AutoStatic on 2010-03-04
> **orin zolis said:**
> woul,d canonical support help me tweak them to work properly in wine on flstudio.No. That's where the Ubuntu community is for.

I'd suggest you first take a peek here: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---


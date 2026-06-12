---
title: "WoW with wine. Can someone post there config.wtf please?"
date: 2010-08-25
forum: Wine
---

### Post by Garoes on 2010-08-25
Hey,
I'm new to ubuntu and just tried to install WoW with Wine, everything seemed fine during installation, and patching.
Everything was going fine - until I launched WoW. I had very low fps, so I tried a few things.

 I tried adding the line which allowed the game to run with OpenGL. it was still going slow.
Then I tried something else, which I can't remember, and the background was gone, the "log in" buttons where there though, I had great fps, but graphical errors.

I tried copy and pasting someone's config.wtf from some other forum and it now has more problems than I started with.

Can someone please copy and paste there config.wtf lines here please?

---

### Post by hikaricore on 2010-08-25
You spelled "their" wrong several times.

But anyway back on topic someone posting their config.wtf file isn't really going to help you.
I suspect this to be a limitation of your "video" hardware or drivers. 
Perhaps you should say a bit more about your system before you assume a conf file will solve your troubles.

Just to humor you or prove my point here's my config.wtf file: [http://pastebin.com/9BTcUzzx](http://pastebin.com/9BTcUzzx)

---

### Post by Garoes on 2010-08-26
> **hikaricore said:**
> You spelled "their" wrong several times.

But anyway back on topic someone posting their config.wtf file isn't really going to help you.
I suspect this to be a limitation of your "video" hardware or drivers. 
Perhaps you should say a bit more about your system before you assume a conf file will solve your troubles.

Just to humor you or prove my point here's my config.wtf file: [http://pastebin.com/9BTcUzzx](http://pastebin.com/9BTcUzzx)

Processor - Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
Graphics card  - Intel gma x3100

I heard I need opengl drivers for the x3100, but I think their already installed. Is there anyway I can find out ? (I'm a noob)

---

### Post by stephlar on 2010-08-26
> **Garoes said:**
> Processor - Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
Graphics card  - Intel gma x3100

I heard I need opengl drivers for the x3100, but I think their already installed. Is there anyway I can find out ? (I'm a noob)


What Ubuntu Linux version are you running?

If you can find your Synaptics Package Manager (under Settings - Administration, if you're running a newer Ubuntu version), you can check to see if you have the following installed on your computer:

xorg, xserver-xorg, and xserver-xorg-video-intel
(should be checked or marked with a green box for "installed" - a box with a ! mark means you can upgrade it...  I'm using Ubuntu 10.04, so that's what it looks like to me.  Could be different with your version)

Those are like the main open source video drivers components.  If one of those isn't installed, then we have a problem!  :)


P.S.  Intel sucks!  Ok, had to get that out there.

---

### Post by Diskbox on 2010-08-26
Garoes, I had the same problem after adding the opengl line to the config file.  The fix for me was to add -opengl to the end of the command line to run launcher.exe

See if this fixes it.

---

### Post by cwwilson721 on 2010-08-26
> **Garoes said:**
> Processor - Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
Graphics card  -[COLOR=Red] Intel gma x3100[/COLOR]

I heard I need opengl drivers for the x3100, but I think their already installed. Is there anyway I can find out ? (I'm a noob)The Intel chips and WoW/wine are VERY problematic right now, due to their CRAPPY opengl 'capabilities'.

Nothing you can really do right now (Not really sure you will ever be able to do anything about it). This forum has TONS of posts about WoW/wine and the Intel issue. The issue is that Intel doesn't implement the full opengl spec in the chips, so you're left hanging.

Intel drivers and opengl and wine/WoW are a HORRIBLE mix.

---


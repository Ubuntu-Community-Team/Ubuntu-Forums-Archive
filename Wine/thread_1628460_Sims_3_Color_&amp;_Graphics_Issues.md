---
title: "Sims 3 Color &amp; Graphics Issues"
date: 2010-11-22
forum: Wine
---

### Post by MelodiesonMusic on 2010-11-22
I've been trying to install The Sims 3 for the last couple of days, and it hasn't been opening. Now that I've finally figured out what i've been doing wrong there's still a major problem. I've installed using playonlinux, and when i open (I use the launcher made by playonlinux, not the actual sims 3 launcher)The screen might turn white, but it always turns black before the green logo appears. The graphics are perfect and it seems as if everything is working. It goes through the entire startup "movie" with no problem. However when the game begins to load it's as if someone's messed with the colors on the screen. All i see is the green loading bar, and some moving light blue text underneath. The rest of the screen is white, and it's way too bright. I can't read any text due to it's blocky, blobish form. After the game loads and what would be the start screen appears (it's also bright and blocky) a message box appears. I think it must be some kind of warning because when i click the left option underneath it disappears for a second and comes back. When i click the right option however, the game closes. I don't know how much help it will be, but i opened the game under playonlinux in the terminal, here's the output:
 
```

visitor@Music:~$ playonlinux
PlayOnLinux v3.8.6

Checking plugin: Advanced Wine Configuration...
Checking plugin: Offline PlayOnLinux...
Checking plugin: Capture...
Checking plugin: Transgaming Cedega...
Checking plugin: Wine Import...
Checking plugin: Wine Look...
Checking plugin: Detour...
Running The Sims 3
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)

```

The last line continues until i click the button that turns off the game. I'm using ubuntu 10.04, and i have both 1.34 & 1.1.42 of wine installed(is that a problem?). Thanks for any help you can give :) I've included some screen shots, I really hope they help.

-Mel

---

### Post by MelodiesonMusic on 2010-11-22
bump

---

### Post by MelodiesonMusic on 2010-11-25
is this in the wrong section?

---

### Post by racie on 2010-11-25
Yes, you're in the right section.

It looks like an ATI driver issue.  Have you tried updating it?

---

### Post by MelodiesonMusic on 2010-11-25
Welll, yes i have. It resulted in me messing up my entire computer and having to do a fresh install. I have an ATI Radeon Xpress 200 G, and i don't think it's supported. I tried installing the latest catalyst but it's a .run file and i had no idea how to open it. I was wondering if i need a new card or can i update it another way?

---

### Post by racie on 2010-11-26
> **MelodiesonMusic said:**
> Welll, yes i have. It resulted in me messing up my entire computer and having to do a fresh install. I have an ATI Radeon Xpress 200 G, and i don't think it's supported. I tried installing the latest catalyst but it's a .run file and i had no idea how to open it. I was wondering if i need a new card or can i update it another way?

Hmm... well have you tried downloading the driver directly from the ATI website?

If you go [here](http://support.amd.com/us/gpudownload/Pages/index.aspx), you'll see that the Raedon Xpress 200 (no 'G,' sorry) actually has an official Linux driver for it.

(Under "Integrated Motherboard Graphics" > "Radeon Xpress Series" > "Radeon Xpress 200" > "Linux x86" or "Linux x86_64")

It's worth a shot if you haven't done it already.

Sorry, I don't know much about graphics cards, but no one else seemed to have anything to say...

---

### Post by MelodiesonMusic on 2010-11-26
ahh, you're a genius! I haven't actually downloaded it yet (i've decided to back everything up first) but you're very right, it's there and it seems to be supported. Thank you thank you thank you :) Not only for helping me, but being the ONLY person to help me.

---

### Post by MelodiesonMusic on 2010-11-26
> **MelodiesonMusic said:**
> ahh, you're a genius! I haven't actually downloaded it yet (i've decided to back everything up first) but you're very right, it's there and it seems to be supported. Thank you thank you thank you :) Not only for helping me, but being the ONLY person to help me.
it worked, and apparently that wasn't the problem. =\ The loading screen looks a little better though, now it's yellow and i can see the outlines of the diamond that's supposed to be in the middle :)

---

### Post by racie on 2010-11-28
Hmm... well have you tried posting on the Wine forums?
[http://forum.winehq.org/](http://forum.winehq.org/)

---

### Post by MelodiesonMusic on 2010-11-29
> **racie said:**
> Hmm... well have you tried posting on the Wine forums?
[http://forum.winehq.org/](http://forum.winehq.org/)
I did, but i didn't get much help. Someone directed me to the playonlinux forums and the guy there basically told me i was doomed and that there was no possible way for the game to work under ubuntu. The wine page says that it works perfectly though. I'm determined to get this thing working, i've found a new place to download my driver from, but it's a .exe file and when i run it under wine it says I need to update BIOS. I guess i just need to backup my files and get to experimenting.

---

### Post by racie on 2010-12-01
Well first of all, installing any type of Windows driver shouldn't work under Linux.

Second, I'm sure the game works great under Wine in most cases, but the issue seems to lie with your graphics card.

I've read somewhere that your card might not be supported by X.org, but I really have no idea how it all works.

Here's the website though: [http://xorg.freedesktop.org/wiki/](http://xorg.freedesktop.org/wiki/)

Also check out: [http://www.x.org/wiki/VideoDriverFAQ](http://www.x.org/wiki/VideoDriverFAQ)

and [http://www.x.org/wiki/Projects/Drivers](http://www.x.org/wiki/Projects/Drivers)

---

### Post by phythagorous on 2011-01-05
hey. your not the only one with this problem. my sims 3 also has block bubbly and unreadable text and that warning window also pops up on mine as well.. so i don't think it is a problem with your computer specifically. I was looking around and it seems as if in order to play sims 3 on ubuntu you have to download a crack for the game because of some complication in the wine program. 
i noticed you posted this a little bit ago and i was wondering if you ever figured out how to play the game..
: ]

---

### Post by MelodiesonMusic on 2011-01-07
no, not really :\ I'm reinstalling and trying again, but if that doesn't work i'll have to partition my drive with a minimal install of windows... gr -_- Have you tried the crack?

---


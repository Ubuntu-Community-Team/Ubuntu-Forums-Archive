---
title: "Having a REALLY bad time with Ubuntu Studio"
date: 2008-12-02
forum: Ubuntu Studio
---

### Post by Snowflake128 on 2008-12-02
I've been trying to set up Ubuntu studio on my computer for a while now, and it's really not working out too good. :(

For a while it seemed to be sort of working but then I started getting glitchy sound especially when recording when it would just drop out for seconds at time and the resulting audio file jumps and misses out bits.

I started removing all the other audio cards except for the audiophile 2496, and then I tried changing the pci slot.

This last move reset all my settings and now even audacity doesn't work. I can still play things in the little mp3 player and the media player thing and they play fine but audacity takes ages to load and when it loads if you try to change the preferances to alsa 2496, the program locks out for a few seconds as soon as you hit the okay button. After that even going into the preferances dialog causes that action.

Playback and recording cause audacity to moan.

I'm really frustrated as I've wasted days on this and I'm really tempted to install win2k instead but I know that if I do I won't ever really be able to go back to linux because I wil be locked in whereas right now I'm moving away from an ancient windows 98 machine.

I'm quite unhappy about it all and welcome any suggestions for solving the problems.

---

### Post by Snowflake128 on 2008-12-02
I think the problem seems to be mostly Audacity, maybe I got a bad version or something. I changed the settings to point to Jack and then it wouldn't let me change them back to anything else without starting and restarting etc.

I get the impression that Audacity is the only real choice for an audio editor in Linux at the moment?

---

### Post by nalmeth on 2008-12-02
>  I get the impression that Audacity is the only real choice for an audio editor in Linux at the moment?
Absolutely not.

First of all, install the realtime kernel by installing the linux-rt package.

If you've installed JACK, and Audacity is causing problems I would ditch it. Try one of these other audio editors to see if the problem is with Audacity specifically.

Jokosher (simple), Rezound (more complicated), Ardour2 (more complicated but most powerful and useful)

Handy tip: in the terminal, type this command to search for other audio editors:
```
apt-cache search audio editor
```

Its not totally clear what the root cause of your problem is, but trying the realtime kernel should rule out any latency problems with JACK, and trying other audio editors should rule out problems with Audacity specifically.

---

### Post by Snowflake128 on 2008-12-03
> **nalmeth said:**
> Absolutely not.

First of all, install the realtime kernel by installing the linux-rt package.



Isn't that installed by default in ubuntu studio?

> 
If you've installed JACK, and Audacity is causing problems I would ditch it. Try one of these other audio editors to see if the problem is with Audacity specifically.


I've got Jack installed but not really set up. The problem seems more to do with Audacity trying to talk to the Alsa layer and getting upset. It's very weird as most of the other apps seemed to be playing audio fine but there were a few exceptions.

I tried playing with Ardour brifly which seemed to show the audio coming in visually on the metering thing but then didn't actually record anything, but then I hadn't really configured Jack so that is no suprise really.

> 
Jokosher (simple), Rezound (more complicated), Ardour2 (more complicated but most powerful and useful)


Those look really intresting. I think it's good to have a choice of audio editors as sometimes you just want something simple with a straightforward UI and othertimes you want something more powerful.

> 
Handy tip: in the terminal, type this command to search for other audio editors:
```
apt-cache search audio editor
```


Unfortunately theres no internet connection in the studio, so the whole apt thing quickly becomes a bit of a pain.

> 
Its not totally clear what the root cause of your problem is, but trying the realtime kernel should rule out any latency problems with JACK, and trying other audio editors should rule out problems with Audacity specifically.

Definitely. It's very odd. I've installed win2k for the time being as I've spent days trying to get Linux to do its thing. I still have another hard disk with Ubuntu Studio installed tho. Win2k seems to work right away although I had to download drivers for the AGP card as windows didn't detect it. (Nvidia GE Force2 MX200). It made me think if maybe Linux doesn't like the AGP card either. Anyway I'm trying to run the Linux apps like Hydrogen that are available for windows in the interim. I suspect Linux might just not like something about my hardware. :(

---

### Post by Stochastic on 2008-12-03
what version of Ubuntu are you running?  what version of audacity is installed? and what's the output of ```
uname -r
```

---


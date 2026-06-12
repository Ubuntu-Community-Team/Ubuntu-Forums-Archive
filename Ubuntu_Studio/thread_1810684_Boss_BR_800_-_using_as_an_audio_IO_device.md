---
title: "Boss BR 800 - using as an audio I/O device"
date: 2011-07-23
forum: Ubuntu Studio
---

### Post by JWD1973 on 2011-07-23
Hi,

Well this is a 1st!

Having something to shout about the same day as I joined this forum.

Why the excitement?

Well  - I've been trying to get myself weaned off MS Window$ as I simply don't think that it is the be all and end all of music production for PC users. Plus - in all honesty, getting a Mac up to spec would take me far out of the reaches of my budget.

So, with what little cash I had to spare, I purchased an older PC, but with enough processing grunt to do what I need to do.

Which TBH - is pretty simple. A bit of MIDI and audio sequencing.
So, yeah - I got an old, but pretty high spec PC (MSI motherboard with AMD dual core processor- 2Gb of the fastest ram it could cope with, a fresh new 500Gb SATA HDD.
There's a few other additions - like a mulit-port USB/eSATA/Firewire where the old floppy drive was, just so I could add peripherals without bumbling round the back every 5 minutes.
The audio side was something I wanted to be able to do, even if the PC crashed or was otherwise non-usable.

So I went for the BOSS BR800 - which as well as being a pretty self explanatory standalone digital multi-track recorder can also be used as an external soundcard, as well as a controller for DAW programs. 

For which, of course there was some support for Linux - but not much.

So I asked one of my friends who is kind of a genius at this kind of thing to put together a patch so it could work as an audio interface through Linux.

That part of the process is now done, we tested it all on his system last night and it both played audio and recorded audio without any issues.

What I want to try and do here, is to document the process of it's instillation and how well it works... giving heads up about strange behavior or abnormalities in use. 
Currently, music wise - I come from a hardware only background...
for a long time I have had an innate mistrust of using a PC as a "all in on box" solution and TBH still have a fair bit of outboard that I will be using to help reduce lagging and bogging down the PC with excessive number crunching....

So yeah.

Very excited, progress is pretty slow setting things up (I am no *code monkey at all *- but I am learning slowly)

Currently road testing 11.04 Ubuntu and am having a look at the "studio" release to see what all the fuss is about... so yeah, will give some FB about that soon.

Kind of lucky ATM as there's nothing really of "mine" on the PC in question - so if it goes all pear-shaped a total "cold reset" is not going to worry me.

So yeah - exciting times and I'll keep y'all posted with links, stuff and the like as time goes on


:D

---

### Post by marseille on 2011-07-26
Oh nice! Like this post:D 

2 Thumbs Up :popcorn:

---

### Post by nardelli on 2012-02-08
Do you really made the BR-800 works on Linux, I mean, the BR-800 was recognized as control surface? How do you (and your genius friend) did it?

My device appears on lsusb but I can't see it as Midi Interface. Any suggestions?

Thanks!

---

### Post by JWD1973 on 2013-02-18
> **nardelli said:**
> Do you really made the BR-800 works on Linux, I mean, the BR-800 was recognized as control surface? How do you (and your genius friend) did it?

My device appears on lsusb but I can't see it as Midi Interface. Any suggestions?

Thanks!

Well, the code that my friend put together (the main issue was that the Roland company had 'hidden' the details of the machine's identity codes, so the working out of that was one of the main issues)... however, the details are now all integrated from the patch he wrote into the new Ubuntu distro and as a result, anything from 12.04 onwards (both 32 & 64 bit) work pretty much out of the box.

However, as an external sound card and audio interface(which really is all I need)... the BR 800 has served me well since the days of 11.04 (my version was 'tweaked' with the patch for it added in, prior to it going live for stability testing).
On my system, the BR shows up as hw :1.0 USB AUDIO device, these details are shown in the input/output when using Audacity....    
HOWEVER, as far as I know there's no MIDI set up for the internal workings of the BR 800 (no MIDI in/out and so on... ) , there's a kind of clunky workaround that I've looked at (which is utterly pointless for my needs): found here - [http://songcrafters.org/community/index.php?topic=8387.0;wap2 ]("http://songcrafters.org/community/index.php?topic=8387.0;wap2")

---

### Post by wildmanne39 on 2013-02-20
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


---
title: "New and looking for help"
date: 2012-11-12
forum: Ubuntu Studio
---

### Post by nickgee667 on 2012-11-12
Hey, my name is Nick Gee, and I'm a musician (do everything really).  I started off 8 years ago using FL Studios, and then switched in 2010 to Reason by Propellerhead.  

I ended up getting frustrated by Windows a few weeks ago and installed Ubuntu, and then found out about Ubuntu Studio, so I just installed that last night.

I'm not sure how to do anything in it really.  I want to be able to synthesize instrumental tracks using my computer keyboard as an input device, and also be able to record vocals onto it.  I know you can connect the JACK thingy to the Ardour thingy and do stuff or whatever.

Not looking for anyone to fully explain these things to me, just if you know of any full tutorials of Ubuntu Studio, could you help me out?

Thanks.

Looking forward to being a member of this community, and seeing what everyone else is doing with it too!

---

### Post by ibjsb4 on 2012-11-12
A good way to search the ubuntu forums for information.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Ubuntu+Studio&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Ubuntu+Studio&as_qdr=all&sa=Google+Search&lang=en")

Thats the only tip I have as I do not run studio.

And welcome to the forums  :)

---

### Post by slickymaster on 2012-11-12
If you care to bother, there are a few more alternatives, whether they are better or worse, I can not say it, but you can always give them a chance:

[Linux MultiMedia Studio]("http://lmms.sourceforge.net/")
[ArtistX]("http://artistx.org/blog/")

---

### Post by nickgee667 on 2012-11-12
Hey, thank you ibjsb4.  I will definitely check that out!

slickymaster, I did install LMMS on my regular Ubuntu installation, and then I installed Ubuntu Studio, and I just installed LMMS this morning before work.  Can't wait to get home and do it, lol.  I had a chance to play around for like 5 or 10 minutes on it, kinda like FL, I will just need to find a huge library of instruments and sounds to add to it.

---

### Post by slickymaster on 2012-11-12
Maybe you should take a look at this post:

[http://ubuntuforums.org/showthread.php?t=2072846](http://ubuntuforums.org/showthread.php?t=2072846)

---

### Post by nickgee667 on 2012-11-13
Alright, thanks.

I'm already experiencing an issue I thought I would.  Where I've used different audio software in the past, I'm sort of familiar with the basics, they are just in a different place now.  I figured out how to record from Hydrogen into Ardour, so I put a drum track in there that I made, and then I was trying to use JACK to connect my LMMS to Ardour to record in my piano that I made, and I couldn't get that working.  I'm assuming LMMS can't be used with JACK or something?

---

### Post by slickymaster on 2012-11-15
Take a look at [LMMS's Audio Settings]("http://lmms.sourceforge.net/wiki/index.php/0.4:LMMS_Settings"):

The Audio Interface sets the mechanism that LMMS uses to produce audio. You can select from:
[LIST]
[*]ALSA (Advanced Linux Sound Architecture)
[*]dummy (no sound output) - useful only for testing whether LMMS is functioning correctly.
[*]JACK (the Jack Audio Connection Kit)
[*]OSS (the Open Sound System)
[*]SDL (Simple DirectMedia Layer)
[/LIST]

_**JACK is the most advanced of all these interfaces, but requires a working JACK daemon to connect to in order to function.**_
ALSA is the default and is standard on almost all modern Linux systems.
Support for PulseAudio may be coming in the future.

With each interface, you can select the actual device and the number of channels used by LMMS. These are interface-dependent settings and should be left at their defaults unless you have a good understanding of the interface in use on your computer.

---


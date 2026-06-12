---
title: "Pro Audio On Ubuntu"
date: 2010-12-12
forum: The Cafe
---

### Post by mr_sausage on 2010-12-12
Hey.

I am a long term pro audio user who has recently discovered Ubuntu as a stable alternative OS to WIndows and OS x.

Over the last 15 or so years, I have used mostly Mac OS to run Midi/multi track recorders and sequencers to record and create music. although I have also used Windows OS for some time.
I turned to Ubuntu after getting spyware hacked on the Mac, and once I started using it, I realised how good it was in terms of stability, price (free) and speed, so thought that it may also be a good OS to use for multi track recording / midi sequencing.

At the moment I use Ubuntu for running email, although would like to run pro audio apps as well.

I was wondering if there were any developers out their planning to Port pro audio applications to Ubuntu so engineers / musicians can use Ubuntu instead of the other popular OS's.

The applications that I would be most interested in seeing ported (and sold for same price as on other OS) are as follows:

Avid/Digidesign Protools
Apple Logic Pro
Propeller Head Recycle
Propeller Head Reason
Propeller Head Record
Stienberg Cubase
Native Instruments Plug Ins including Traktor
Waves Plug Ins
Focusrite DSP plug ins with Liquid Mix
UAD DSP hardware support and plug ins

I think that Ubuntu has tremendous potential. Especially where portable PC's are concerned.
I wish the developers luck in their developments :-)
:KS

---

### Post by Frogs Hair on 2010-12-12
I can't answer your questions about specific features you listed but take a look at the link. Ardour is in the software center along with some other music apps . See the plugins page at the Ardour site. [http://ardour.org/](http://ardour.org/)

---

### Post by toupeiro on 2010-12-12
[http://ubuntustudio.org](http://ubuntustudio.org)

---

### Post by cchhrriiss121212 on 2010-12-12
> I was wondering if there were any developers out there planning to Port pro audio applications to Ubuntu so engineers / musicians can use Ubuntu instead of the other popular OS's.
I don't think there is any money in it for the big companies (extra development costs, extra bug fixes, extra support etc.). FOSS developers have been developing their own solutions for some time based around the jack audio server. Linux has it's own set of plugin standards: LV2, LAPSDA and DSSI. Plugin support for proprietary stuff (VSTs etc.) is slowly improving but it is still not usuable without much fiddling.

Check out what packages you get in the Ubuntu Studio release, Ardour has been mentioned but it is just one example. Some of FOSS is not on par with proprietary solutions right now but I've seen big improvements since I first tried them out, which was only a year ago.  

Upsides of Linux pro audio today:
Cost - none
Modular - jack allows you to connect audio wherever you like
Stability - once you get it set up, jack can be relied on for long periods

Downsides:
Lack of polish - both in terms of looks and ease of use
Harder to set up - jack is a real head-scratcher for new users
Hardware support - don't expect this to change any time soon as it requires the soundcard manufacturers assistance or massive reverse engineering
Plugins - a good selection but still small compared to other platforms

---


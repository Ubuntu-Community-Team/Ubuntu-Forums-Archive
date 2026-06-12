---
title: "openlp Church Presentation Software"
date: 2010-02-15
forum: Ubuntu Christian Edition
---

### Post by oneinch on 2010-02-15
[http://sourceforge.net/projects/openlp/](http://sourceforge.net/projects/openlp/)

Just stumbled on it while looking for a java project to hack on

---

### Post by stlsaint on 2010-02-17
nice...im soon looking to buy a projector.

---

### Post by oneinch on 2010-02-19
Projectors ROCK. wish I could play my xbox360 on one.

---

### Post by LaneLester on 2010-09-13
At my new (to me) church I'm moving into the video control position, and Presentation Manager is the software I'm inheriting. I've watched the videos and read the manual, but there are still some bugs (I think) and confusion on my part.

After I get familiar with the new environment, I want to look at open source/cross platform (Linux at home/Windows at church) software as an alternative to what we're using. I plan to consider OpenLP, KWorship, and OpenSong as possibilities.

Have you compared any of these?

Lane

---

### Post by oldsam on 2011-05-21
OpenSong doesn't work too well on Linux and the old version of OpenLP doesn't have a Linux version. OpenLP 2.0 will also run on Linux, but it's still beta at the moment.

You can try ExpoSong ([http://exposong.org]("http://exposong.org/")).
It works on Linux and Windows and has a simple and easy to use interface.

---

### Post by LaneLester on 2011-05-21
Thanks, oldsam. I've just downloaded both OpenLP beta and ExpoSong and will give them a look.

Since my previous post I've gained considerable experience with Presentation Manager, the commercial Winapp we have at church. In spite of its bugs and quirks, it's very powerful and flexible. More to the point, I'm not the only person who uses it, and this is the biggest barrier to making a switch.

PM does announcements, songs, and Bible verses, all of which I use in each service. I suspect the Bible function may be the stopper for other programs.

Another nice feature of PM is, in a slideshow, each slide can have a different exposure time. A glance at ExpoSong's site suggested that all slides have to have the same times, not a good thing.

Lane

---

### Post by oldsam on 2011-05-25
> **LaneLester said:**
> 
Another nice feature of PM is, in a slideshow, each slide can have a different exposure time. A glance at ExpoSong's site suggested that all slides have to have the same times, not a good thing.

Lane

You mean that if you use a timer, you cannot set a different time to each slide? Yeah, that's true, but I wonder if that's something many users need.

Feel free to share your thoughts about ExpoSong when you have tried it out, you are talking to a developer of it ;)

---

### Post by LaneLester on 2011-05-25
> **oldsam said:**
> You mean that if you use a timer, you cannot set a different time to each slide? Yeah, that's true, but I wonder if that's something many users need.
It may just be me, but I want the text-heavy "Upcoming Events" on the screen a lot longer than "Welcome!". :)

> Feel free to share your thoughts about ExpoSong when you have tried it out, you are talking to a developer of it ;)
Thanks, I'll do that.

Lane

---

### Post by who_da_fly on 2011-06-08
OpenLP currently also currently uses a single time for all the slides. But, that doesn't mean you can't log a feature request. You'll find that a number of folks in our community have had their feature requests implemented sooner than they thought.

Oh, I say "our" because I'm the OpenLP project leader :-)

---

### Post by bcschmerker on 2011-08-15
This may be a useful application for a [project on which I am fielding recommendations]("http://ubuntuforums.org/showthread.php?t=1776921") (none received as of 14 August 2011).  I am currently testing an eMachines®/Acer® EL1210-09 (Advance Micro Devices® Athlon 64® LE-1620, nVIDIA® MCP78S chipset/GeForce® 8200 IGP, VGA plus HDMI), augmented with a Shuttle® PC6200002 PSU (in for the stock---and mis-built---LiteOn® PS-5221-06) and an Asus® EN210/DI/512MD2(LP) PCI-Express x16 VDA, as a possible projection computer under Ubuntu® 10.04.2-LTS, AMD64 Edition.  The nVIDIA® X server (from ubuntu-restricted-extras) picked up both the planar GF8200 and add-on GF210, and registered them as individual Video Devices; I need to know whether it is necessary to have them as parts of one X.org desktop to use the smaller of two displays as a projector for Open LP, Sun® OpenOffice.org, or similar presentation software.

**Update:**  OpenLP&#8482; does require that the VDA's be integrated into a multipane desktop, e.g., by using Xinerama in the nVIDIA® X server (package: nvidia-current).  Due to the better support of specific multimedia functions in KDE&#8482;, I have replaced the earlier Ubuntu® installation with Kubuntu® 10.04.3-LTS, AMD64 Edition.

---


---
title: "Koala Mini Questions"
date: 2008-02-27
forum: System76 Support
---

### Post by BladeMelbourne on 2008-02-27
Hi,

I am looking at replacing my aging PPC Mac Mini (running Hardy) with a Koala Mini. I have some questions...

1) Does the power supply adapter auto-switch between 110v and 240v? I live in Australia, so I need 240v operation. (I'm thinking I will have to have it delivered to a friend in the US, who will need to ship it to Melbourne.)

2) Is the Intel graphics chip fully supported by the xorg Intel driver? Is 3D/OpenGL performance decent? Are the adapter and driver capable of 1920x1200 resolution?

3) Does a standard Gutsy installation CD contain all the drivers required by the Mini, or does it ship with a modified CD that specifically suits the Mini?

4) Does the Mini work with Windows? I can hunt down and install drivers, however I would like to know in advance if it is even possible. I need Visual Studio for work, so I can't fully switch. Dual boot would be the way I would go.

5) It's a 64 bit machine... so can you run the 32 bit flash plugin easily? Running PPC Linux has caused me endless frustrations without Flash (and gnash just isn't good enough). Thanks Adobe :-|

Thanks for any advice!

Mike

---

### Post by thomasaaron on 2008-02-27
> 1) Does the power supply adapter auto-switch between 110v and 240v? I live in Australia, so I need 240v operation. (I'm thinking I will have to have it delivered to a friend in the US, who will need to ship it to Melbourne.)

Yes. Just FYI, though: We don't ship to Australia.

> 2) Is the Intel graphics chip fully supported by the xorg Intel driver? Is 3D/OpenGL performance decent? Are the adapter and driver capable of 1920x1200 resolution?
It better! We sell a 1920x1200 monitor for it! So, yes.

> 3) Does a standard Gutsy installation CD contain all the drivers required by the Mini, or does it ship with a modified CD that specifically suits the Mini?

It comes with a Windows drivers CD for those wishing to dual boot. We do not ship a restore CD. If you need to restore, you can use a standard Ubuntu 64-bit install CD and then install our System76 driver and run it.

> 4) Does the Mini work with Windows? I can hunt down and install drivers, however I would like to know in advance if it is even possible. I need Visual Studio for work, so I can't fully switch. Dual boot would be the way I would go.

Yes. See #3.

> 5) It's a 64 bit machine... so can you run the 32 bit flash plugin easily? Running PPC Linux has caused me endless frustrations without Flash (and gnash just isn't good enough). 
Thanks Adobe 

You can just download 32 bit firefox and do it that way. We also have a workaround for using 32-bit flash with ndiswrapper on 64-bit firefox. Incidentally, it comes with flash installed and working.

---

### Post by BladeMelbourne on 2008-02-27
Thank you! Your answers are those I was hoping to hear.

Except for not shipping a **Koala** Mini to Australia :p
I have a couple of colleagues in the US that can help, so no biggie.

Thanks again :-)

---

### Post by BladeMelbourne on 2008-02-28
For those reading... nota bene.

nspluginwrapper ([http://gwenole.beauchesne.info/projects/nspluginwrapper/](http://gwenole.beauchesne.info/projects/nspluginwrapper/)) is meant to facilitate running Netscape/SeaMonkey/Firefox plugins on different architectures than which they were compiled.

ndiswrapper [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/) is for making some wireless ethernet drivers devices work under Linux.

---


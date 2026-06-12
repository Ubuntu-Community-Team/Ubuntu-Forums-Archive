---
title: "Reducing electric bill? (Media server on 24/7/365)"
date: 2015-08-08
forum: Server Platforms
---

### Post by Donny Bahama on 2015-08-08
Does anyone have suggestions for minimizing power consumption for a (media) server that's on 24/7/365? In addition to being the backend for my audio and video libraries, I hope to get Plex setup so that I have access to all my music, movies, and TV shows from outside the house. But on the other hand, it'd be nice if I could automatically put it into power saving mode when I'm not using it -- but only if it would wake up reliably whenever I want to use it.

---

### Post by Bucky Ball on 2015-08-09
Two things to start with that have nothing to do with software: I use Western Digital green drives which spin down (built into the drive and not dependent on the OS) and use about a third less power than the average hard drive; most important thing in the box, the power supply unit. Are you running a media server with a couple of hard drives and you have a 1000w power supply? Is it a generic silver box? If you machine is a server with a couple of drives you could halve or more the power supply. As for silver box generic PSUs, don't use them. They are good heaters in Winter but unreliable, imho unsafe, and <70+ efficient. Your money goes to heat, not power.

Use a PSU calculator to see what size PSU you need (there are a few online, try the Antec site) and then buy a quality 80+ or 85+ PSU. That is clearly marked. Bit more cash but will last for ages (probably longer than the machine) and have every safety switch you will ever need. There you go. Start saving. :)

(PS: I run an Odroid, like a Raspberry Pi, as a media server with a 1Tb WD hard drive hanging off it. The hard drive dock plugs directly into the wall so powers itself and the Odroid has regular 5v power adapter that plugs straight into the wall socket. You don't need a lot. Good luck.)

(Bit of a rant but energy-efficient computing hardware is one of my obsessions, or used to be an obsession I should say. :))

---

### Post by Donny Bahama on 2015-08-09
Thanks for the response, Bucky Ball! It probably would have helped if I'd given some system details.
There are 13 drives (8 x 3.5" and 5 x 2.5") plus a Blu-ray drive. Too late to buy WD Greens so I guess I'll have to make sure to configure Ubuntu Server to spin them all down. (How/where do I configure that?) As for the PSU, it's a Thermaltake 500W, 80plus Silver rated.

Any other suggestions? The server is headless so no GUI. Not sure where/how to set power/saving options in general. I manage the server with Webmin but I don't think there's any power settings there.

---

### Post by Filipe_ribeiro on 2015-08-09
what is your cpu? for power savings, better to use green Hard drives, depending on the cpu you can always under clock it and undervoltate it, unplug as many cd drives or fans as you can.
I use myself the athlon 5150 25w 4 cores, its a cheap setup and work great with my plex.

PS: As the OS drive i use an 2.5 sata green, as it use little power to run

---

### Post by TheFu on 2015-08-09
There are lots of ways to attack this.

Where I live power isn't nearly as expensive as in some other places.  The household monthly bill is $75-ish with 6 systems running 24/7/365 with all the other modern things in the house (not including A/C). 3 of those systems are lower power and the other 3 normal.  The full desktops w/ Core i5 and Core i7 CPUs suck most of the power.

I do not enable any power-saving features, except to power off the monitors connected and let the CPUs slow down when not needed. I specifically disable any drive spin-down. Saving $3/month just isn't worth it to me.  Plus suspend has never worked well. Even on my newest netbook, coming out of suspend sometimes fails - usually it is the audio that breaks.  It doesn't always fail - perhaps 1 out of 6 attempts. Just enough to be a nag. I spent months trying to solve it and never did.  I've seen similar issues on all hardware. Not worth my time.

For my needs, it is more about noise levels than absolutely minimizing power use.  Using a highly efficient picoPSU might be the answer for reducing noise and power needs. I have an 80W version and it is completely silent. These are designed to be use with MicroITX motherboards. Going for lower power CPUs is the first step.  A 35W CPU is really amazing these days.

---

### Post by Filipe_ribeiro on 2015-08-10
picoPSU are a great idead, but may miss some security features that ATX psu have, there is also boards that allow to plug laptop chargers, like mine ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813157491](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157491)), the best way to reduce power, is to lower cpu frequency and voltage.

---


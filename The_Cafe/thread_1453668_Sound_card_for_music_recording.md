---
title: "Sound card for music recording?"
date: 2010-04-13
forum: The Cafe
---

### Post by BinaryFeast on 2010-04-13
I am going to buy a new stationary PC. In addition to media and gaming I want to use it for recording guitar and keyboard, but I am unexperienced in the area of PC recording and would like some advise. What should I think about when choosing the components, specifically the sound card? Any experts on here?

---

### Post by pepito7 on 2010-04-13
[SIZE=2][COLOR=black]Just built this new rig principally as a music server.

Intel Core i5
Gigabyte "Silent Cell" G-force 9800GT
Corsair 4GB DDR3 1600 PC3
Gigabyte GA-P55A-UD4[/COLOR][/SIZE]

[SIZE=2][COLOR=black]Bought this sound card - [http://www.esi-audio.com/products/julia/](http://www.esi-audio.com/products/julia/)
[/COLOR][/SIZE]'A 4in/4out audio interface with swappable I/O socket'
[SIZE=2][COLOR=black]
To my ears sounds great and does everything I need it to do.
Worked straight out of the box with Ubuntu 9.10.
Highly recommended.
[/COLOR][/SIZE]

---

### Post by cchhrriiss121212 on 2010-04-13
Depends on a few things really, do you want a midi port for the keyboard? Do you want to have a pci/usb/firewire device? I use a m-audio delta44, which is all I need and is fully linux compatible. You can check the alsa database for supported devices:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
Here's a recent thread form the studio forum:
[http://ubuntuforums.org/showthread.php?t=1449800](http://ubuntuforums.org/showthread.php?t=1449800)
In addition to a sound card you might want a cheap pre-amp for your guitar (electric I assume) so that you can get a decent sound (a boss stomp box will do in a pinch). You can use guitarix and rakarrak for amp simulation and effects.
There are plenty of open source audio apps out there, but you should be prepared for setting up jackd (the best sound server) as it is not configured well out of the box.

---


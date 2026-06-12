---
title: "Wanting to try Ubuntu Studio, but scared of drivers, or lack of.."
date: 2012-04-24
forum: Ubuntu Studio
---

### Post by birdie_in_texas on 2012-04-24
I have a windows machine with Pro Tools 10 and it is the biggest pain in the butt ever..most of the time it does not even start, forcing driver re-installation and a reboot...if not more.

I am sick of it..  

I only have Pro Tools because it came with a piece of equipment, I would like to use something else and read about Ubuntu Studio.

I do not mind setting aside on of my PC's and putting Ubuntu on it, but I am complete Ubuntu (linux) newb and have no idea what I am doing.  I have tried Ubuntu before, but it did not work out well with the family unit, and I have had to go back to familiar Windows territory on behalf of my sanity..

My fear is that none of my interfaces will work, and I do not even know how to install a driver in Ubuntu/Linux, even if there is one.

I have both USB (tascam 144mkii) as well as Firewire (m-audio 410) but do not know if I can even use these devices.  

Also, several of my preamps are USB interfaces in and of themselves, but I have looked and not a single device I own has any dedicated drivers, at least not on the manufacturers website/support sections.

Is there a knowledge base for newb people such as myself somewhere that me and google just cannot find?

Any help would be most appreciated.

Thank you in advance.

Birdie :)

---

### Post by jejeman on 2012-04-24
That firewire interface is not supported
[http://www.ffado.org/?q=node/24](http://www.ffado.org/?q=node/24)

---

### Post by birdie_in_texas on 2012-04-24
I did not find that before..

I also cannot find anything like that telling about the Tascam USB interface..

---

### Post by sgx on 2012-04-24
Hi, several people have various Tascam devices working.
There may be a Tascam firmware in synaptic. Linux
does not
use drivers, like windows, so support for each device comes
from the kernel, alsa, and specific kernel modules.

Go to the qjackctl wiki, links 4  and 8 will show how
to set up jackd and its qjackctl gui.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

google ubuntu tascam usb, lots to read, so take notes.

[http://download.cnet.com/SiSoftware-Sandra/3000-2086_4-10556571.html](http://download.cnet.com/SiSoftware-Sandra/3000-2086_4-10556571.html)

Pro-tools techies might help if you give them a sisoft sandra
report, and concise story of what happens.

Download the app, and run it, it chronicles the
nooks and crannies of your system, and they cross reference
areas that have been problems for people with similar systems.
Report generation takes time, so choose a free period with
other things to do.
Cheers

---


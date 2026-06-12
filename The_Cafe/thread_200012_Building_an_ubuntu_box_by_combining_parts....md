---
title: "Building an ubuntu box by combining parts..."
date: 2006-06-19
forum: The Cafe
---

### Post by K2712 on 2006-06-19
...from two old computers?  Is this possible?

I've always thought about building my own system, but haven't done it for the same reason I haven't bought a new comp. in a long time....$$$$.  The good thing is, I have two old computers, an HP and a Compaq, both ~ 6 years old, both Pentium systems.  How feasible is it to build a single computer using both processors, memory, etc?  I know this would be a complicated task taking alot of time and effort, but that would not dissuade me if it were possible. 

Any comments?

---

### Post by K.Mandla on 2006-06-19
Only that you should go for it. My systems are all cobbled together from other machines, and I'd bet most folks here are working on homemade rigs. 

It's (usually) much, much cheaper than buying an entire machine new and assembled.

My only advice is to learn about which parts work with each other, and which ones don't. Have fun! (And always unplug it before you open it. ... I've made that mistake, and it got my attention. :) )

---

### Post by glotz on 2006-06-19
You can select the best compatible parts from the two but you cannot combine the processors. It's not too complicated.

If they're pentium I class machines, you'll likely have better luck with Xubuntu or Damn Small Linux or some other distro. I mean for desktop use. As a *headless* or *desktopless* small private server or as a firewall that'd do probably just fine.

Now go fetch that screwdriver! :)

My box is salvaged together too.. A speedy Pentium III 450@527 MHz with whopping 192 megs of RAM. Geforce2. SB 16. Running 6.06 with Gnome. A little bit jerky but works for me.

---

### Post by mscman on 2006-06-19
I'm not so sure about using both processors, new dual core procs. (and dual-CPU machines) are specially designed to work with specific chips.  Memory may transfer to one machine, it just depends on the types the machine's motherboards use (Compaq and HP are fairly proprietary...)  As far as hard drives and graphics cards go (assuming the graphics cards aren't onboard), those should transfer fine.  I would probably do this:

Choose the machine with the faster processor.
Transfer the other hard drive(s) (and graphics cards & network interfaces if you'd like)
Transfer the memory and see if the machine starts up (try just one stick from the other machine and see if it works, then try all of them).

If all of the above work, you may get a little more oomph out of your system.  I would also maybe recommend using Xubuntu or do a server install and Fluxbox to improve performance.

Creating one super-computer with two CPUs and motherboards is an idea I've tossed around before (actually running two separate computers in one case with a KVM switch and shared monitor so I can run Linux and Windows side-by-side and connected via internal LAN), but it would take an insane amount of work and time that I don't have on my hands.  I don't think you'll be able to use all of the parts in one machine (although you could create a two-computer cluster....)

---

### Post by nuvo on 2006-06-19
You can't really put the two CPU's into one system unless you've got a dual CPU board to put them in, and even if you do, they'd have to be compatible.
With memory, you need to check to see if they both use the same type (incorectly pairing RAM can cause problems and if it's completely wrong, it won't even fit the board).
Using the HDD's is pretty simple.
You just need to read the back of the drive, set the jumper as needed and plug it in.
Graphics cards shouldn't pose a big problem so long as you know what type the card is.
If it's a PCI graphics card you want to use, it should be fine as pretty much every main board supports PCI.
If it's an AGP card, just make sure the board you're plugging it into has an AGP slot.
If it's an on-board GPU, these can't be swapped around, so if you wanted to change the graphics system, you'd need to add a graphics card to take over from the inbuilt GPU.
My machine was built from two older systems (A 953Mhz Duron based Q-tech POS and a HP Pavilion) and is now happily purring along as a 2.53Ghz Celeron based system with 2x40Gb Seagate HDD's, a pretty spacious case, 256Mb or RAM (the Q-tech RAM wasn't DDR) and what little trinkets I've actually bought for it over the last year (an nVidia GeForce 6600 graphics card, a belkin WiFi card and a 27" DVI widescreen monitor).
All I need is some more RAM (mainly just so I can say it's there, Ubuntu runs nice on my current rig) and a better case (this one doesn't have vents, it has full blown holes in it with wires sticking out because I liked my front USB ports and the case didn't have them, so I ran them out of an optical drive bay and broke a 3.5" cover trying to get something else sorted) and I'll be set for the next few years of programming and random Linux adventures.

---

### Post by K2712 on 2006-06-19
I appreciate the responses.  I had the feeling that putting two processors into one machine was way beyond my ability, I think I just needed to hear someone else say it.

---

### Post by IYY on 2006-06-19
Taking all the memory and harddrives from one and moving them to the other is very easy, though.

---

### Post by nalmeth on 2006-06-19
> (And always unplug it before you open it. ... I've made that mistake, and it got my attention. :smile: )
Elaborate. I can imagine a couple scenarios, but have never had anything bad happen to me personally. I usually always unplug first, but sometimes I forget, and realize it when I have both my hands in the beast.

Also, I never use those static arm-bands. Is this what happened? You zapped a HD or something?

---

### Post by phantomreaper on 2006-06-19
I use ubuntu 5.10 quite fine.

I have a Pentium 3@876mhz, 128mb RAM, 40GB HDD, 32 MB Intel Onboard (I officially hate Onboard Cards), Intel Integrated Audio, Network Card.

Ubuntu runs like a breeze!

---

### Post by bodhi.zazen on 2006-07-11
nalmeth:

I was perusing this forum and came here. I used to work on my box occasionally, well frequently, well almost always, plugged in.

1 week ago I fried my sound card. Apparently I had a build up of static electricity. I went to unplug my speakers, and move to my other sound card --> SPARK --> SMOKE --> Hey that was mu nice sound card!! At least it was not my CPU or HD.

This was a first time experience with computers and unwanted electrical discharges. Now I unplug.

---

### Post by bodhi.zazen on 2006-07-11
K2712:

HD, video cards, sound cards, ethernet cards, CD/DVD should all be interchangable.

Memory is +/-.

CPU. Interesting thought, but no. Not even close.

---


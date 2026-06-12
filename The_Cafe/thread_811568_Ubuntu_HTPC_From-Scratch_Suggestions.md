---
title: "Ubuntu HTPC From-Scratch Suggestions"
date: 2008-05-29
forum: The Cafe
---

### Post by mastermindg on 2008-05-29
The only reason that I haven't moved completely over to Linux (not including virtualization :0) is because of the lack of an 'easy to use' Media Center solution.

I have decided to build an HTPC around MythTV and/or Freevo. I need suggestions on hardware that will give me the least amount of trouble when I get down to configuring them. I'm looking at pcHDTV since these are MADE for Linux distros.

I will also be getting a dual-dvi video card.

Any suggestions will be greatly appreciated.

---

### Post by blastus on 2008-05-29
You should shoot for silence...

- Antec Solo Case
- Asus EN9600GT Silent (passive cooling) (has two DVI-D connections)
- Intel Core 2 Duo E8400 45nm (runs very cool)
- A motherboard that has S/PDIF optical/coaxial outputs so that you can connect it directly to your home theater system
- A Zalman or Ninja CPU cooler (minimum 92mm fan)
- A fan controller that you can use to reduce fan speeds and control noise
- A fast USB key or a SSD (Solid State Drive) instead of a mechanical hard drive (again for silence)
- A MythTV backend server that sits in another room

---

### Post by mastermindg on 2008-06-08
I ended up choosing 2 K-World ATSC 115's. These are supported quite well and were only $35 at newegg.

---

### Post by segalion on 2008-08-21
I recomend you a 17" laptop, with a good grafic card.
This is the best cheap, size, design and silence relationship hardware for HTPC.

And plus you have:
- compatible hardware guaranted
- a TV screen.
- a portable mp3 player (speaker included)
- internet wifi conection
- and of course a complete laptop for what you want.

You can get your favorite HTPC with all your media content whenever you go (hollydays, etc).

Sugestions for cards: all-in-one "flydvb trio cardbus", ...

---

### Post by TheSlipstream on 2008-08-21
> **segalion said:**
> 
- a portable mp3 player (speaker included)


Yes, a nice, portable 17 inch Mp3 player. :P

---

### Post by gn2 on 2008-08-21
The laptop idea is a good one, if I ever get an HD TV the HDMI output on my Asus F9E might be useful.

---

### Post by Swarms on 2008-08-21
Keep an open eye on AMDs new All In Wonder card specielly designed for HTPC's, its an tvtuner and graphics card in one. They said it was going to be supported on linux, so find some info.

If you are not interested in a extra graphics card you can find a motherboard that has a hdmi output and should be able to process 1080p. I know Gigabyte makes them.

You should not use C2D processor unless you want to game on it too, but either Atom or AMD's new ones running on insanely low watts, find what just handles your needs and thereby develops low heat and therefore noise from fans.

---

### Post by geoken on 2008-08-21
Do you forsee yourself doing a lot of liveTV recording.

If live TV is less of a concern, I would suggest boxee. I'm running it right now and it's great. It's a front end for XMBC and it's the best HTPC software I've used.

---

### Post by Swarms on 2008-08-21
> **geoken said:**
> Do you forsee yourself doing a lot of liveTV recording.

If live TV is less of a concern, I would suggest boxee. I'm running it right now and it's great. It's a front end for XMBC and it's the best HTPC software I've used.

If I could just figure how to compile it on 64 bit. :(

---

### Post by segalion on 2008-09-17
At this moment, the more hardware related issue for a HTPC is the remote control.
For this, you need [lirc]("http://www.lirc.org/")
Because the perfect complement of a HTPC is a good TVset (big LCD), and a good audio/video amplifier, I recomend you a RI (Remote Interactive) compatible, as Onkyo box, because you can connect your 6.1 amplifier to the mic in via jack2jack and configure lirc without any hardware (you can see this great Stormx [howto]("http://ubuntuforums.org/showthread.php?t=477958")

---

### Post by geoken on 2008-09-17
Why wouldn't you just get an Microsoft MCE remote (which will work out of the box as there are preconfig'd lirc files) then control your other devices through the remote without doing it through lirc? The MCE remote makes this really easy. You can make it learn any command by pointing a devices remote at the MCE remote, pressing a key, then letting the MCE remote assign that IR command to one of it's own keys. For example, you could take your amps remote, point it at the MCE remote, hold the switch source button, then have the MCE remote assign that switch source command to one of it's buttons.

---

### Post by segalion on 2008-09-18
I dont know the MS MCE remote. 

How the remote send information to the PC? Via some USB dongle?

Seems that this remote is a Universal IR remote too? (learn commands from other IR remote controls)

---

### Post by segalion on 2008-09-18
I dont know the MS MCE remote. 

How the remote send information to the PC? Via some USB dongle?

Seems that this remote is a Universal IR remote too? (learn commands from other IR remote controls)

---


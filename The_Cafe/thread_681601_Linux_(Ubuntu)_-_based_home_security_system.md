---
title: "Linux (Ubuntu) - based home security system"
date: 2008-01-29
forum: The Cafe
---

### Post by maxino on 2008-01-29
Hello,

I am wondering if I could build a home security system (anti-burglar) by using a salvaged laptop, linux (obviously Ubuntu!) and perhaps some other dyi hardware. It would run a simple demon which would monitor reed switches and passive infrared sensors for windows and doors and maybe other sensors (fire, etc). I have seen I/O interfaces which have a number of digital/analog inputs, but I don't know about laptops: perhaps some sort of "connection box"  using USB, PCMCIA???
Anybody has ever thought (or build) something like that? Any ideas about what to do/where to look for inspiration?

Cheers,

---

### Post by barbedsaber on 2008-01-29
good luck to you. sorry i cant help

---

### Post by handy on 2008-01-29
[***_X10_***]("http://en.wikipedia.org/wiki/X10_(industry_standard)") is something you might find stimulating, it may not be what you are looking for, but it is connected. (no pun intended)

It is apparently possible to connect it to Linux machines, but I have not chased up the details.

---

### Post by fatality_uk on 2008-01-29
This might help
[http://www.yolinux.com/TUTORIALS/LinuxTutorialX10SmartHomeNetworking.html]("http://www.yolinux.com/TUTORIALS/LinuxTutorialX10SmartHomeNetworking.html")

---

### Post by FFighter on 2008-01-29
Hi maxino,

This is exactly the kind of thing that attracts me. This, IMHO, is a very exciting but underestimated use of Information Tecnology. I will definetly want to have a inter-connected "intelligent" home in a near future! (not only for security, but other crazy things too!).

Thanks for posting - the info here will be valuable as an introduction.

---

### Post by Whiffle on 2008-01-29
Its probably possible.  I'm not familiar with a security end of it, but I've dabbled with HVAC control and data logging.  You might check out a few different things.  One of them is the X10, they're fairly well developed.  You could check out [http://www.smarthome.com](http://www.smarthome.com) for some ideas I think, although I think their prices are high.   I've 1-wire bus parts from [http://www.aagelectronica.com/aag/index.html?target=p_44.html&lang=en-us](http://www.aagelectronica.com/aag/index.html?target=p_44.html&lang=en-us) in combination with the digitemp software to log data.

---

### Post by maxino on 2008-02-02
Hi,
It seems there is another approach (besides X10 stuff) which would require only standard switches and sensors/detectors: using the parallel port. There are quite a few input pins in a parallel port which could poll the state of several switches/sensors. Reading the state of such pins could be greatly simplified by using a library such as [[COLOR="DeepSkyBlue"]parapin[/COLOR]]("http://parapin.sourceforge.net").
And, of course, one or more outputs could drive (suitably interfaced) the loudest siren one can find.
What do you think? Looks interesting and... cheap ;)

---

### Post by jondecker76 on 2008-02-02
Check out LinuxMCE - it does home security, audio, video, automation, phones and more!  Its based off of Kubuntu

I just got my system set up and WOW!

---

### Post by maxino on 2008-02-02
It certainly looks awesome...
I just had a quick glance at the documentation and it seems that this nice piece of software is very much media-oriented, while I was thinking along the lines of a much simpler application which could run on low-end hardware (preferably semi-obsolete laptops) and monitor a number of events/states (doors, windows, presence of people, etc).
Thanks for the tip, jondecker76. If you don't mind, perhaps you could tell us more about your set up.

Cheers

---

### Post by jondecker76 on 2008-02-02
My setup is just starting out, but what I have so far for LinuxMCE is:
-A core based on an ASUS M2NPV-VM motherboard, 2GB ram, AMD Athlon AM2 BE-2400 processor and 5TB of internal storage (6 x 1TB Western Digital Caviar drives raid 5 configuration)

For those who haven't heard of linuxMCE, check out [www.plutohome.com]("http://www.plutohome.com")

Linux MCE is a for of PlutoHome, built upon Kubuntu.

For a good rundown of some of the popular features of Linux MCE, check out a demo video at:
[http://video.google.com/videoplay?docid=2176025602905109829&hl=en]("http://video.google.com/videoplay?docid=2176025602905109829&hl=en")

It really is as great as they say it is - although it is not a simple peice of software and setup takes some learning/trial/error... But its just amazing, i would recommend it to anyone!  Though, it is not extremely cheap either...

After I get more experience with it, and add on to it more, maybe I'll make and post a demo video of my own

---

### Post by maxino on 2008-02-03
> **jondecker76 said:**
> ...and 5TB of internal storage (6 x 1TB Western Digital Caviar drives raid 5 configuration)

 my goodness... :shock::shock::shock:

---

### Post by regomodo on 2008-02-03
For what you require a laptop is overkill. An [  Arduino]("http://arduino.cc")would mostly fit the bill for you.

---

### Post by maxino on 2008-02-03
Granted.
I was just thinking of a way to give new life to some aged laptop that I could grab almost for free, and I am positive that even the crappiest one would be way overkill for this kind of application. But then again, wouldn't it be nice to set up a simple web server and being able to login from anywhere in the universe (well... world) and check the integrity of doors, windows, temperature, water level in the cat's drinking fountain? :)

---

### Post by xpod on 2008-02-03
> I am wondering if I could build a home security system (anti-burglar) by using a salvaged laptop, linux (obviously Ubuntu!) and perhaps some other dyi hardware. It would run a simple demon which would monitor reed switches and passive infrared sensors for windows and doors and maybe other sensors (fire, etc). I have seen I/O interfaces which have a number of digital/analog inputs, but I don't know about laptops: perhaps some sort of "connection box" using USB, PCMCIA???
Anybody has ever thought (or build) something like that? Any ideas about what to do/where to look for inspiration?

I`ve been considering something along the same lines myself funnily enough..cheers.
Not for any *real* need mind you as no-one(that knows us) would dare enter our house without permission,not down here in London.
They all think us Scots are completely nuts for some  weird reason:-\"

> 
This is exactly the kind of thing that attracts me. This, IMHO, is a very exciting but underestimated use of Information Tecnology. I will definetly want to have a inter-connected "intelligent" home in a near future! (not only for security, but other crazy things too!).

Thanks for posting - the info here will be valuable as an introduction.

+1
I`d also like to start doing something more with some of that spare hardware we have,besides giving it away again.
Of course though,i`ll still be a complete noob after 18 years,never mind the 18 months i`ve used Ubuntu & Co so far (only 23 months using pc`s) hence it`s threads like these and all the great Howtos & guides out there that keep me going.
Got to stay a step or two ahead of those kids of ours at the very least[-X

The closest i`ve come to any DIY Spyware myself(best i was capable of anyway)  was setting up an Eyetoy *inside* one of my sons hifi speakers,that sat beside his monitor at the time.
That Eyetoy and SSH had him thinking all sorts for a day or two:twisted:
MIne & his Mums laughter got us caught pretty quickly mind you.

Even when he sneaked down the stairs and caught us watching him it still took him another 20 minutes to figure out where the camera was.
He actually believed we were watching him through his monitor at first.

> After I get more experience with it, and add on to it more, maybe I'll make and post a demo video of my own

IF my own experiences fall flat the i will be waiting patiently for it:)

---


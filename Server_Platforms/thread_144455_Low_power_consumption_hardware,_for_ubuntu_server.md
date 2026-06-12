---
title: "Low power consumption hardware, for ubuntu server"
date: 2006-03-14
forum: Server Platforms
---

### Post by simone.brunozzi on 2006-03-14
Hi there,
I'm going to prepare an ubuntu server for a student community in Italy, however we REALLY need a machine with low power consumption and low heat production (because it is going to be installed in a not-cooled room, and we want it with high reliability.

I've read (googling around) that there are some machines with Pentium-M processors installed, but I'm not sure if they work well, or if it is possible to dinamically manage CPU frequency like in laptops.

In synthesis, I'm blind on this one... can anyone help me with informations and suggestions?

Also, do you think that a compact Flash Hard Drive could be useful and worth the cost?

Cheers,

---

### Post by isitaboat on 2006-03-17
You thought about the low-power AMD Opterons?

---

### Post by MJN on 2006-03-17
Why is power consumption such a concern? Due to the associated heat production? If so, don't worry about it  - a single server is not going to need any special cooling/atmospheric requirements over and above what occupants of the room might want!
 
Mathew

---

### Post by va3uxb on 2006-03-17
I'm using an older (G4 PPC) Mac Mini to run Ubuntu at home.  It is very small, very quiet, and doesn't get too warm.  It's got an 80GB drive in it, and seems to work very well as a home server.  It's been runing since early December 2005 without any troubles.

---

### Post by simone.brunozzi on 2006-03-17
Hi there!

Mac Mini could not be a solution for a server.

Power consumption and heat dissipation is a MAJOR issue in this case.

What do you mean for "low-power AMD Opterons"? Mobile versions? Where can you buy them??

Cheers,

---

### Post by kmi on 2006-03-17
Hello,
1 I think the answer REALLY depends on what you do with your server... Running a small (but reliable :) ) website with static pages for a small community is quite simple and an old (bt reliable :) ) PII would certainly fit... If you need to load a big amount of data through all sorts of requests for a huge amount of users, then it's quite different...
So, please tell us what you wanna do with it ! :)

2 Compact flash (or any sort of flash disk) is always a good solution in terms of power consumption BUT the price per gigabyte still remains high... especially if you need a big capacity of storage... Another option would be to consider the use of 2.5" ide (or SATA) disk(s) : to my opinion, it combines a quite low power consumption with a relatively low cost for a broad choice of capacities (that's what I'm using now on several machines).

---

### Post by kmi on 2006-03-17
[QUOTE=simone.brunozzi]Hi there!

Mac Mini could not be a solution for a server.

Power consumption and heat dissipation is a MAJOR issue in this case.

What do you mean for "low-power AMD Opterons"? Mobile versions? Where can you buy them??

Cheers,[/QUOTE]

Why the hell is a Mac mini NOT a solution (maybe U should have a look [here]("http://switch.richard5.net/isp-in-a-box-using-a-mac-mini/") ?)

Low power AMD = Turion

---

### Post by simone.brunozzi on 2006-03-18
kmi,
mac mini is jut not reliable like other machines, and it cannot be "upgraded" easily (ethernet ports et similia).
That's why I didn't take it as an option.

This machine can have just 2 GB of storage, and possibly 512 MB of RAM.

2,5" HD are a good idea though.

Thanks, any futher help is always appreciated.

Cheers,

---

### Post by MJN on 2006-03-18
What's wrong with any mdoern (branded perhaps) off-the-shelf PC?

You really need to specify your requirements - leaping to 'low power consumption and heat' doesn't really help as these could well be (and I suspect they are) unjustified contraints.

Mathew

---

### Post by simone.brunozzi on 2006-03-20
Mathew,
I understand your point, and I'll now try to be more specific:

I need a VERY RELIABLE machine (so, something better than an ordinary PC), that will be a SERVER (thus, almost always up), needs to have low power consumption and heat dissipation.
I think that there are some solutions involving: industrial hard disks (on average more reliable), or industrial flash drives (obviously very reliable compared to hard disks), and possibly a Mobile or Ultra-low voltage processor.

However, I wasn't able to find a supplier for that kind of machine, that's why I asked to ubuntu community.

I hope that this time I've been clear. If anything is missing, my apologies, and please don't exitate to ask for further details.

Thanks a lot!

Cheers,

---

### Post by MJN on 2006-03-20
That's helped a little I'm sure however you still haven't said why you want low power consumption and heat dissipation... or is it just 'cos you do?! ;)
 
You left the fundamental issue out... your budget. And can you quantify 'VERY RELIABLE'?
 
Mathew

---

### Post by va3uxb on 2006-03-20
Well, your only priorities are low power consumption, good heat dissipation, and reliability, then there's this:
[http://va3uxb.dynip.com/](http://va3uxb.dynip.com/)

It runs on 5 or 6 volts dc at less than 500mA, it's all solid-state so there are no moving parts to wear out, and you can use up to 2GB of filespace with a single SD card.  4GB if you want to use 2 SD cards.It's strictly wireless, 802.11b.  Oh, and it has a built-in battery good for about 2 or 3 hours of up-time, so if the power fails it will keep on going for a good long time.  Uptime is at 105 days since I plugged it in and started it serving webpages.  

How's that for low power, low heat, and reliability? :D 

It's relatively inexpensive too, so you can 'deploy' more than one if necessary.

Now, admittedly, it's not runing Ubuntu, but it is running linux, so you can configure it any way you like.

---


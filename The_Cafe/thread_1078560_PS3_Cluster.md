---
title: "PS3 Cluster"
date: 2009-02-23
forum: The Cafe
---

### Post by kuniyori on 2009-02-23
Hi all,

Just wondering if its possible to set up a cluster on PS3s using Ubuntu instead of fedora/red hat/yellow dog[-o<?

Also any ideas on how to go about setting up a server to administer this with a web front-end so I can use it when away from home?:popcorn:

Not really sure where this post would be most appropriate so to be safe I'll throw it in here.:p

Oh and when I start building I'll try to put up some pics and stuff.(It's only in the planning stages at the moment!)

Thanks!!

---

### Post by ghindo on 2009-02-23
I don't think that Ubuntu supports the PS3's architecture.

---

### Post by TravisNewman on 2009-02-23
> **ghindo said:**
> I don't think that Ubuntu supports the PS3's architecture.
Yeah it totally does. 
[http://psubuntu.com/](http://psubuntu.com/)
It's the powerpc architecture.

As for clusters, no clue.

---

### Post by hyperdude111 on 2009-02-23
> **ghindo said:**
> I don't think that Ubuntu supports the PS3's architecture.

It runs perfectly on PS3, i use it however it is poor on the lack of ram, lack of graphics drivers and a huge lack of applications.

---

### Post by handy on 2009-02-23
OP, is there any reason that you need to have a PS3 cluster, beyond exploring the possible?

---

### Post by doorknob60 on 2009-02-23
> **hyperdude111 said:**
> It runs perfectly on PS3, i use it however it is poor on the lack of ram, lack of graphics drivers and a huge lack of applications.

Use Openbox/Lxde, Gnome runs slowly on the PS3. (that's what I do, it runs very fast). Just sudo aptitude install lxde and it will install Openbox, Pcmanfm, Lxpanel, and lots of other great apps that make a very light DE. You can choose it from GDM menu.

---

### Post by jimi_hendrix on 2009-02-23
imagine a beowulf cluster of those...*ducks*

---

### Post by kuniyori on 2009-02-23
No real reason other than i have an unhealthy interest in 'projects'. remote control aeroplane that can fire model rockets, a freedos beowulf cluster on lattitude cpis, ya know that sort of thing. I can prob use it to run spss and mathlab, maybe the odd time to compile stuff and for blender. The web interface is so I can use it while Im in college and let the peoplle in my class use it for statistical analysis projects, might even offer its use to the blender project. Lots of things to do with it!! :D

Its an amazing piece of hardware to be honest!!!! I really like the fact that i can run open source games and emulators on it. 

you can also try running Xubuntu on it, I think it only takes up 67-9 megs of ram running idle. If I set it up in a cluster I will probably run it headless and use my normal computer to vnc into it. so that should save some ram.

Any ideas on uses and software?

---

### Post by TravisNewman on 2009-02-23
Just out of curiosity, PS3's are not cheap... is that not a barrier to this idea?

---

### Post by handy on 2009-02-23
I don't think you will gain anything by having more than one PS3, as far as gaming is concerned either.

---

### Post by kuniyori on 2009-02-24
In europe the cost around 350-400 euro. when you compare the power of these in a cluster formation to the same im pc format it is much much cheaper! Just because its not all about the power but the ability to parallel process. One PS3 contains 8 cpus. For the same price I couldn't get a similarly powered computer (with the exception of the RAM). I only plan on buying maybe 10 of these over a period of time so its not too expensive for the possibilities.

---

### Post by mips on 2009-02-24
[http://gravity.phy.umassd.edu/ps3.html](http://gravity.phy.umassd.edu/ps3.html)
[http://www.ps3cluster.org/](http://www.ps3cluster.org/)
[http://en.wikipedia.org/wiki/Playstation_3_cluster](http://en.wikipedia.org/wiki/Playstation_3_cluster)

> Q: Why the PS3?  

A: In short, the Cell Processor &#8216;packs a punch&#8217;. One of the authors (Khanna) estimates that his MPI computations run much faster than on desktop workstation chipsets, and that his original 8 PS3 (i.e. 64 core) Cell cluster had comparable if not better performance to a 200 Node IBM Blue Gene system.

---

### Post by kuniyori on 2009-02-24
I know that PS3 arnt cheap but for _what you get_ its relatively cheap especially if you use them as part of a cluster. A PS3 has 8 cpu's clocked to run at the 3.2GHz and thats with one of the SPEs disabled, an extreemly poweerfull video card (which if you like to program you can use as an extra processor, a blueray drive, 3 network cards, wireless, bluetooth, an upgradeable HDD and the only downside 256Megs of Ram. Its also designed to be extreemly poweer effecient. 

So even if you have to buy a few of them and hook them into a cluster its no more expensive than buying a good new computer, except that most of the cost is borne by Sony. :D Its a chep powerfull system and when i get bored I can always boot it up into Playstation mode and play some games.

Ya I know it wont effect the ability to play games but thats not what i want it to do. Although I think in this reguard the Linux distrobutors have lost out on a major oppertunity. Were they to have developed a lightweight OS for the system which took advantage of the cell architecture it would have allowed games developers to develop games on a stable linux platform for the next few years without the need to pay sony royalties. It also could have probably have lead to a lot more commercial games support for linux in general and a bigger home base which would have been normalised to the use of linux. This is just my opinion and speculation though.

It was more trying to come up with ideas for the use of such a machine and under ubuntu rather than fedora as is the case at the moment.

---

### Post by TravisNewman on 2009-02-24
It doesn't technically have 8 processors does it? I was under the impression that it was an 8-core CPU

---

### Post by kuniyori on 2009-02-24
Its got 8 cores but you can have them act as if they were individual cores from what ive read (I could be wrong here).

---

### Post by juanmoreno92 on 2009-02-24
A PS3 has actually one true PowerPC core and 7 Synergestic Processing units which are second to Chuck Norris in number crunching SIMD opertions (take a look at folding@home).

---

### Post by kuniyori on 2009-02-24
Just thought it would be too complicated to explain :P!!

---

### Post by handy on 2009-02-24
> **kuniyori said:**
> In europe the cost around 350-400 euro. when you compare the power of these in a cluster formation to the same im pc format it is much much cheaper! Just because its not all about the power but the ability to parallel process. One PS3 contains 8 cpus. For the same price I couldn't get a similarly powered computer (with the exception of the RAM). I only plan on buying maybe 10 of these over a period of time so its not too expensive for the possibilities.

From memory, only 7 CPU's (;-)) are functioning.

---

### Post by handy on 2009-02-24
> **kuniyori said:**
> 
Ya I know it wont effect the ability to play games but thats not what i want it to do. Although I think in this reguard the Linux distrobutors have lost out on a major oppertunity. Were they to have developed a lightweight OS for the system which took advantage of the cell architecture it would have allowed games developers to develop games on a stable linux platform for the next few years without the need to pay sony royalties. It also could have probably have lead to a lot more commercial games support for linux in general and a bigger home base which would have been normalised to the use of linux. This is just my opinion and speculation though.


From what I have read, programming app's to run with the CELL processor is incredibly difficult, & has been a limiting factor in the both the number & quality of the games produced for the PS3.

Sony states, that they will not release a PS4 until the limits of the PS3 have been reached by software engineers.

---

### Post by juanmoreno92 on 2009-02-24
> **handy said:**
> From memory, only 7 CPU's (;-)) are functioning.

1 SPU (not CPU) is reserved for the Hypervisor.

---

### Post by kuniyori on 2009-02-24
It is a difficult arcitecture to program for but the fact still remains that it would reduce the cost to game developers. The very fact that its so complicated to program for means that it would be ideal for companies to group together to develop core engines thus reducing the cost for the individual developer even further. And yes one of the Spus are held in reserver for the console OS and hypervisor.

The longer it stays a stable system the better for the game community. To be hones this really is a golden oppertunity for the linux community. one of the biggest problems with linux is many distros and many hardware platforms. Thats why almost no commercial games are released for it.

Reasons why it should be seriously looked at despite its complexity:

It is cheap (Sony subsidises the hardware)
It is state of the art hardware (its so cutting edge it is could not be competitively sold at or above cost price)
It will be in production for many years to come (as you have mentioned)
It provides a standardised open platform upon which to base software development.
Many people already have these sitting in their homes!!!

---

### Post by mips on 2009-02-25
I wonder if it would be possible to upgrade the ram at all, address lines allowing. There are memory chips available that are double the size of the original ones used in the PS3. I did some research a little while back and the chips are available. Just wondering if drop in replacement would be possible via surface mount desoldering/soldering?

---

### Post by handy on 2009-02-25
I reckon the good professor would have sussed it out all ready; as he is on a good government wage & it pays for him to come up with the goods, so to speak, it keeps him on a good wicket & furthers his advancement in the bureaucracy he is dedicated to.

---

### Post by mips on 2009-02-25
> **handy said:**
> I reckon the good professor would have sussed it out all ready; as he is on a good government wage & it pays for him to come up with the goods, so to speak, it keeps him on a good wicket & furthers his advancement in the bureaucracy he is dedicated to.


Maybe you should come join me for that cold one ;) The barman has a good ear :)

---

### Post by handy on 2009-02-25
> **mips said:**
> Maybe you should come join me for that cold one ;) The barman has a good ear :)

:lolflag:

---

### Post by kuniyori on 2009-02-25
If you could do that it would be one of the greatest pieces of hardware ever!!! Have to admit though I have no intention of trying... Im a bit of a coward when it comes to modding hardware... 

Maybe it will advance his career. Lets face it though Id prefer to have a person who finds good creative ways to solve problems than a person who moves up the line because he knows the right people and cant do his job!! (LOL)

The ram idea is interesting though!! Will have to look into it! (Even if I am scared to tinker with that sort of thing!:P)

---

### Post by mips on 2009-02-27
If you want to look into the RAM issue I can tell you the PS3 uses 4x512Mbit XDR RAM chips supplied by Elpida & Samsung.

[http://www.elpida.com/en/products/xdr.html](http://www.elpida.com/en/products/xdr.html)
[http://www.samsung.com/global/business/semiconductor/productList.do?fmly_id=139](http://www.samsung.com/global/business/semiconductor/productList.do?fmly_id=139)

Only Elpida seem to have the 1Gbit density chips.

The package is FBGA and I have no idea how to desolder those at all as I don't even think it's possible as you cannot get to the pins.. These things get soldered via a universal heating process of all the solder/flux in one go. Testing is via laser or x-ray to check joints.

[COLOR=DarkOrange]EDIT: [/COLOR]
Looks like soldering and desoldering is possible after all for the hobbyist, [http://www.lrr.in.tum.de/~acher/bga/index.html]("http://www.lrr.in.tum.de/%7Eacher/bga/index.html")
But I would advice sending it to someone that has the proper tools.
[http://www.google.co.za/search?q=How+to+desolder+FBGA&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](http://www.google.co.za/search?q=How+to+desolder+FBGA&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a)

---


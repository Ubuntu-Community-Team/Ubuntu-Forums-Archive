---
title: "Help me buy a new server for my home"
date: 2008-10-19
forum: The Cafe
---

### Post by happyisland on 2008-10-19
Hello ubuntu party people!

Given the excellent feedback I got during my last computer purchase "[Help me buy a new computer]("http://ubuntuforums.org/showthread.php?t=672666")", I have decided to enlist the help of the forum again. This time I am interested in setting up a home file server - something I know even less about than building a PC. I don't have any old PCs laying around, so I would have to buy something.

My goals:

1) to be able to access a central repository of music and movies from any computer using my home's wireless router. I'd like to be able to listen to any song or watch any movie streamed over the wireless network from any part of the house.

2) storage in the neighborhood of 500gb

3) energy efficiency

4) relatively cheap (since there will never be more than two or three users concurrently I imagine I won't need much computer horsepower).

5) usable for backing up the computers on our network.




Any recommendations about hardware, software, configurations, etc, would be highly appreciated!!!


Thanks in advance!

-Happyisland

---

### Post by pp. on 2008-10-19
NSLU2 with external USB disks.

---

### Post by happyisland on 2008-10-19
That looks like it might be EXACTLY what I need... Have you used one of these before?

---

### Post by smbtol on 2008-10-19
My dream is to buy a fit-pc for a home server.
The prices are here:
[http://www.fit-pc.com/new/ordering-fit-pc-slim-us-canada.html](http://www.fit-pc.com/new/ordering-fit-pc-slim-us-canada.html)
Description is here:
[http://www.fit-pc.com/new/whats-new.html](http://www.fit-pc.com/new/whats-new.html)
It comes with Ubuntu 8.04.
NSLU2 is so old.

---

### Post by billgoldberg on 2008-10-19
I will start by saying that you'll need to hook up your server to the router using an ethernet cable. Do not use wireless for the server.

I presume you are using all Ubuntu machines.

I would use openssh for that. Just install the package "openssh-server" or just "ssh" if your on 8.10 beta. No configuration needed.

Then just use "Places -> Connect to server" from your Ubuntu computers and you'll be able to access any file on the server, including configuration files and such. Totem, vlc, exaile, ... will be able to stream the movies, music, ...

If you have upnp machines (ps3, ...) then install "mediatomb". There are lots of guides on setting it up.

Any low budget pc will do, put a couple of terabyte drives in there and you're good.

If you are putting the server in the living room or something, make sure it's a silent machine.

---

### Post by pp. on 2008-10-19
> **happyisland said:**
> That looks like it might be EXACTLY what I need... Have you used one of these before?

I have, indeed, and I was very pleased. Doing backups is very easy, either to another device or from one USB disk to the other. The built-in SMB server is quite robust.

---

### Post by KiwiNZ on 2008-10-19
A HP Superdome  should meet your needs :p:D

---

### Post by happyisland on 2008-10-19
> **billgoldberg said:**
> I will start by saying that you'll need to hook up your server to the router using an ethernet cable. Do not use wireless for the server.

I presume you are using all Ubuntu machines.

I would use openssh for that. Just install the package "openssh-server" or just "ssh" if your on 8.10 beta. No configuration needed.

Then just use "Places -> Connect to server" from your Ubuntu computers and you'll be able to access any file on the server, including configuration files and such. Totem, vlc, exaile, ... will be able to stream the movies, music, ...

If you have upnp machines (ps3, ...) then install "mediatomb". There are lots of guides on setting it up.

Any low budget pc will do, put a couple of terabyte drives in there and you're good.

If you are putting the server in the living room or something, make sure it's a silent machine.


Well, for the actual physical server, is there any advantage you can see to me using an old PC instead of a NSLU2 by linksys (or something similar)?

Another question: what are the minimum recommended specs for RAM and processor for an old PC solution?

---

### Post by billgoldberg on 2008-10-19
> **happyisland said:**
> Well, for the actual physical server, is there any advantage you can see to me using an old PC instead of a NSLU2 by linksys (or something similar)?

Another question: what are the minimum recommended specs for RAM and processor for an old PC solution?

I don't know what the NSLU2 is.

Your server will most likely be gui-less so running it won't take that much.

Anything from a mid range PII and 256mb ram would be fine I guess.

Off course, the more the better. Ram is cheap these days, and some older, decent processes aren't that expensive.

---

### Post by stmiller on 2008-10-19
Old pcs are usually available for free out there. Most can hold at least two hard drives, which gives raid or multiple storage possibilities.

Anything Pentium II and higher is enough for a home file server. :)

---

### Post by Dr Small on 2008-10-19
> **billgoldberg said:**
> I will start by saying that you'll need to hook up your server to the router using an ethernet cable. Do not use wireless for the server.


+1
I learned myself that the server responds faster for data streaming and connectivity if it's plugged into ethernet.

---

### Post by happyisland on 2008-10-19
Thanks to everyone above for the great input. Now I'm thinking that a server might be overkill for my purposes (simple file sharing for users connected to my wireless router). For cost of purchase and lower power consumption I'm strongly leaning toward the low tech solution proposed above, the Linksys NSLU2.

Unless, that is, there is anyone out there who thinks this is a terrible idea or something...

---

### Post by Frak on 2008-10-19
Find an old PowerMac G4. BTW, they all used PCI-X.

Ubuntu server runs great on them, and they seem to be built for the job (ironic much?).

Any extra NIC will work in it, but [these]("http://sonnettech.com/product/prestogigserver.html") (PCI-X) are the best I can find.

---

### Post by mips on 2008-10-20
> **smbtol said:**
> My dream is to buy a fit-pc for a home server.
The prices are here:
[http://www.fit-pc.com/new/ordering-fit-pc-slim-us-canada.html](http://www.fit-pc.com/new/ordering-fit-pc-slim-us-canada.html)
Description is here:
[http://www.fit-pc.com/new/whats-new.html](http://www.fit-pc.com/new/whats-new.html)
It comes with Ubuntu 8.04.
NSLU2 is so old.


That uses a 2.5" hard drive wich will not yield 500GB the OP wants.

---

### Post by Nox_UK on 2008-10-20
found the nslu2 a bit slow tbh, streaming was ok, but getting the stuff up onto it in the first place was terrible.

Nox

---

### Post by billgoldberg on 2008-10-20
> **happyisland said:**
> Thanks to everyone above for the great input. Now I'm thinking that a server might be overkill for my purposes (simple file sharing for users connected to my wireless router). For cost of purchase and lower power consumption I'm strongly leaning toward the low tech solution proposed above, the Linksys NSLU2.

Unless, that is, there is anyone out there who thinks this is a terrible idea or something...

My desktop is on 24/7 or at least most of the time. I just run my openssh and upnp server from there.

I let that serve files to my wireless devices.

I never even noticed any impact from those services when they are being used.

That way I don't need another pc.

---

### Post by Lowcountry on 2008-10-20
> **pp. said:**
> NSLU2 with external USB disks.

I have one...works great!
I use it to host my wife's small business website, a music server, and for file back-up.  I got it on e-bay for $30.

---


---
title: "Deluge repository for Ubuntu open"
date: 2007-11-28
forum: The Cafe
---

### Post by zachtib on 2007-11-28
AS some of you know, i've been hosting deluge debs on my personal ppa, but i've just set one up on the Deluge-team PPA in launchpad, which is what i'll use from now on.  
to add the repository, add these lines to sources.list:
```
deb http://ppa.launchpad.net/deluge-team/ubuntu gutsy main universe
deb-src http://ppa.launchpad.net/deluge-team/ubuntu gutsy main universe

```

packages are also available for feisty and hardy.
then apt-get install deluge-torrent

---

### Post by FuturePilot on 2007-11-28
> **zachtib said:**
> AS some of you know, i've been hosting deluge debs on my personal ppa, but i've just set one up on the Deluge-team PPA in launchpad, which is what i'll use from now on.  
to add the repository, add these lines to sources.list:
```
deb http://ppa.launchpad.net/deluge-team/ubuntu gutsy main universe
deb-src http://ppa.launchpad.net/deluge-team/ubuntu gutsy main universe

```

packages are also available for feisty and hardy.
then apt-get install deluge-torrent

Awesome! :guitar:

---

### Post by rune0077 on 2007-11-28
Great! Spectacular! Thanks very much!

---

### Post by procrastinator on 2008-01-12
How about putting up 0.5.8?

---

### Post by motin on 2008-01-25
Great, but when is Deluge going to be part of universe you think? Ready for Hardy?

Cheers!

---

### Post by bufsabre666 on 2008-01-25
> **motin said:**
> Great, but when is Deluge going to be part of universe you think? Ready for Hardy?

Cheers!

wait for version 1.0, its still a little too buggy

---

### Post by RomeReactor on 2008-01-25
> **bufsabre666 said:**
> wait for version 1.0, its still a little too buggy

Really? Admittedly, in Feisty it had a few noticeable bugs, but in Gutsy, Deluge hasn't given me any trouble whatsoever; for me it's been absolutely great. By the way, zachtib, thank you very much for Deluge! Hopefully it won't take long to become the default BitTorrent client in Ubuntu. :popcorn:

---

### Post by bufsabre666 on 2008-01-25
> **RomeReactor said:**
> Really? Admittedly, in Feisty it had a few noticeable bugs, but in Gutsy, Deluge hasn't given me any trouble whatsoever; for me it's been absolutely great. By the way, zachtib, thank you very much for Deluge! Hopefully it won't take long to become the default BitTorrent client in Ubuntu. :popcorn:

im exactly opposite, i had no problems in feisty, and in gutsy it does nothing but give me headaches and crash, it made me go back to azureus

---

### Post by RomeReactor on 2008-01-25
> **bufsabre666 said:**
> im exactly opposite, i had no problems in feisty, and in gutsy it does nothing but give me headaches and crash, it made me go back to azureus

Even though it eats loads of RAM, I still like Azureus (but not as much as Deluge :P).

One of these days I'll give Transmission a try...

---

### Post by bufsabre666 on 2008-01-25
> **RomeReactor said:**
> Even though it eats loads of RAM, I still like Azureus (but not as much as Deluge :P).

One of these days I'll give Transmission a try...

i prefer azureus's GUI but i prefer deluges funtionality ((well i did in feisty and under windows))

---

### Post by RomeReactor on 2008-01-25
I have this strange fascination with Java programs... it's like a guilty pleasure: you know you shouldn't, but you just can't stop :)

---

### Post by gordonh on 2008-01-27
> **bufsabre666 said:**
> wait for version 1.0, its still a little too buggy

Speaking of which, I've tried to update from Feisty to Gutsy a few times, but the upgrade has always failed with a message regarding Deluge.

Does anybody have any info/thoughts/ideas?

I can post the output if it would help.

---

### Post by Anduu on 2008-01-27
I was a hardcore Azureus user till they started getting all fancy with their Vuze bloatware...Deluge now rocks my sox :)

---

### Post by Polygon on 2008-01-28
something must be wrong on your end as ive been using the svn builds of deluge ever since gutsy came out and i have had no problems whatsoever.

report a bug maybe on the deluge-torrent.org forums?

---

### Post by bufsabre666 on 2008-01-28
> **gordonh said:**
> Speaking of which, I've tried to update from Feisty to Gutsy a few times, but the upgrade has always failed with a message regarding Deluge.

Does anybody have any info/thoughts/ideas?

I can post the output if it would help.

yeah output usually helps, my problem is because of running alot of other python progrmas it just didnt mesh right, maybe its the same for you

---

### Post by gordonh on 2008-01-30
Here's the output

Failed to fetch [http://deluge.mynimalistic.net/apt/dists/dapper/main/binary-i386/Packages.bz2](http://deluge.mynimalistic.net/apt/dists/dapper/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://acorbeaux.free.fr/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://acorbeaux.free.fr/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found

---


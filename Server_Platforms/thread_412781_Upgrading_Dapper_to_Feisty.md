---
title: "Upgrading Dapper to Feisty"
date: 2007-04-18
forum: Server Platforms
---

### Post by tla on 2007-04-18
So i'm pretty new at this, this is pretty much my first time using CLI with any linux distro, anyways i have a dedicated server hosted by a company, it provides a small range of Distros, Ubuntu 6.06 being one of them. (It is also possible to boot to a small debian distro, but i have no idea of installing ubuntu from that)

Problem is that right now PHP 5.1.2 is the newest repository release, and with many being recommended upgrading to 5.2.x i decided i'd try to skip the whole compile from source deal and upgrade to Feisty(Some time after release tomorrow).

I  tried to upgrade to Edgy Eft, and since there was no "Update-manager" i decided to try out by modifying the sources.lst. 

I did and did the apt-get dist-upgrade and apt-get upgrade, even a couple of times(as i heard that sometimes it would be missing packages after doing the progress, where you would then want to do it a couple of times to make sure).

Anyways no new packages were to be installed and there was no warnings signs that i noticed, so i went ahead and rebooted the machine, a minute later i tried reconnecting and i got the "Connection Timed Out", and i tried pinging it, again "Connection Timed Out", i also tried restarting the server through the restart-service that my provider has for me, still no luck with connecting.

I restart it using their pre-programmed automated ubuntu installer, and i get my system back to 6.06.

So my question is, since i've seen a lot of different ways to do this, what would the step by step procedure be(I heard that the order of commands matter, i also heard someone append some flags to the apt-get procedure)?

Is there any way to determine if a dist-upgrade is successful and if possible revert back changes made if not successful? Seeing as i've been unable to boot it up after a dist-upgrade, this would be very helpful if i could detect that something had gone wrong and roll back the changes.

Serverstats are a Athlon 64 3700+ running amd64 binaries, got 1GB of DDRRAM and 2x160GB harddrives in a software raid 1.

---

### Post by tla on 2007-04-20
Well i think i'm pretty sure on how the upgrade works now, i heard that Lilo needs to be reconfigured after an upgrade, which might be why i couldn't boot previously on my server?

Is it true?

---

### Post by andrumond on 2007-04-23
Well, as long as I know, before upgrading you must first edit your sources.list (/etc/apt/sources.list) and change the version especifications (but you've done it, right?). Where it reads dapper, make it edgy (or feisty). Actually, I'm not sure whether it would be good to upgrade from dapper to feisty, anything could be missing. I was up to do that, but I just read that "You can only directly upgrade to Ubuntu 7.04 ("Feisty Fawn") from Ubuntu 6.10 ("Edgy Eft")" - from [http://www.ubuntulinux.org/getubuntu/upgrading](http://www.ubuntulinux.org/getubuntu/upgrading).
Too bad.
Good luck!!!

---


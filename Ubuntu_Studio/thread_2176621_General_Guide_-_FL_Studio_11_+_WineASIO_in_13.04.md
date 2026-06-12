---
title: "General Guide - FL Studio 11 + WineASIO in 13.04"
date: 2013-09-25
forum: Ubuntu Studio
---

### Post by paulo_sousa2 on 2013-09-25
So yesterday I posted about the two last issues I had with FL Studio 11 running under Linux.

Here's my process.

1 - I installed UbuntuStudio 13.04.
2 - I added the KXStudio repos, updated and did sudo apt-get install wineasio. It installed WINE 1.4 and everything else I needed.
3 - Installed FL Studio. I didn't make a prefix because I'll only be using FL Studio from Windows. I registered it and it loaded properly.
4 - I used regsvr32 to register wineASIO.
5 - In Qjackctl, make sure you have your proper soundcard selected in device. To make sure, press the arrow next to it and you'll be able to see device names. Mine shows up as Conexant, yours is probably different.
6 - Make sure Realtime is off (wineASIO thing), Soft Mode is on, Force 16bit and that should do it.
7 - Start the server and load FL Studio. It should show up as a connection on Qjackctl. Connect FL to system and presto. It should be connected automatically from now on.

Native VSts load fine, CPU load hasn't been properly tested.

It's only a general thing, since it was a two day process and I don't remember everything. Should you look up all the proper documentation, all the info should be there.

Things I've noticed. I think I'm using jackd1 (part of the wineASIO install I think) and not jackd2, it seems wineASIO won't work with it. But it could be just outdated info.

On to the bells and whistles, now that FL is installed and my class compliant Launchpad S is coming!

---

### Post by cub on 2013-10-07
Out of curiosity, why didn't you use KXStudio distribution all the way?

---


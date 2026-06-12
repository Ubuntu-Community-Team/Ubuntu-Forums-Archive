---
title: "LAN party hosting server"
date: 2010-09-26
forum: Server Platforms
---

### Post by Affrikka on 2010-09-26
Hey eveyrone,

I'm a part of our High School's FBLA, and every year we host several LAN parties. I'm trying to convince our school's head of technology that we don't need windows pretty much at all for the stuff we do. He's already been convinced that ubuntu is "really awesome, and super easy to use" and has dual booted all of our desktops at school with win7 and ubuntu 10.04, so I'm on a good track.
Anyway, we have our first LAN party this weekend, and we had the idea to host a few tournaments this year (something we've never done before) which would include:
-Armagetron Advanced (open source/all platforms)
-Urban Terror or Nexuiz (open source, all platforms)
-Warcraft 3 (DoTA specifically) (windows, works in wine)
-TrackMania (windows, works in wine)

The two windows games we could only have a tourney with those who actually own the game, obviously, but as far as WC3/DoTA goes, there is hosting software (called GHost One) specifically made for it.

My question is, is it possible to host these game tourneys (over a LAN) on ubuntu server? And, if not, what would be the most effecient way of hosting these tourneys? The head of technology at my school is willing to lend me a server to set all of this up on my own, and they are pretty nice-- but I wanted to further the "coolness" of ubuntu to show how you can even use it for cross platform thigns such as this, because just about everybody at the LAN party will be running windows.

Thanks for everything in advance,



Mathieux

---

### Post by perspectoff on 2010-09-26
Game servers are game specific.

Your game must have a server for Linux. (I host Skulltag (ZDoom derivative) on a Linux server all the time, for example -- see [http://ubuntuguide.org/wiki/Skulltag_tips](http://ubuntuguide.org/wiki/Skulltag_tips))

After that, you only need to forward the port for the game server from your router to the computer on the LAN that is hosting the game server. Pretty easy, really.

For Nextuiz, for example, i think the server function is built in. just forward ports UDP 26000 as detailed here:

[http://alientrap.org/nexuiz/faq#Server%20setup](http://alientrap.org/nexuiz/faq#Server%20setup)

Urban Terror needs the server installed separately:

[http://www.urbanterror.info/docs/texts/116/#3](http://www.urbanterror.info/docs/texts/116/#3)

I personally don't like any LAN/online games from Wine. Wine adds some lag that makes the gaming experience not so great.

---


---
title: "Streaming server"
date: 2010-10-05
forum: Server Platforms
---

### Post by tatewaki on 2010-10-05
Hey I'm trying to setup a streaming server so that i can stream the videos and shows i have placed on my server, places at a different location then my home.
I'm unsure if MythTV will do what i want or if there is some better software for it. Oh and I do not have a recording card, and i will not record TV, it's just DVD i have ripped that i would like to stream.

Right now i can stream my videos if i mount my SSH connection as a local drive and play it like a local file, but that is bit to techy for my girlfriend. 

So basicly i would like to:

1) Stream my videos over the internet 
2) Stream my music over the internet
3) Would be nice with a pretty interface, with album arts etc.
4) Have a web interface or maybe a app

Do anybody have some information?

---

### Post by arrrghhh on 2010-10-05
So if you just want to stream on your LAN, and the clients are Windows you can easily do this with a UPnP server - PS3MediaServer, miniDLNA, uShare... there's more.  Mediatomb, twonky also come to mind.

This is only local tho, it won't work over the WAN.

For music, I'd say Subsonic hands down.  There's a ton of other ways to do it, Jinzora and Ampache come to mind.  I use mpd personally, but the learning curve was kinda ridiculous IMHO.  I love it now, but just use it to play music locally to my amp.  Haven't sorted out streaming with mpd, so I just use Subsonic on my phone :D

BTW, Subsonic is a completely self-contained music streaming server.  The phone app is just a client, so fear not there!

---

### Post by tatewaki on 2010-10-05
Well I have found lots of ways to stream my music, the real problem is the video.

But i have seen that Jinzora also supports Video, so i will test that. 
I guess i would wish that i could get a mediacenter experience over the internet.

---

### Post by arrrghhh on 2010-10-05
Well unless you have a HUGE bandwidth pipe, streaming video over the internet is kind of... useless honestly.

Perhaps you are better off in Denmark, but here in the US I have a huge download pipe with a very puny upload pipe.  So I don't even want to think about trying to stream any video over the internet.

VLC does it quite well I've heard, but that's not really a complete streaming suite, so I know that's not what you're looking for - but perhaps there is some suite that utilizes VLC as a backend...?  I'm not sure.

---

### Post by tatewaki on 2010-10-05
Well i got a 50/50 Mbit so the bandwith is no problem.

Well maybe something like SinCast3? I have to look into that :)

What i have thought about is to mount the server with ssh, and then maybe have a media center on the computer in my home.

---

### Post by tatewaki on 2010-10-05
Okay i just installed xbmc, and there I saw that I can select FTP as a source. So i think i will setup a FTP server and see if that works.

(I have tested it with my SSH mount and that works perfect)

---


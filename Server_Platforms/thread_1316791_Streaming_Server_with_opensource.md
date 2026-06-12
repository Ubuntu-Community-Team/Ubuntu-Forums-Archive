---
title: "Streaming Server with opensource"
date: 2009-11-06
forum: Server Platforms
---

### Post by budiw on 2009-11-06
Hello all,

I wanted to built a sites just like m.youtube.com. A friend of mine said, that m.youtube.com is built using helix from realnetworks.com.

Another friend of mine said, you should use helix if you want to play your video from mobile-phone. He said, he already try everything and finally he gave up and buy a license of helix. That cost a fortune. ](*,)

Is there any opensource solution for streaming to mobile phones? Any suggestion appreciated.

Thank you.

Budiw
:D

---

### Post by terazen on 2009-11-06
Have you looked into darwin streaming server or red5?  I've only streamed to pc's and haven't used helix so I can't say how they would compare.  I'm curious to know what you find if you test them.

---

### Post by i.r.id10t on 2009-11-06
Darwin Streaming Server from Apple, I think there is a free (if not Free) version of Helix as well.

---

### Post by budiw on 2009-11-07
@terazen: I've just tested DSS, and it doesn't work streaming to mobile phones. I tested in PC, the streaming is OK. But when I tried on the mobile phone, It stucks. I tried with Blackberry using wifi connection.

And I test my friends server using licensed helix, the streaming is OK on Blackberry using wifi. :(

I Think I would like to try red5. I just know now. :D

@i.r.idi0t : Helix Community is not supported with mobile phones. I Already tried. But is oke when I open with PC.

Thank you.

---

### Post by budiw on 2009-11-09
@terazen: I don't think red5 will do the streaming to mobile phone. ([http://www.red5server.org/](http://www.red5server.org/)).

And I just tried ffmpeg with ffserver. It does good streaming on PC but no streaming at all on mobile phone.
DSS is just the same with ffmpeg.

Any other ideas?

---

### Post by ZALinuxDude on 2009-11-09
Hi all please excuse me if i am hijacking this thread but i would just like to know as far as video streaming is concerned what would be the best to use for an application such as :

I have a home network (or rather i'm in the process of setting one up) which i have set up for 1) storing movie files (DivX, AVI, etc) and MP3's and since this subject was brought up i asked my self is there some way that i can stream these files directly off the server rather then copying the file to the local client, the thing is my experience is that any form of streaming can be quite tedious and in some cases very irregular and jumpy if i decided to go this route how would i go about achieving this, when the specs are as follows..:

Server:

Pentium 4 2.X (cant remeber) 1gig Ram (2x 512 modules)
40 gig OS Hdd
40 gig Data Hdd
160 gig Data Hdd
Ubuntu Server 9.10 or 8.04 LTS (depends which runs better still testing)

Clients :
Desktop pc,
Core 2 Duo 2.6
4gigs ram
250gig hdd
Windows 7 ultimate

Laptop,
Pentium celeron M
2.5 gig ram
160gig hdd
Windows XP pro SP3

CAT5e cabling
gigabit switch
(D-Link DGS-1005D 5-port 10/100/1000 Mbps Gigabit Ethernet Switch)

I'm pretty sure the Hardware is capable but what soft ware would you guys (and girls) use for this use?

---

### Post by Lars Noodén on 2009-11-09
> **budiw said:**
> 
Is there any opensource solution for streaming to mobile phones? Any suggestion appreciated.


It depends on the standards.  TCP, especially for IPv6, supports multicast.  On top of that layer you have HTTP or RTSP.  On top of that layer you have the data format, like MPEG, Quicktime or Vorbis.

Which layer is giving your friend problems?



As far as software goes you have these (at least) to choose from:

VLC
[http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html)

FFMPEG
[http://ffmpeg.org/](http://ffmpeg.org/)

Icecast
[http://www.icecast.org/](http://www.icecast.org/)

and 

Darwin
[http://developer.apple.com/opensource/server/streaming/](http://developer.apple.com/opensource/server/streaming/)

---

### Post by i.r.id10t on 2009-11-09
DSS does stream to mobile devices - I'd recommend joining the users listserv for it and checking the archives.

---


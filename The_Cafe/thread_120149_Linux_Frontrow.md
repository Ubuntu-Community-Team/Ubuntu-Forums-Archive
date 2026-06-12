---
title: "Linux Frontrow?"
date: 2006-01-20
forum: The Cafe
---

### Post by ossi on 2006-01-20
Hi!

I am just curious if anyone works on something similar like Frontrow or anything like this? I am not too much into it and don't know too much about, but I am just now going to bed and somehow saw something from Apple and then thought  I would use Frontrow now to listen to some music and sleep. Just interested....

---

### Post by drizek on 2006-01-20
you can do everything front row does with regular apps.

if you want a home theater type thing though, there is mythtv.

---

### Post by xequence on 2006-01-20
I think something like this would be a great idea.

Make a whole new DE like frontrow where you can access ALL media from one program that looks really cool.

---

### Post by drizek on 2006-01-20
Mythtv!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Monsieur le Comte on 2006-08-06
But is there an easy app that lets you browse all your media files for linux?  

I'm installing Ubuntu right now and desperately want one, without going through the hassle of setting up MythTV.  I don't want to record video, I just want a nice clean way to browse and watch it on my TV.

I've heard of Totem.. How is that for interface/browsing?

---

### Post by bobbybobington on 2006-08-06
since it would deal with media and stuff it should install all the media codecs automatically. some xgl integration would be nice:grin:

---

### Post by Monsieur le Comte on 2006-08-06
Is it possible to install JUST the MythTV frontend to browse & play movies/images/music?

---

### Post by codypumper on 2006-08-06
I attempted installing MythTV and kept getting errors...

---

### Post by gurgle on 2006-08-06
i would LOVE to see MediaPortal ported to Linux. 

team-mediaportal.com 

its the only reason i boot into windows. 

yes, i can use MythTV, but MP is nicer.

---

### Post by Wormsie on 2006-11-25
I'd be interested in programming something like that - mainly because I like the idea to be able to control my PC as a multimedia centre with a remote - but so far I haven't managed to compile a single working Linux application :D

---

### Post by teet on 2006-11-25
I think it would be a neat idea.

MythTV (when properly setup) can do most of the things you want.  Maybe they should work on making MythTV easier to install or maybe there should be a separate mythtv distribution (mythubuntu...like knoppmyth).

MythTV is really an awesome program if you can manage to get it working.  I never had much luck with MediaPortal...it was incredibly slow and usually crashed when I tried to watch/record TV with it.

-teet

---

### Post by tageiru on 2006-11-25
The GStreamer people are working on something similar called [Elisa](http://www.fluendo.com/elisa/).

---

### Post by Beamerboy on 2006-11-25
MythTV is great.  I have been running it for about 6 months or so, with a lot of the plugins like mythgallery, mythphone, mythvideo, mytharchiver and mythmusic.

There is nothing difficult about setting it up if you follow the wiki guide.  The problem is if you try and install it from the Ubuntu repos, they seem to do a really really bad job with mythtv.

The best way to install it is to install the dependencies via the repos but then build mythtv from the stable svn checkout.

I managed to get it working the first time I tried, so if I can do it, no reason why others can't.

Start with "sudo apt-get build-dep mythtv" and everything just falls into place after that.

Then if you install lirc you can have remote control via a handset too.  I am in the UK and have sky tv which uses a set top box for decrypting the signal, I am able to control that box with a home made serial Infrared blaster (which I made for a couple of bucks) and a microsoft media center edition remote control.

You can find the circuit diagram for an IR blaster on my site here:

[http://www.paladine.org.uk/ir_blaster.jpg](http://www.paladine.org.uk/ir_blaster.jpg)

You can also join #mythtv-users on irc.freenode.net which is full of very helpful people.

Paladine

---

### Post by apoclypse on 2006-11-26
Elisa seems to be the best wannabe frontrow type thingy. It uses opengl to draw its interface and eventhough I think the ui can use some work its as simple to use as frontrow and extremely simple to install (I wish the same could be said bout mythtv). I see mythtv as mor of a windows mce or a tivo type thing where dedicated pc is used for a htpc. Frontrow is exactly what its name implies a "front" end for its media apps such as itunes, quicktime, iphoto, dvdplayer etc. It doesn't do much more than cover  up these apps in the background. Elisa is more like the MCE frontend in this respect as it uses a centralized program to do everything without loading other apps in the background. The great thing about Elisa is that it will have the ability to be extended by modules. At the moment it doesn't do tv viewing, but a modulecan be written that can do this is in the future. I still they should work on the ui. Hopefully, the ui can be configured any which way you want and there should be options for different animations. Its being worked at the moment so expect some rough edges, but it does work rather well.

---

### Post by Beamerboy on 2006-11-26
I totally disagree with your interpretation of MythTV.  People may CHOOSE to dedicate an entire pc for it but that is certainly not required.  I use MythTV on my desktop system and it sits in the bottom left corner of my right hand monitor taking up just over 1/4 of the screen with xchat above it and Gaim chat windows next to it (I have a xinerama setup).

I have the MythTV window set to the same resolution as a 4:3 PAL TV (720x576).

Furthermore, there is nothing difficult about setting up MythTV if you simply follow the very comprehensive instructions.  As previously mentioned do not try to install it from the Ubuntu repos, they do a very bad job of it and I have yet to find anyone who has managed to get it to work via the official repos.  The problems most people encounter are not related to MythTV but are related to bad packaging by Ubuntu for this particular suite of applications.

Paladine

---

### Post by ixus_123 on 2006-11-27
oxine is also worth a look

[http://oxine.sourceforge.net/]("http://oxine.sourceforge.net/")

---

### Post by davim on 2008-01-15
Oxine and elisa look great and are lighter than  mythtv and you also have entertainer:

[https://launchpad.net/entertainer](https://launchpad.net/entertainer)

[http://oxine.sourceforge.net/](http://oxine.sourceforge.net/)

[http://elisa.fluendo.com/screenshots/](http://elisa.fluendo.com/screenshots/)

---

### Post by Badjaccur on 2008-01-16
Old but interesting thread if you ask me. Elsia is becoming a very nice Frontrow clone and using it to watch TV is possible btw. It's a [rather dirty hack]("http://elisa.fluendo.com/forums/?forumaction=showposts&thread=45&forum=1&start=0") for now but every update Elisa gets more fun stuff. The developers have added a Youtube, Stage8 and a Flickr plugin and much more is on the way.

---

### Post by airtonix on 2008-01-20
problem with elisa is it require a compositing desktop enviroment like compiz.

not cool.

---

### Post by DeadSuperHero on 2008-01-21
LinuxMCE looks pretty nice, try taking a look at that.

[http://linuxmce.com/](http://linuxmce.com/)

---

### Post by bb10 on 2008-01-21
XBMC for linux. Still in development though... :)

---

### Post by gforcing on 2008-03-27
XMBC, for sure.

---


---
title: "anyone use media tomb have this?"
date: 2011-03-11
forum: Server Platforms
---

### Post by adduds on 2011-03-11
on if i browse media tomb with anything but my ps3 i get doubles/tribles/quadrubles etc... actually can be as many as 8 of my files

ie. rhythmbox, vlc, totem

any clue on why or whats gonig on?

---

### Post by arrrghhh on 2011-03-11
Use PS3MediaSever.

Worlds ahead of MediaTomb IMHO.

There's even a [repo](http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589) for the newest one.

---

### Post by littlegreiger on 2011-03-11
I think that has to do with the transcoding settings in the config file. Unfortunately, I'm not at home right now so I can't check for sure. I'm pretty sure that you can setup multiple transcoding engines and that's why you're getting duplicates. So I'd say take a look at the config options for mediatomb and go from there.

The other thing to try is to restart mediatomb, I know that in the past I've had problems where my files were out of order and duplicated and simply restarting it fixed this.

As for arrrghhh's suggestion of using PS3MediaServer, I'd say definitely check it out. I have had problems in the past with it though, but the latest version seems to be doing quite fine. Right now I'm actually running both servers incase of problems with either one.

---

### Post by arrrghhh on 2011-03-11
> **littlegreiger said:**
> As for arrrghhh's suggestion of using PS3MediaServer, I'd say definitely check it out. I have had problems in the past with it though, but the latest version seems to be doing quite fine. Right now I'm actually running both servers incase of problems with either one.

Good point, there's no harm in running two media servers, assuming their ports are unique ;).

I should give mediatomb another shot, it was probably 2 years ago that I last used it - and the configuration was a nightmare, and I couldn't get it to transcode to save my life.  For better or worse, PS3MediaServer "just works" for me!

---

### Post by adduds on 2011-03-11
thanks muchly for your quick replies

the only reason i decided to try media tomb is because 1

i'm running ubuntu server edition so i'm practicing doing everything remotely with web admin

so is there a way i can install pms and configure it from cli?

number 2 pms worked great with my ps3 but when i went to access it from my laptop in rhythmbox wouldn't detect it? anyone ever run into that? i have the upnp extension installed..

---

### Post by arrrghhh on 2011-03-11
> **adduds said:**
> so is there a way i can install pms and configure it from cli?

number 2 pms worked great with my ps3 but when i went to access it from my laptop in rhythmbox wouldn't detect it? anyone ever run into that? i have the upnp extension installed..

Yup, no GUI on my server friend!  Everything pms-linux can be done from CLI - there's a conf file and everything!  No webUI so I guess mediatomb wins that battle.

Also, I've never tried to stream to anything other than a PS3 with PS3MediaServer.  For music I use DaaP via FireFly (among other things).

---

### Post by adduds on 2011-03-11
> **arrrghhh said:**
> Yup, no GUI on my server friend!  Everything pms-linux can be done from CLI - there's a conf file and everything!  No webUI so I guess mediatomb wins that battle.

Also, I've never tried to stream to anything other than a PS3 with PS3MediaServer.  For music I use DaaP via FireFly (among other things).

where will i find the conf file to alter the pms-linux server i can't seem to find it by running locate PMS.conf or pms.conf in /

two omfg ty soooo much for FireFly i installed that ran rythmbox and it is BYFAR the best for music! it streamed it all to my rhythmbox just as though i was browsing through my HD so it looks as though i'll just use pms and firefly I'm not really liking media tomb

any other info hit me up thanks again for all your guys help!

---

### Post by arrrghhh on 2011-03-12
> **adduds said:**
> where will i find the conf file to alter the pms-linux server i can't seem to find it by running locate PMS.conf or pms.conf in /

two omfg ty soooo much for FireFly i installed that ran rythmbox and it is BYFAR the best for music! it streamed it all to my rhythmbox just as though i was browsing through my HD so it looks as though i'll just use pms and firefly I'm not really liking media tomb

any other info hit me up thanks again for all your guys help!

Check out that thread on pms-linux, assuming you installed it from that thread.  He has directions on how to configure it, and that forum is a great resource for PS3MediaServer ;).

---


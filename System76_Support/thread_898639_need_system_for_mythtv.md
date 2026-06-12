---
title: "need system for mythtv"
date: 2008-08-23
forum: System76 Support
---

### Post by eppo on 2008-08-23
i was thinking of replacing the extremely old pc i have running the myth-frontend, and also replace my existing server. going to replace the frontend with the koala mini and my p4 1.8 server with the Eland Pedestal. the server has many uses. its going to be the mythbackend, i also use it as a gateway, and a fileserver. right now i just dvr SD tv, but in the future i plan on getting the hauppauge HD-PVR and record HD content as well. so i want to make sure that my server, and my koala is powerful enough to record and playback all the conent. for the koala, i plan to get the Core 2 Duo T5750 2.0 GHz 667 MHz FSB 2 MB L2 upgrade, and maybe do a memory upgrade to 1gig, also upgrade to the 250gig hd, so i can rip dvd's with it. for the server, i'm going to upgrade to the Quad Core Intel Xeon X3210 2.13 GHz 1066 MHz FSB 8 MB L2 65nm processor, 2gigs of memory. do you think that this would be good enough. any opinions would be great. thanks

---

### Post by thomasaaron on 2008-08-25
That sounds pretty reasonable to me. I'd up the RAM on the Koala to at least 2G, though.

---

### Post by nanonils on 2009-06-09
How did this setup work out for you? I'm also in the process of setting up a server and 2-3 clients that will have to be able to run Mythbuntu at home. I am new to all of this but I have been so happy with the ease of installing and using Ubuntu both at home and at work that I will take the plunge.

Here is the planned setup: 
The Pedestal as a multimedia and file server and one Wild Dog, one Meerkat NetTop and one Lenovo T61 laptop as clients.
Comcast will be the high speed ISP at our new place (from what I read I'll have to use a specific Comcast/Linux-friendly router because of that).
There will be maybe a Wii or a BluRay player containing gaming box, too.
Music, TV, gaming: all in the living room.
TV: two further rooms.

My questions are:
What are the specs of the machines you ended up getting? In particular, how much storage space and what RAID configuration? 2TB as the upper limit for the Eland Pedestal almost sounds like it might not be enough in the long-term for HDTV. But the Eland Pro Pedestal is quite a step up price-wise. Cheaper NAS (e.g. [www.drobo.com](www.drobo.com)) on the other hand is not very good at streaming video, from what I've read. 
Are you running ext4 to handle the large files?

I am confused about whether hardware encoding or software encoding is the way to go:
I want to be able to encode at least two channels in HDTV simultaneously yet watch or listen to something else at the same time. Should I simply go with a beefy multicore server for software based encoding? Is hardware encoding better? Did you put 2 HDTV hardware encoding cards into your server (DViCO FusionHDTV5 RT Gold looks like a good choice at [http://www.mythtv.org/wiki/Tuner_Card#Cards_that_work)?](http://www.mythtv.org/wiki/Tuner_Card#Cards_that_work)?)
I don't understand why [www.mythbuntu.org](www.mythbuntu.org) lists a graphics card as a general requirement. Isn't that only needed in the frontend?

Would it be better to just get a maxed out Wild Dog and stick additional TB-sized HDs in it or would the permanent-on recording and wear-and-tear be too much for non-server class equipment? I am not very concerned about chances of data loss, I have different means of saving crucial stuff.

Another concern that I have is that the cable socket happens to enter in the living room. The mythbuntu server backend has to be here, doesn't it? Is the heat generation too much to stick it into storage furniture to suppress the noise (the power supply is an amazing 500 to 800 W)?

Thanks!

---


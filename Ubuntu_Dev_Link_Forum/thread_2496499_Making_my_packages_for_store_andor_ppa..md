---
title: "Making my packages for store and/or ppa."
date: 2024-03-31
forum: Ubuntu Dev Link Forum
---

### Post by tychosoft on 2024-03-31
It is hard for me to understand which are correct forums for some questions for some topics these days. I am also blind so my concern these days is os accessibility.  However, at the moment, I am simply trying to decide if I want to make a ppa for my newer packages or even do snap/store builds.

This would be things like the coventry phone system, bordeaux telephony application server, apollo web management console (now in AlpineLinux testing), and the partisipate Qt client. These are generally described on [https://www.tychosoft.com/tychosoft](https://www.tychosoft.com/tychosoft) and most are licensed using the GPLv3. I already know how to make .deb packages and how to upload to a ppa. I have internally built and tested most things for Ubuntu locally under multiple architectures, and I am just wonder if anyone else would want these things.

---

### Post by TheFu on 2024-04-02
I don't know anything about those applications.

I've never setup a PPA or created a snap package, so feel 100% free to ignore what I've written here.

If the software is packaged in a way that end-users can easily install, configure and use, then both a PPA and a snap package are the ways to go.  Snaps have constraints that may make the software not work, especially in a corporate environment. If you find that the snap package works and works for others, then great!  Release it as well.  

Snaps (none of them) work under my normal user account on Ubuntu.  They force some things that nobody else forces and I find the suggested work-around to be impossible for our needs.  OTOH, it seems that most snap users aren't impacted, so those mandated constraints don't usually matter, until you need access to hardware.  Snap packages can be nice for the appropriate use.

The more dependencies there are, the better suited a snap package is - that's my feeling.  Since most versions of Ubuntu aren't based on Qt, those libraries would need to be dependencies and included in the snap dependencies, I'd guess.  I like **AppImages** better, since they bundle the software AND they work for all my users. Also, AppImages don't have constraints, so when someone wants to add constraints around an application, they can choose which constraint system they will use.  I prefer **firejail**, but both **firejail** and snaps cannot be used at the same time.  For typical Ubuntu end-users who don't know about firejail (or the other 10 constraint management systems), snap-based constraints are better than nothing, if there is actually a good reason for it.  For example, a snap package for a calculator that doesn't do any networking makes very little sense to me.  Forced constraints when there isn't any risk, is a waste of resources and locks out some functionality.

I have lots of little tools that were created to "scratch an itch" of my own, but they've never been built to work in a way that is useful to others. Those little tools pull data from 2 places that have a 14 day lifetime before it is useless and the data gets translated to a merged, specific, output XML format specific to my location and about a radius of 10 miles around me. There are about 25K input records that I grab every 7 days to transform into XML.  There is some overlap where 5+M people nearby might find part of the data useful, but very few people know about it or care enough to bother.  I'd guess fewer than 100 nerds would care.  Even in the nerd community, I've never found anyone who cared beyond a slight interest, but certainly not enough to setup a similar system for their own use.

---

### Post by tychosoft on 2024-04-05
What I do touches upon servers and IoT as well.  A ppa seems a good way to internally produce redistributable builds without having to use local resources I may not have, even if just using it for myself to install other machines. It does seem possible to also do a snap for headless services and use it in things like Ubuntu core.  I once used a snap of rocketchat because I was too lazy to set it up at the time, but I found different issues with lxd as a snap, storing images, and accessing drives. A snap with a stack with apollo, bordeaux, and coventry would look a lot like rocketchat, and would be very self contained.  Partisipate is a desktop Qt application, so I guess it would be more natural to think of as a potential snap / store app.

---


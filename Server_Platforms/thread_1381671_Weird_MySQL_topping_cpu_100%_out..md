---
title: "Weird MySQL topping cpu 100% out."
date: 2010-01-15
forum: Server Platforms
---

### Post by Acid7711 on 2010-01-15
My server is a decent rig, consisting of core2duo, 4GB ram, ubuntu 64bit server, 2- 1TB RAID 1 (mirrored) drivers, (I've tried other distro's too just to make sure, same problem)

The weird thing is, I was using the exact same code/database/setup at work and it goes quickly.  At home, it lags the cpu like crazy.


Basically, I've narrowed my select statements down as far as they can go, no select * from, bla bla, very specific, small statements.  Realativly small db consisting of 1000 or so "tickets" 8 tables (not all joined at once, usually only 2-3 at once)


Like I said, at work this thing flies, at home, it pokes, and when I run top from command line, I can see mysql shoot to the top and just chew the cpu up at 100% until the command finishes 30+ seconds later.  At work it's almost instanatious.  I don't get it.

Running a simple apache, mysql, php setup.  Tried multiple distros, and it's my nas too, so i was running netatalk and samba, but to see if those were the problem, I took them out of the equation and did a fresh install with JUST the database/webpage stuff.  Same result.   On Fedora, it's *slightly* faster than ubuntu server for some reason.


Funny thing I don't get is, I can go into phpmyadmin, run the EXACT same command I'm pulling from the php page, and it takes literally 0.012 seconds to run he command, so it's not taxing at all until I pull it through php.


What's the deal here? Can anyone lead me to an answer? I need to get this down to a decent time here for pulling these queries. I know the server at work is probably far beyond what I'm running at home, but the hardware I've got here isn't exactly old crap either.


I've even run it straight on the machine itself, and it's slow. I don't get it. I can't figure it out.


Thanks for any help anyone can offer.

John


**edit:  btw, I've tried both the onboard "hardware" (software) raid, and the ubuntu software raid with the same results : /   I don't think it would be the raid.  I have the raid because I originally had one of my drives go out on me and almost lost all of my data.  So, this time it's raid 1, with external weekly backups.

---


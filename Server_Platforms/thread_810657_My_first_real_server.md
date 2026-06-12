---
title: "My first real server"
date: 2008-05-28
forum: Server Platforms
---

### Post by Twizzle on 2008-05-28
Last weekend I set up a home server using the 8.04 desktop version. Having now read a whole heap of posts and asked a few questions, I have decided to take the plunge and opt for the server edition.

I am an Ubuntu newbie so I still would like the 'option' of a GUI of sorts. I have not yet decided between something like Webmin, or installing Gnome onto the server. (Please don't turn this into a GUI or no GUI post - I have made my decision :) )

I have a couple of questions before I start though:

1. Does the server edition auto update or do I have to keep checking for updates by running some sort of command every day? The reason I ask is that I notice the Desktop edition is often telling me about updates and I would hate to miss a critical one.

2. Partitions. I have two HDDs in the server at the moment, one 140Gb drive and one 320Gb. I was thinking of splitting the smaller into /root /swap and /backup from my main PC. How big would you recommend making the partitions for the install and swap seeing as there probably won't be a huge amount going onto it. I am also considering a separate /home partition (if you have one on the server edition?)

Cheers

John

---

### Post by NateMan on 2008-05-28
Sounds like you've done your research on this, I think webmin would be a nice fit for you, since it allows you to run updates and such from it as well as putting most server administration tasks at your finger tips. Gnome is kinda heavy and it isn't as easy to administer from as webmin. 

As far as partitioning goes I would recommend placing about 40gigs as your / directory. I can't see how I could even fill that up and it should give you a good bit of room. I'd also setup a partition for /var as well, probably of similar size. You'd probably be fine with a gig of swap space, how much ram do you have? 

I don't believe that the server automatically updates, as mine does not. I'm sure it could be easily scheduled, but I just manually do it every week or so. Its normally not too big of a deal for a small home server.

---

### Post by Twizzle on 2008-05-28
Thanks for that.

The system is an Athlon XP 2400 (underclocked to 1800 to be cooler) with 1Gig ram.

Sorry to sound stupid but what is the /var partition / directory and why do you recomend it as a seperate partition?

---

### Post by NateMan on 2008-05-28
Its were your log files are stored and eventually if you don't keep check on it, then it will fill up. Also its were webpages and such are stored, so its nice to be able to reinstall and have your webpage already ready to go upon setup.

---

### Post by heebus on 2008-05-28
As NateMan said, it's a good idea to put var on its own partition.  It bested me once!

Overnight I had a problem on my machine and had logs continuously filling up.  When I came in my office that morning my machine was really sluggish.  After a few minutes of investigating I noticed my root directory was 98% full (from the previous 50%).  When I did some checks to see where the space went, it was all in the var directory from the night prior.

I have since placed /var directory on its own partition and continue to do so to this day.  Oh, and I fixed the overall issue.

---

### Post by garethsimpsonuk on 2008-05-28
Aren't log files just ASCII txt files? Surely they don't take up much room? How big can it get yet when it has a hiccup?

---

### Post by heebus on 2008-05-28
It was a few gigs of mysql's binary log files.  I'm not exactly sure what caused it, because it was a while ago.

---

### Post by NateMan on 2008-05-28
Trust me, log files can fill up quickly, depending on whats going on. I normally just watch my / drive and go in and remove what I don't need, as my server is not partitioned in such a way. All of my newer ones however are.

---

### Post by heebus on 2008-05-28
It was something that burned me once, but never again.  It may never happen to you, but why risk it when you could create a simple partition.

---

### Post by bmathis on 2008-05-28
You should check out the Ubuntu Security Announcement list for those critical updates, then you'll know when you need to update and why.

[https://lists.ubuntu.com/]("https://lists.ubuntu.com/")

---


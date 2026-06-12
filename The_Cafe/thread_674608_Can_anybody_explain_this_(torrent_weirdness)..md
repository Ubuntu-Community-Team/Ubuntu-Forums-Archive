---
title: "Can anybody explain this? (torrent weirdness)."
date: 2008-01-21
forum: The Cafe
---

### Post by blueglue on 2008-01-21
Hi, I have an issue's regarding torrent downloads on a shared connection. The problem is that 4 people including myself are sharing the same connection to the internet via a wireless router (linksys WRK54G NOT the popular WRT54G). I am hard wired and the other 3 are wireless. 70% of the time we exist side by side quite happily on a 2M connection, however one guy likes to use torrents alot and this renders the connection useless to everbody else. 

Before anyone makes any recommendations on how to restrict torrent traffic by configuring the router I have to point out that this user is quite savvy and in the age of I.P changers/bouncers MAC AD changers and encryption it is damn near impossible to block torrent traffic (ISP's have problems with this so im not going to break my head on trying to filter). However after a beating around the head with my fairly weighty and robust late 90's Logitech keyboard he agreed to DL overnight which he does.

Right hear is the problem, I also use bit torrent and for ligitimate and legal reasons mainly downloading albums using the excellent Jamendo plugin now included in Rythmbox (i hope we see alot more of these CCL networks emerge). Somehow and I can figure it out, his pc always sucks up all the bandwidth and leaves me with about 5% of the bandwidth. As my connection is wired and his is wireless surely I have a better connection to the router, so how come his PC is getting all the bandwidth? My suspect some kind of encyption or a feature of his torrent client but i have no idea what as I am not a media whore and an opensource user so my need to know about advanced bit torrenting has been non until now.

My basic question is how do I get my fair share of the bandwidth? and how is this happening?

I use Ubuntu Gutsy, and have tried Azureus, KTorrent, deluge and QTorrent the results always the same.

He uses Bittornado on windows Vista.

Any light that could be shed on this please help!!!! P.S I hope this is in the right section of the forum!

---

### Post by ~LoKe on 2008-01-21
I hope you're not trying to use the same port as him.  Trying using one around 50000.

---

### Post by inversekinetix on 2008-01-21
lol, all use uTorrent and set the max download bandwidth to 1/4 of your total.

use different ports.

are the files youre both downloading equally seeded? do the people youre connected to have the same upload bandwidth?

---

### Post by bufsabre666 on 2008-01-21
there is the quality of serivce tab in the router info but thats hard to work with, id say tell him to lower his settings

---

### Post by Ocxic on 2008-01-22
try QoS scheduling in your router

---

### Post by el_ricardo on 2008-01-22
u just have to come to an agreement, thats what we do in our flat, one of my flatmates is just the same as yours, and we just agree to only start torrents at around 4 in the morning, you can set most torrent clients to schedule traffic, azureus can certainly do that

---


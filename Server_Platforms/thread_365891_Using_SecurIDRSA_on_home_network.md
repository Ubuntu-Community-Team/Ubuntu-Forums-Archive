---
title: "Using SecurID/RSA on home network"
date: 2007-02-20
forum: Server Platforms
---

### Post by Catsworth on 2007-02-20
Hi Guys,

I've been using SecurID fobs at work to set up some remote users, and it occured that this would be quite a cool technology to deploy on my home network to allow me to connect remotely (and securely) while I'm on the road.  At the moment my servers are tied down and have no access to the outside world, which is nice and secure but doesn't help me when I'm not at home.

I've searched Google and the forums here but can't find any information on how this might be accomplished.  

I'm fairly new to Linux and SecurID etc but I'm happy to do most of the learning/hard work myself - I just need a bit of a leg up to get me on the right path.  Are there any tutorials available, or could someone give me a quick run-down, on how this might be accomplished (if it's even possible that is.....)?

Do I need anything other than some software and some SecurID fobs?  Will it matter if these fobs are pre-used (the ones I'm looking at state that they "only have a two year life span left" so I'm assuming that someone else has used them previously)?  Is £20 or so a good price for 10 tokens?

Thanks :)

---

### Post by Catsworth on 2007-02-20
Sorry, forgot to mention:

The server is a Win2K box at the moment, but (as soon as I can find the time) I'll be taking all the files off of it, reformatting/partitioning the drives, and then installing Ubuntu Server.

---

### Post by Catsworth on 2007-02-21
Apologies for bumping this (won't do it again), I'm just getting a bit like a dog with a bone on this one (ie. won't let go).

I've carried on searching and poking around but still can't seem to find an answer to this on my own, is there anybody here that's tried this or managed to do something similar?

Am I trying to overcomplicate this?  Is there an easier way to achieve what I'm trying to do?

---

### Post by MJN on 2007-02-21
I very much doubt it's possible as if a free software-based server-side authentication module existed then there'd be no market for RSA's offerings other than supplying keys (and even then there'd be an open market of those if the alogorithm was known).
 
Incidentally, I suspect you'd need the seeds for the 2nd hand fobs in order to initiate the sync so if you do buy any for whatever reason make sure you get them!
 
Mathew

---

### Post by Catsworth on 2007-02-21
Hmmm.....

Ok, thanks for that.

So, that kinda begs the question - what's the best way to enable myself to log into my home box remotely _without_ leaving mysefl open to the morons that might try to take advantage of the fact that I've left ports open through my firewall to facilitate it?

Thanks again :)

---

### Post by MJN on 2007-02-21
Decent passwords? Better still, but potentially more inconvenient (often a trade off), public key authentication.

Mathew

---


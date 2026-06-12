---
title: "Syncing two servers"
date: 2008-05-01
forum: Server Platforms
---

### Post by dacool25 on 2008-05-01
Hey everyone,

I'm thinking about setting up a fail over cluster (Or at least my way of it =P).

What I wanted to do was set up a round robin DNS to go to two different ubuntu boxes in two separate physical locations.  Now I can get the round robin part easily, however what should I use to replicate the servers?

I was thinking about rsync over ssh.  If so, how can I do this?  Also if anyone has any other suggestions of how I should do this, I'm very open to them.

Thanks

---

### Post by HermanAB on 2008-05-01
Yup, rsync is your friend.  Since the servers are right next to each other, you probably need not use SSH encryption.  Just read up on rsync and put it in cron.hourly or cron.daily depending on how close the machines must be.

Cheers,

H.

---

### Post by dacool25 on 2008-05-01
Sorry, what I meant by two separate physical locations was that they'd be off of two separate geographic locations.  Will this still be possible?

---

### Post by HermanAB on 2008-05-01
Yes, but then you HAVE to tunnel over SSH.  It is very simple to set up and there are many examples in Google.  I'm using it to make backups over the internet, but I don't have any examples at hand.

H.

---

### Post by dacool25 on 2008-05-01
Cool!

My only other question is what should I have it sync?  The entire drive?

I am currently running ISPConfig Web Management software, so I would want that to be the same on both servers.

---


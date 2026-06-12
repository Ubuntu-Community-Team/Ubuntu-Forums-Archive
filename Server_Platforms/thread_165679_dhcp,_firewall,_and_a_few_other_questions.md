---
title: "dhcp, firewall, and a few other questions"
date: 2006-04-25
forum: Server Platforms
---

### Post by augied on 2006-04-25
Hi,
First, I'd like to say that Ubuntu amazing, blah blah blah, you've heard it all before so just pretend I said it too.  (It's late, I don't want to type much.)

Last week I finally got around to setting up a web server, I had been putting it off for months.  The server is currently behind a router.  What I would like to do is to connect it directly to the internet, and pass the connection on to the router, and the rest of my home network.  I want to do this because I use BitTorrent a lot on multiple computers and I'd like to limit their upload speed so that there's some left for the web server.  As far as I can tell, my router won't do that.
Here are my questions:
What's the best/easiest way to share a connection with limited upload speed?
I'll also need to do port forwarding.  How do I do that?
How can I set up a firewall to open certain ports only to computers on my network?
For a firewall, I'm currently using ipkungfu because it was the quickest to set up, but I'm open to suggestions for something else.
I can't think of anything else at the moment.

Thanks,
Augie

---

### Post by alamba on 2006-04-25
Firewall/Port forwarding/share a internet connection: Each of your question points to IPTables. Shorewall is a powerful gui tool to manage IPTables. 

A

---

### Post by FredSambo on 2006-04-25
I am just learning how to use IPTables and Shorewall has been a huge help!

---

### Post by augied on 2006-04-25
I've started reading some of the documentation and it looks great.  Thanks.

---

### Post by alamba on 2006-04-26
You're welcome. You might want to look into webmin too for managing shorewall/iptables.

A

---

### Post by fishfillet on 2006-10-03
> **augied said:**
> Hi,
First, I'd like to say that Ubuntu amazing, blah blah blah, you've heard it all before so just pretend I said it too.  (It's late, I don't want to type much.)

Last week I finally got around to setting up a web server, I had been putting it off for months.  The server is currently behind a router.  What I would like to do is to connect it directly to the internet, and pass the connection on to the router, and the rest of my home network.  I want to do this because I use BitTorrent a lot on multiple computers and I'd like to limit their upload speed so that there's some left for the web server.  As far as I can tell, my router won't do that.
Here are my questions:
What's the best/easiest way to share a connection with limited upload speed?
I'll also need to do port forwarding.  How do I do that?
How can I set up a firewall to open certain ports only to computers on my network?
For a firewall, I'm currently using ipkungfu because it was the quickest to set up, but I'm open to suggestions for something else.
I can't think of anything else at the moment.

Thanks,
Augie

Actually, ipkungfu can do port forwarding, internet connection and much more!

I use ipkungfu and it does the job for me.

---


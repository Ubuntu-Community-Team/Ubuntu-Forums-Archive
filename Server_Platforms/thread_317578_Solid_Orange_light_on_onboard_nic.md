---
title: "Solid Orange light on onboard nic"
date: 2006-12-12
forum: Server Platforms
---

### Post by vv88 on 2006-12-12
Hey all, let me just say that I've tried numerous linux releases and have been extremely pleased with ubuntu.  As a newer user (4 months) I do have a lot of questions, but I'll stick to my main concern.  I hope this is the correct forum.

One of my pcs has an asus a8n sli motherboard and since unintalling/reinstalling windows my orange nic light turned from solid green to solid orange.  Well, I grew ectremely tired of windows and decided to go all linux on every pc.  This particular board has:

1.5 gb ram
1 IDE 40 GB Drive
1 SATAII 120 GB Drive
1 CD/CDRW Drive
1 DVD/DVDRW Drive
AMD64 Athlon 2.4ghz processor

I'm thinking this is a problem with the bios but I may be way off track.  Again, I'm hoping this is the correct forum to ask this question...this is not a server.

Any help is appreciated.

---

### Post by Zelut on 2006-12-12
so does the nic work at all?  My guess would be a BIOS issue as well.. not sure what setting to look for (too bad BIOS' can't be standard) but if its OS-independent that would be my best gues..

---

### Post by vv88 on 2006-12-12
Well, you are correct, it's not an OS dependent issue.  Actually, I've looked long and hard for answers (this includes mobo forums, newsgroups, simple web searches) and have not come up with an answer. The digging only resulted in the possibility that my mobo thinks it's connected to a much faster connection.  I'm not sure if that's the case.

As far as the status of the nic, it connects fine.  However, past experience tells me that this may be an indication/warning of future problems.  I sure hope not.

Thanks for the response kuyaedz.  Any insight is welcomed. Although I realize this probably has nothing to do with ubuntu, I'm running out of resources.

---

### Post by chrisfay on 2006-12-12
Have you tried removing and re-installing the network drivers?

Anything in our datacenter that turns orange gets immediately replaced since, as you mentioned, it is usually a sign of things to come. But since you also mentioned that its not a server, it may not be vital until it actually breaks. 

Good luck!

---

### Post by vv88 on 2006-12-13
Well, thanks for the reponses.  After a bit of debating I pulled a card out of a pc that I wasn't using.  The light is green once again. btw, after digging deeper, the orange light did indicate a 100 mbps connection, if only :rolleyes:

---

### Post by MJN on 2006-12-13
> **vv88 said:**
> Well, thanks for the reponses. After a bit of debating I pulled a card out of a pc that I wasn't using. The light is green once again. btw, after digging deeper, the orange light did indicate a 100 mbps connection, if only :rolleyes:
 
What was on the other end of the patch lead that was plugged into your NIC? At a guess I'd say it was either a cable modem or a router - in which case a 100mbps connection between the two is quite normal... it's got nothing to do with the speed at the other end (i.e. connecting to the Internet for example).
 
I think you were looking for a problem that didn't exist. :)
 
Mathew

---

### Post by vv88 on 2006-12-13
mjn, good to know...though I don't fully grasp what you are saying. So it's simply indicating the communication between the router and nic, not the router and net?  Yes, obviously I'm running through a router that's connected to a DSL modem.  The reason it had me so baffled is that all other components with connections had green lights (as this one did originally and up until about 2 weeks ago).

I learn something new everyday.  Thanks!!

---

### Post by MJN on 2006-12-13
Spot on.

You may be wondering what's the point of having a 100mbps connection to your router yet only a 4mbps (or whatever) out the other side but you must also remember that your router is serving your local LAN (if you have one) and hence you can enjoy 100mbps throughput to your other machines.

The solid light is a common indicator that a 100mbps connection has been established at both ends (and it stays unlit for 10mbps).

Mathew

---


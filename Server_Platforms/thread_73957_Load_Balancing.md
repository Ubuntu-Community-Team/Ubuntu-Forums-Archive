---
title: "Load Balancing"
date: 2005-10-10
forum: Server Platforms
---

### Post by markgreene on 2005-10-10
I have two internet connections at my house, one a DSL and one a Cable. I would like to have three NICs, two of them taking in the DSL and the Cable, and the last running out to a switch where anyone can plug up and get online. The machine should then balance the two connections evenly among requests.

How can I do this?

---

### Post by mlomker on 2005-10-10
I hate to say that it *can't be done* because that's rather absolute, but I'm sure not aware of any way to do it.  Generally this can only be done by Internet Providers because you need to run BGP in order to policy route which traffic comes back in through which interface.

You can load balance if both connections go to the same router on the other end.  I have 4 T1's here at work that are load balanced that way.

---

### Post by sickdude on 2005-10-10
a managed switch, this is how we load balance 4 webservers @ my work.

---

### Post by LordHunter317 on 2005-10-10
You can't do what you want.  At best, you can get route balancing on a per-connection basis.  That's still likely to be far from ideal.

---

### Post by muszek on 2005-10-10
In Poland there are many "amateur LANs" (people chip in for a DSL or something and share the costs).  what they often do is route p2p traffic through one line and all "regular ports" (default http, pop3, etc.) through the other.  I can't give you any technical details, though.

My friend is an admin of one such LAN - 200 computers, they have 1Mbit up/down for p2p and 2Mbit/256kbit for the rest.  It works pretty nice.

---

### Post by mlomker on 2005-10-10
> what they often do is route p2p traffic through one line and all "regular ports" (default http, pop3, etc.) through the other.

Yes, that would work.  That's actually layer 4-7 routing and somewhat advanced.  I have some expensive Cisco content switches that can do that.  I'm not sure how you'd accomplish it using a regular linux box.

---

### Post by markgreene on 2005-10-11
well I appreciate the comments but it does seem that whatever COULD be done is beyond my abilities right now. Let me know if you come up with something else.

---


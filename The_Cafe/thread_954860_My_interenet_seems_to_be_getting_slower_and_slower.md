---
title: "My interenet seems to be getting slower and slower..."
date: 2008-10-21
forum: The Cafe
---

### Post by Lord Xeb on 2008-10-21
Just loading this page takes forever sometimes compared to what it use to be. I sometimes have to go downstairs and unplug then plug back in the wireless just to get things to speed up somewhat. What is going on? Is there anyway to fix it? And no, I do not have the luxery of installing Tomato or DD-WRT unfortunately... the routers are my parents and they would kill me.

---

### Post by LaRoza on 2008-10-21
> **Lord Xeb said:**
> Just loading this page takes forever sometimes compared to what it use to be. I sometimes have to go downstairs and unplug then plug back in the wireless just to get things to speed up somewhat. What is going on? Is there anyway to fix it? And no, I do not have the luxery of installing Tomato or DD-WRT unfortunately... the routers are my parents and they would kill me.

There are several places the problem can be. In your ISP, in the router, or in the computer.

Does anyone else have this problem?

---

### Post by kk0sse54 on 2008-10-21
:lolflag: I've been having  pretty much the exact same thing happening to me and I have pretty much no idea what to do especially since the most help my ISP can give me is to unplug and plug my router back in again. Unfortunetaly I have pretty much no skill in this area at all since it's my parent's router and I'm not allowed to touch it or mess with our network in any way.

---

### Post by MaxIBoy on 2008-10-21
Comcast has been giving me more and more grief since we got it. Typically, your ISP is adding more customers without upgrading some of the decades-old equipment they use. (And if you're using a torrent program... well, just google "comcast throttling torrents.")

---

### Post by Lord Xeb on 2008-10-21
Well I figured it out. It was my network manager and FF itself. My router sometimes needs to reset its ram but other than that it is was FF. Just changed a few settings and bam, much faster and pages don't take forever to load.

---

### Post by zmjjmz on 2008-10-21
> **Lord Xeb said:**
> Well I figured it out. It was my network manager and FF itself. My router sometimes needs to reset its ram but other than that it is was FF. Just changed a few settings and bam, much faster and pages don't take forever to load.

Please do tell, this has been happening to me.

---

### Post by patrickballeux on 2008-10-21
In my old Averatec laptop. the wireless card always connect at 1M and I you reported, it is slow.  What I do, once connected, it open a terminal and run "sudo iwconfig ra0 rate 11M", then everything work as expected.

Have a look at your wireless connection by running "iwconfig" in a terminal.  This will tell you if the connection is good between your wireless card and the router.

Then, you can try playing with the rate, to see if there is a better one the the one selected by default.  Maybe it is too high.  For internet access, 11M is more than enough....


Good luck!

---

### Post by Lord Xeb on 2008-10-22
Well, first off I installed wicd and that helped out quite a bit in itself. Then I did some hacks to FF. I will have to get them from my bro, so I will update you guys on what I did (and it is not the usual hacks).

---

### Post by mips on 2008-10-23
Here in deepest darkest Africa the internet has always been slow.... ;)

---


---
title: "Is there an Internet battle/war going on?"
date: 2013-02-25
forum: Security
---

### Post by davidvandoren on 2013-02-25
I just came from work and was pretty nerved that all the windows Machines there couldn't access google and the Internet explores seemed to be hijacked.
One pc could access google with Firefox though , but seemed to be infected with something. 

Now I am back home and the internet here is strange too.

First of all loading google takes for ever. My wife says she cant access youtube and people are complaining about this on the internet as well. 

after checking my log files I found this ```
Feb 25 21:31:05 david-desktop kernel: [ 1928.482641] [UFW BLOCK] IN=ppp1 OUT= MAC= SRC=74.125.31.132 DST=Not for you LEN=77 TOS=0x00 PREC=0x00 TTL=41 ID=57499 PROTO=TCP SPT=443 DPT=50412 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
Feb 25 21:31:06 david-desktop kernel: [ 1929.244299] [UFW BLOCK] IN=ppp1 OUT= MAC= SRC=74.125.31.132 DST=Not for you LEN=77 TOS=0x00 PREC=0x00 TTL=41 ID=57501 PROTO=TCP SPT=443 DPT=50412 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
Feb 25 21:31:07 david-desktop kernel: [ 1930.768078] [UFW BLOCK] IN=ppp1 OUT= MAC= SRC=74.125.31.132 DST=Not for you LEN=77 TOS=0x00 PREC=0x00 TTL=41 ID=57502 PROTO=TCP SPT=443 DPT=50412 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
Feb 25 21:31:10 david-desktop kernel: [ 1933.815695] [UFW BLOCK] IN=ppp1 OUT= MAC= SRC=74.125.31.132 DST=Not for you LEN=77 TOS=0x00 PREC=0x00 TTL=41 ID=57503 PROTO=TCP SPT=443 DPT=50412 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
Feb 25 21:31:16 david-desktop kernel: [ 1939.910957] [UFW BLOCK] IN=ppp1 OUT= MAC= SRC=74.125.31.132 DST=Not for you LEN=77 TOS=0x00 PREC=0x00 TTL=41 ID=57504 PROTO=TCP SPT=443 DPT=50412 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
Feb 25 21:31:26 david-desktop kernel: [ 1949.883540] [UFW BLOCK] IN=ppp1 OUT= MAC= SRC=74.125.31.132 DST=Not for you LEN=77 TOS=0x00 PREC=0x00 TTL=41 ID=55750 PROTO=TCP SPT=443 DPT=50412 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
Feb 25 21:31:36 david-desktop kernel: [ 1959.855901] [UFW BLOCK] IN=ppp1 OUT= MAC= SRC=74.125.31.132 DST=Not for you LEN=77 TOS=0x00 PREC=0x00 TTL=41 ID=55750 PROTO=TCP SPT=443 DPT=50412 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
Feb 25 21:31:46 david-desktop kernel: [ 1969.828234] [UFW BLOCK] IN=ppp1 OUT= MAC= SRC=74.125.31.132 DST=Not for you LEN=77 TOS=0x00 PREC=0x00 TTL=41 ID=55750 PROTO=TCP SPT=443 DPT=50412 WINDOW=1002 RES=0x00 ACK PSH URGP=0 

```I chaned my IP to not for you but the other is from google.

This one is from netname:        CANONICAL-CORE
descr:          Canonical Ltd
country:        GB

```
Feb 25 21:25:16 david-desktop kernel: [ 1580.745741] [UFW BLOCK] IN=ppp1 OUT= MAC= SRC=91.189.94.12 DST=Not for you LEN=660 TOS=0x00 PREC=0x00 TTL=47 ID=49484 DF PROTO=TCP SPT=80 DPT=44391 WINDOW=530 RES=0x00 ACK PSH URGP=0 
Feb 25 21:25:16 david-desktop kernel: [ 1580.749966] [UFW BLOCK] IN=ppp1 OUT= MAC= SRC=91.189.94.12 DST=Not for you LEN=754 TOS=0x00 PREC=0x00 TTL=47 ID=49257 DF PROTO=TCP SPT=80 DPT=44395 WINDOW=528 RES=0x00 ACK PSH URGP=0 
Feb 25 21:26:20 david-desktop kernel: [ 1644.314751] [UFW BLOCK] IN=ppp1 OUT= MAC= SRC=91.189.94.12 DST=Not for you LEN=660 TOS=0x00 PREC=0x00 TTL=47 ID=49485 DF PROTO=TCP SPT=80 DPT=44391 WINDOW=530 RES=0x00 ACK PSH URGP=0 
Feb 25 21:26:20 david-desktop kernel: [ 1644.318170] [UFW BLOCK] IN=ppp1 OUT= MAC= SRC=91.189.94.12 DST=Not for you LEN=754 TOS=0x00 PREC=0x00 TTL=47 ID=49258 DF PROTO=TCP SPT=80 DPT=44395 WINDOW=528 RES=0x00 ACK PSH URGP=0 
```I heard that there is a lot of international hacking going on these last 10 days and that Microsoft has been hacked as well. 

Did you noticed anything strange?

BTW. I am in Taiwan

---

### Post by Soul-Sing on 2013-02-25
> I heard that there is a lot of international hacking going on these last 10 days and that Microsoft has been hacked as well. 

Could you please give us the source of your information?

Mind, ip adresses in your logs are not likely, and a priori, "attacks" on your system. Canon. and google/facebook ip-adresses are very common. I am not going into politics regarding international hacking. Because I dislike politic discussions, and I have no access to verify the information. And this could very easy going politic.

---

### Post by Ms. Daisy on 2013-02-25
Microsoft had a few developers' computers in the Mac business group cracked.

[http://mobile.reuters.com/article/idUSBRE91L19A20130223?irpc=932](http://mobile.reuters.com/article/idUSBRE91L19A20130223?irpc=932)

That's got nothing to do with your home PCs.

There are always sites getting hacked. I haven't seen anything unusual in the last 10 days, aside from the fact that more companies happen to be openly talking about it right now.

What DNS service do you use? Your ISP's?

---

### Post by davidvandoren on 2013-02-26
> **Ms. Daisy said:**
> Microsoft had a few developers' computers in the Mac business group cracked.

[http://mobile.reuters.com/article/idUSBRE91L19A20130223?irpc=932](http://mobile.reuters.com/article/idUSBRE91L19A20130223?irpc=932)

That's got nothing to do with your home PCs.

There are always sites getting hacked. I haven't seen anything unusual in the last 10 days, aside from the fact that more companies happen to be openly talking about it right now.

**What DNS service do you use? Your ISP's?**

As it turns out, the Service provider here in Taiwan had a major fire in their data centre causing people to have problems all over the island. 
I couldn't access ubuntu forum after starting this thread and went to a forum here in Taiwan to ask what was going on. 
Everyone was reporting the same issues.

By the way, why is my firewall blocking google and why does it say windows when googles DCs all use Linux machines? I'm just curious.

---

### Post by haqking on 2013-02-26
> **davidvandoren said:**
> As it turns out, the Service provider here in Taiwan had a major fire in their data centre causing people to have problems all over the island. 
I couldn't access ubuntu forum after starting this thread and went to a forum here in Taiwan to ask what was going on. 
Everyone was reporting the same issues.

By the way, why is my firewall blocking google and why does it say windows when googles DCs all use Linux machines? I'm just curious.

Are you referring to the "window" in your logs ?

That doesnt mean windows as in MS, it is the buffer in TCP (TCP Window) which temporarily holds data.

---


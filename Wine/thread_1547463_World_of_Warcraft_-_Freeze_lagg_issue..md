---
title: "World of Warcraft - Freeze lagg issue."
date: 2010-08-06
forum: Wine
---

### Post by Nocturnal.kaldorei on 2010-08-06
_**Hello there! **_

To start with; I'm sorry if this is the wrong place to post this, but it's the Gaming-"zone" for threads. So I'll try here.

I'll try to get all the information I can about my computer and everything involved and related to my issue. 

**Information about my computer and my connection:** 

To begin with; I just installed the newest version of Ubuntu, 10,04. and I run WoW through the newest version of Wine.

I had no problem with installing and updating WoW, and neither with the expansion sets. 
[B]
My Internet connection is based upon a bridged connection[/B] from another computer. 
(My computer is connected to a router, that router is connected to a  computer that got an wireless connection to another router with an  Internet connection in it.) 


**And now to my issue:** 

I got no problems with login in or playing whatsoever but every  10-20 minutes I get a "Freeze-lag" and I can't cast spells and neither  attack, but I can still run around with my char. 

This freeze-lag **sometimes** gets me disconnected but not all times. And the freeze is around 1-4 minutes every 10-20 minutes. 

**What I've tried to fix the problem:** 


[LIST]
[*]          I've tried change the graphic settings to openGL
[*]          Lowest / highest graphic detail
[*]          Windowmode / Full screenmode
[*]
[LIST]
[*]Disabling firewall
[/LIST]
 
[*]
[LIST]
[*]Deleting WTF, Cache and WDB folders. (Who would have guessed?)
[/LIST]
 
[*]
[LIST]
[*]Portforwarding
[/LIST]
 
[*]
[LIST]
[*]Reinstall OS + WoW
[/LIST]
 
[*]
[LIST]
[*]Repairtool
[/LIST]
 
[*]
[LIST]
[*]And changed all related settings.
[/LIST]
 
[/LIST]

---

### Post by Octagonal on 2010-08-06
Just wanted to suggest that you disable all your addons (you've probably already done this but just wanted to offer it up) if you're using any.
I play in 10.04 without issue--but auctioneer did cause me lag issues, although different from how you're describing.

---

### Post by Nocturnal.kaldorei on 2010-08-06
I got no addons at all, and I've never had any.

Thanks for the quick reply.

---

### Post by Octagonal on 2010-08-06
you could do something simple like open up a terminal window and ping a website
> ping [www.yahoo.com](www.yahoo.com) > pings.txt
to pipe pings to a text file.  Ping it for like 30 min and see if there are any problems with connectivity for a long period of time to at least try to rule out your internet connection as the potential cause of the problem...

---

### Post by _h_ on 2010-08-06
What server are you playing on? Do you know the website address or the server IP address?

---

### Post by Nocturnal.kaldorei on 2010-08-06
Thanks, I will try that out [Octagonal]("http://ubuntuforums.org/member.php?u=390569")

---

### Post by Nocturnal.kaldorei on 2010-08-06
> **_h_ said:**
> What server are you playing on? Do you know the website address or the server IP address?

It's blizzards' official realm I play on, I don't know the IPs there. But I'm sure it's able to look it up.

---

### Post by _h_ on 2010-08-06
> **Nocturnal.kaldorei said:**
> It's blizzards' official realm I play on, I don't know the IPs there. But I'm sure it's able to look it up.

What's the name of the realm? I can lookup on wowwiki for you.

---

### Post by Nocturnal.kaldorei on 2010-08-06
> **_h_ said:**
> What's the name of the realm? I can lookup on wowwiki for you.

It's the realm Argent Dawn RP (EU)

Thanks.

---

### Post by _h_ on 2010-08-06
> **Nocturnal.kaldorei said:**
> It's the realm Argent Dawn RP (EU)

Thanks.

Ok. Open terminal and do this command:

```
traceroute 80.239.179.95 > trace.txt
```

If it says you don't have traceroute:

```
sudo apt-get install traceroute
```

Then open the trace.txt, copy paste the output here with CODE tags.

---

### Post by Nocturnal.kaldorei on 2010-08-06
traceroute to 80.239.179.95 (80.239.179.95), 30 hops max, 60 byte packets
 1  192.168.10.1 (192.168.10.1)  1.650 ms  2.611 ms  25.588 ms
 2  gw2-no55.tbcn.telia.com (81.231.237.1)  27.566 ms  27.564 ms  33.527 ms
 3  kbn-b3-link.telia.net (80.91.253.80)  34.511 ms kbn-b3.telia.net (80.91.253.70)  35.494 ms kbn-b3-link.telia.net (80.91.253.80)  36.479 ms
 4  kbn-bb2-link.telia.net (80.91.249.50)  37.464 ms  37.454 ms kbn-bb2-link.telia.net (80.91.247.112)  40.428 ms
 5  hbg-bb2-link.telia.net (80.91.254.2)  44.411 ms hbg-bb1-link.telia.net (80.91.249.205)  44.407 ms hbg-bb2-link.telia.net (80.91.254.2)  55.375 ms
 6  ffm-bb1-link.telia.net (80.91.248.24)  136.311 ms ffm-bb2-link.telia.net (80.91.248.85)  66.882 ms ffm-bb1-link.telia.net (213.248.64.42)  101.809 ms
 7  prs-bb1-link.telia.net (80.91.247.231)  54.811 ms prs-bb2-link.telia.net (80.91.246.185)  54.819 ms prs-bb2-link.telia.net (80.91.246.183)  56.778 ms
 8  prs-b1-link.telia.net (80.91.247.57)  59.757 ms  59.755 ms prs-b1-link.telia.net (80.91.250.249)  60.732 ms
 9  prs-tc-i1-link-telia.net (80.91.250.30)  60.727 ms  63.693 ms  61.687 ms
10  80-239-174-106.customer.teliacarrier.com (80.239.174.106)  71.653 ms !X * *

---

### Post by _h_ on 2010-08-06
> **Nocturnal.kaldorei said:**
> traceroute to 80.239.179.95 (80.239.179.95), 30 hops max, 60 byte packets
 1  192.168.10.1 (192.168.10.1)  1.650 ms  2.611 ms  25.588 ms
 2  gw2-no55.tbcn.telia.com (81.231.237.1)  27.566 ms  27.564 ms  33.527 ms
 3  kbn-b3-link.telia.net (80.91.253.80)  34.511 ms kbn-b3.telia.net (80.91.253.70)  35.494 ms kbn-b3-link.telia.net (80.91.253.80)  36.479 ms
 4  kbn-bb2-link.telia.net (80.91.249.50)  37.464 ms  37.454 ms kbn-bb2-link.telia.net (80.91.247.112)  40.428 ms
 5  hbg-bb2-link.telia.net (80.91.254.2)  44.411 ms hbg-bb1-link.telia.net (80.91.249.205)  44.407 ms hbg-bb2-link.telia.net (80.91.254.2)  55.375 ms
 6  ffm-bb1-link.telia.net (80.91.248.24)  136.311 ms ffm-bb2-link.telia.net (80.91.248.85)  66.882 ms ffm-bb1-link.telia.net (213.248.64.42)  101.809 ms
 7  prs-bb1-link.telia.net (80.91.247.231)  54.811 ms prs-bb2-link.telia.net (80.91.246.185)  54.819 ms prs-bb2-link.telia.net (80.91.246.183)  56.778 ms
 8  prs-b1-link.telia.net (80.91.247.57)  59.757 ms  59.755 ms prs-b1-link.telia.net (80.91.250.249)  60.732 ms
 9  prs-tc-i1-link-telia.net (80.91.250.30)  60.727 ms  63.693 ms  61.687 ms
10  80-239-174-106.customer.teliacarrier.com (80.239.174.106)  71.653 ms !X * *

Everything looks normal except for hop #6 where it jumps to over 100ms ping and goes back to normal on #7. I'm thinking maybe that specific server could be having problems.

---

### Post by Nocturnal.kaldorei on 2010-08-06
> **_h_ said:**
> Everything looks normal except for hop #6 where it jumps to over 100ms ping and goes back to normal on #7. I'm thinking maybe that specific server could be having problems.

Is that the ISP's server or the Blizzards'?

---

### Post by _h_ on 2010-08-06
> **Nocturnal.kaldorei said:**
> Is that the ISP's server of the Blizzards?

The servers that your network routes through, it should be a constant steady pings and not have any spikes like #6.

---

### Post by Nocturnal.kaldorei on 2010-08-06
Is it able to fix?

---

### Post by _h_ on 2010-08-06
> **Nocturnal.kaldorei said:**
> Is it able to fix?

Well if it is a routing issue, and not directly your ISP, then there's really nothing you can do but wait until it gets fixed.

Just curious too, have you attempted to connect on different realms and get the same issue?

---

### Post by Nocturnal.kaldorei on 2010-08-06
> **_h_ said:**
> Well if it is a routing issue, and not directly your ISP, then there's really nothing you can do but wait until it gets fixed.

Just curious too, have you attempted to connect on different realms and get the same issue?

I've not tried that, tho the other computers on the same network does not have an problem with playing on the realm.

But I'll try on another server.

---

### Post by Nocturnal.kaldorei on 2010-08-06
> **Nocturnal.kaldorei said:**
> I've not tried that, tho the other computers on the same network does not have an problem with playing on the realm.

But I'll try on another server.


I've been playing on the realm "Sylvanas PvP EU" for some time now and there's no problem at all it seems

---

### Post by Iowan on 2010-08-06
Moved to Wine.

---

### Post by NeverHide on 2010-08-10
2 days ago and also today i noticed an unjustified high latency in wow....after some searching i found this thread and i tried the traceroute command for my realm's ip(twilight's hammer,also found it on wowwiki)...
saved the results in a txt and this is what i got

```


traceroute to 80.239.179.19 (80.239.179.19), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1.637 ms  2.115 ms  2.426 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *


```

That is about the latency in ms that i get ingame...
any idea what that means?

---


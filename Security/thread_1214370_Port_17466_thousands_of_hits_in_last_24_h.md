---
title: "Port 17466: thousands of hits in last 24 h"
date: 2009-07-15
forum: Security
---

### Post by DrJohn999 on 2009-07-15
My 8.04 LTS server, running Shorewall, logged over 10x the usual number of dropped packets yesterday, all directed at 17466 both tcp and udp, total number of dropped packets = 2384. Maybe that's not a lot in some places but here it's a new record.

These came from all sorts of source IP addresses ranging from 28.58.86.134 up to 222.228.125.206 with little or no apparent grouping. Source ports are variable. Timestamps from Jul 14 21:56:07 to Jul 15 04:30:39 

Anyone else see this? I'm curious about this sudden change in firewall bashing patterns / quantity.

-- Dr J.

---

### Post by aesis05401 on 2009-07-15
I'm not seeing this activity in my netblock, but I checked the IANA reg and there isn't anything official assigned to that port number.  

Probably somone has an exploit in the wild listening on that port and they are scanning your netblock for zombies.

I should mention I get constant scanning of the sort you mention, just not that port recently.

---

### Post by The Cog on 2009-07-16
My advice is to stop logging dropped packets. Dropped packets can't harm you - they've been dropped. The ones that harm you are the ones that get through, and of course they don't get logged.

---

### Post by bodhi.zazen on 2009-07-16
> **The Cog said:**
> My advice is to stop logging dropped packets. Dropped packets can't harm you - they've been dropped. The ones that harm you are the ones that get through, and of course they don't get logged.

The internet is a scary place. Nothing like reading the logs to encourage a bit of security. Try opening port 22 :lolflag:

That level of traffic is nothing to be concerned with, IMO, and the packets were dropped.

---


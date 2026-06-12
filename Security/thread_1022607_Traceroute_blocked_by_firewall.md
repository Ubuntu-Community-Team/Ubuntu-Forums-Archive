---
title: "Traceroute blocked by firewall"
date: 2008-12-27
forum: Security
---

### Post by BenFischer on 2008-12-27
Hi, I've been trying to use traceroute, but my firewall has been blocking the packets.  I use firestarter to manage the wall. When I turn off ICMP filtering most of the routers give me responses, but a few still give ***. Those are my ISP's routers, I know because when I turn my firewall off I get total responses.  Is there some way to enable traceroute returns without giving blank check unfiltered ICMP packets, and does anyone know why does my wall has to be completely off to get some of the responses?
Thanks, Ben

---

### Post by Kinstonian on 2008-12-27
Here is part of what the manual for traceroute says.

> 
-I

Use ICMP ECHO for probes

-T

Use TCP SYN for probes

-U

Use UDP datagrams for probes (**it is default**). Only UDP method is allowed for unprivileged users.

UDP is the default, so try ICMP or TCP.  Keep in mind, the responses you get back are ICMP.  Try turning on firewall logging so you can debug the rules better.  Is it the outbound traffic that is getting filtered, or is it the ICMP response?  Also, a lot of times the traceroute traffic will get filtered a long the way.  Changing between UDP, ICMP, and TCP might fix that.

---

### Post by The Cog on 2008-12-27
I know that the two ICMP packet types that you need to receive are **echo reply** (for the response for the final destination) but mainly, for the intermediate hops, you need to be able to receive **TTL Exceeded** packets. 

But I didn't think Ubuntu shipped with traceroute. And I'm not sure that Windows traceroute doesn't use other packets than ICMP. On Ubuntu, I like to use **mtr** which I know uses ICMP.

---

### Post by cariboo on 2008-12-27
FYI System-->Administration-->Network Tools-->Traceroute. I'm not sure if the network tools versions is the tool to use, as I have found several bugs, that have been pushed upstream. You are probably better off installing the command line package and using that instead.

Jim

---

### Post by The Cog on 2008-12-28
Ah, right. That GUI uses tracepath, not traceroute. And tracepath sends UDP packets, not ICMP pings.

---

### Post by dcstar on 2010-05-27
> **The Cog said:**
> Ah, right. That GUI uses tracepath, not traceroute. And tracepath sends UDP packets, not ICMP pings.

And tracepath also defaults to massive packet sizes that may not get past your networking equipment (mine cannot pass them).

I have put in a bug as this means that the GUI "Traceroute" can be useless for a lot of people.

---


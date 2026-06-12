---
title: "Need to mark outgoing tftp packets with port 69 with iptables"
date: 2008-07-03
forum: Server Platforms
---

### Post by rosscarroll on 2008-07-03
Hi All,

I'm a bit of a n00b with Ubuntu, so try to be gentle with me. Let me explain the situation i'm in.

We need to set up a tftp server to upgrade firmware in phones. The phones will be sitting behind a router we make which only accepts tftp traffic on port 69. The only tftp server we could get working on our Ubuntu server accepts traffic on port 69, but sends it out to a random port. We'd like to take all those outgoing packets and use 69 as the source port. Indeed, we have an XP box with a free tftp server doing this now, but we want the extra security that ubuntu would bring.

We thought the iptables command would be the way to go. So far, we've come up with this:

sudo iptables -t nat -A POSTROUTING -p udp -o eth0 -j SNAT --to-source 195.7.32.124:69

Now, we thought that would make all udp packets have a source port of 69, but it didn't. In fact, it stopped the phone updating behind our control router (which it did work from previously) and didn't make it start updating through our own router. 

Is there a step we're missing? Should we be marking the packets in one rule, and changing them in another like [this says]("http://www.clintoneast.com/articles/multihomed.php")
Or should we be going about it entirely differently?

Any advice gratefully received!!

---


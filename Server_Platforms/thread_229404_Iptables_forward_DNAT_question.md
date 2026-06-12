---
title: "Iptables forward DNAT question"
date: 2006-08-04
forum: Server Platforms
---

### Post by djvishnu on 2006-08-04
I'm having some trouble following a howto i found on the net, this is what i want to do:

(the ip of the box is 10.0.0.2)

Send packets from 10.0.0.88 with destination *:80 to 10.0.0.2:3128

I want to redirect everything incoming on port from 10.0.0.88 to the squid i run on port 3128

The commands from the howto uses the chain PREROUTING, which my iptables complains about.

any tips?

---


---
title: "[SOLVED] virtualbox puel working fine, but how to enable network?"
date: 2008-04-03
forum: Virtualisation
---

### Post by larsdk on 2008-04-03
Hi,

I have installed Windows on a virtual box and that works like a charm. However, I would now like to enable networking in Windows, but I know next to nothing about networking, so I can't really figure out the different options I have in Virtualbox's settings.

Oh, and another question. Is Windows, being the guest of Linux, protected by the security in Linux (does the default iptables settings work in windows for instance?)

Lars

---

### Post by foresto on 2008-04-05
If I remember correctly, VirtualBox will by default allow your guest OS to use the network via NAT.  This is in some ways more secure than iptables, because no incoming connections will be allowed at all.  Outgoing connections, like web browsing, should work.

If you want more advanced networking setups for your guest, you'll have to do some reading. VirtualBox didn't make it easy last time I checked.

---

### Post by larsdk on 2008-04-07
Now I got the default NAT setting to work I must have done something wrong when I tried it the first time - thanks :)

---


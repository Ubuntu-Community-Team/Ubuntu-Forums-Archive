---
title: "Samba and Shields Up"
date: 2007-01-13
forum: Server Platforms
---

### Post by tweedledee on 2007-01-13
I just ran a Shields Up! scan on my computer, and noticed something odd: I am running Samba, but the ports used by Samba, plus a couple of others, showed up as stealthed (specifically 135-139, and 445; I thought only 137-139 and 445 were used by Samba).  All others showed up as closed.  While this is reassuring, in the sense that my local network works and the ports obviously aren't open to the broader internet, I want to make sure this is a real result and not an artifact.

Specifically, I'm concerned because the computer I'm testing this on is behind a hardware firewall/NAT router.  I enabled port forwarding on all ports on the computer to test this, and if I manually open other ports they show up as open; only the Samba ones show the stealthing.  In normal life, I of course keep my hardware firewall in place and so don't really care, but my concern is for my laptop, which I also need to use as a Samba server sometimes but travel with, and I can't always rely on a hardware firewall for it.

So my question is this: does Ubuntu/Samba somehow recognize that the port probe was coming from something other than my local network and not respond, or is this an artifact of my router and so I need to be concerned for my laptop?  Right now I am not running any firewall on my computers; I'd much rather not have to, as Guarddog is overkill for my needs, I don't have the time to learn IPtables, and Firestarter is pain because I use multiple network interfaces.  (Yes, I know there are ways around that if you use network manager, but for some reason network manager and my laptop don't get along.)

Any clarifications would be greatly appreciated.

---

### Post by tweedledee on 2007-01-20
A little more investigation revealed the answer: my ISP (Comcast) is blocking the ports (135-139 & 445).  Oh, welll - for a while I thought Samba had very intelligent behavior built-in!  Now I have to resort to the IP tables/firewall solution to block these ports on my laptop from general access.

---

### Post by genesis[OFT] on 2007-01-20
Also, a word of warning - the GRC ShieldsUp! test isn't a very good indicator at your Network's\System's security setup - it leaves a LOT of things out.  Things like SSH exploits, Buffer overflows and what not, are not checked - and this is where most setups come unstuck.  Keep your kernel updated, and ONLY the ports that you NEED open, open, then you'll be fine. :)

---


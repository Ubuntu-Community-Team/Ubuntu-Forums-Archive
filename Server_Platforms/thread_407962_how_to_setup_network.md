---
title: "how to setup network?"
date: 2007-04-12
forum: Server Platforms
---

### Post by 95aspire on 2007-04-12
just wondering, im debating on having my ubuntu machine act as the dhcp server. meaning, put my linux machine after the modem but before the router, then go from there

but is this safe and whatnot. should i leave it the same as it is now with all comps behind the router?

---

### Post by kidders on 2007-04-13
Hi there,

Using your Ubuntu as a DHCP server is perfectly *safe*, but whether you actually want to do it is a question only you can answer. :-)

Proper implementations of DHCP (ie those *not* built into routers/modems/etc.) are _far_ less likely to have bugs, and tend to be much more flexible. Whether these things matter to you will, I suppose, dictate your decision.

---

### Post by 95aspire on 2007-04-13
ok, this is just somthing im looking at trying out sometime for the experience. right now im fine with how its setup, but just wondering what other options there are.

---

### Post by kidders on 2007-04-13
Ah, I see. Setting up a full implementation of DHCP has its advantages, and is quite easy to do. If I were you, I would consider trying it out the next time you find yourself doing something that would benefit from having a good DHCP service. Examples might include...

[LIST]
[*]Netbooting.
[*]Using apps that are happier dealing with static IPs (eg iptables).
[*]OS-specific (or client-specific) network configuration.
[*]Local DNS.
[*]Running a Samba-based Windows domain.
[*]Etc, etc...[/LIST]

---


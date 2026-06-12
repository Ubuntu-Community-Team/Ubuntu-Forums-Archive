---
title: "Viability of using a single server as a router and file server"
date: 2009-12-29
forum: Server Platforms
---

### Post by CharlesA on 2009-12-29
Is it really viable to set up a server to deal with routing, samba, dns, dhcp, ssh, and whatnot?

From a security standpoint it sounds pretty stupid, but I guess with a good IDS and strong passwords and locked down firewall it would be possible.

Opinions?

---

### Post by mhanson on 2009-12-30
You can certainly do it. However if by routing you mean that it will be the machine that is your gateway to the internet then I personally would not do that. I would use one maching for the router and another for everything else. Like you asked for.. thats my opinion. Im sure you can do it securely. But why increase your risk and complexity unless you have to? Build a proper router and give youreself the peace of mind.

---

### Post by CharlesA on 2009-12-30
I pretty much figured as much. Thanks!

---

### Post by volkswagner on 2009-12-30
Hmn,

I certainly don't want to hijack....but isn't the above services all part of ClarkConnect?

I am glad to read this as it has just brought my attention to the changes made at ClarkConnect, now ClearOS.

I have always wanted to play with the system, but never got around to install it.  The idea just seems really cool.

So, can anyone comment on the existence of ClarkConnect, when so many folks go to the school "keep routing/firewall separate"?

---

### Post by CharlesA on 2009-12-30
I've not used it, but I guess it would works well for a gateway. There is also ebox.

Maybe throw it in a VM and check it out?

The main thing I was wondering was if it would be a security risk to have a file server act as a gateway. It does seem like it would be better just to have 1 machine doing routing/firewall/ids and another acting as a file server.

---

### Post by mhanson on 2009-12-31
Sonce someone brought up a specific solution, Ill add to it:

Monowall: I use in at home on a Soekris box and at work too for NAT and firewall/routing. Its very stable and fairly simple to use. Runs off a CF card too. Nice.

Smoothwall: uesed it for our LUG as a router/firewall. On a old PC with 3 NICs. It was also a pleasure to work with.

PF-Sense: never used it but heard many good things.

Vyatta: never used it.

Astaro: never used it.

Cheers

---


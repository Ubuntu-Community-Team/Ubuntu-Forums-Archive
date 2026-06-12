---
title: "Specifying network adapter"
date: 2010-03-31
forum: Server Platforms
---

### Post by Heinrisch on 2010-03-31
I have two network adapters named eth0 and eth1.

Say that I have two programs, A and B. Is it possible to make A only use eth0 and B only used eth1?

---

### Post by realzippy on 2010-03-31
Generally,yes.
Depends on A and B.
Will you tell us whats A and B?

---

### Post by Heinrisch on 2010-03-31
> **realzippy said:**
> Generally,yes.
Depends on A and B.
Will you tell us whats A and B?

A is rtorrent and B is everything else basically.

---

### Post by iissmart on 2010-03-31
Usually there is a setting in the config file (per application) which can specify what interface it should use. However, even if you do specify what interface rtorrent uses, that doesn't mean *everything else* will use the second interface. I'm also interested on how one could do this.

---

### Post by Heinrisch on 2010-03-31
> **iissmart said:**
> Usually there is a setting in the config file (per application) which can specify what interface it should use. However, even if you do specify what interface rtorrent uses, that doesn't mean *everything else* will use the second interface. I'm also interested on how one could do this.

Well the important thing for me is that rtorrent uses a specified interface. The other programs can really do what they want :P

---

### Post by iissmart on 2010-03-31
This looks easy. Run **rtorrent -h**, and take a look at the **-b** and **-i** switches. Using some combination of those (probably just -b then the IP that is on the interface you want it to use) when you run rtorrent should make it work how you expect, assuming your routing is set up properly. If it's not, I can probably help you with that as well :)

I'm still curious as to whether it's possible to have *all other* traffic go to a specific interface, if anyone else knows (assuming you're getting two IPs on the same subnet).

---


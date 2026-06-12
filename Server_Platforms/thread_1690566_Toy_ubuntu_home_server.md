---
title: "Toy ubuntu home server"
date: 2011-02-18
forum: Server Platforms
---

### Post by nayrb on 2011-02-18
I am not entirely sure if this is the appropriate place for this, and perhaps someone can point me to somewhere else if it isn't.

As a hobby, I want to try and set up a old cheap computer with ubuntu and run it as a home server to toy around with. Any suggestions on how to get started? (Where to get an old computer? Craigslist? What specs should I be looking out for? Wireless vs. ethernet? What software to use? ssh?)

---

### Post by arrrghhh on 2011-02-18
> **nayrb said:**
> I am not entirely sure if this is the appropriate place for this, and perhaps someone can point me to somewhere else if it isn't.

As a hobby, I want to try and set up a old cheap computer with ubuntu and run it as a home server to toy around with. Any suggestions on how to get started? (Where to get an old computer? Craigslist? What specs should I be looking out for? Wireless vs. ethernet? What software to use? ssh?)

Well, what do you want to do?  Do you want to use it as a router?  Do you want it to be a file server?  Run a website?

If you truly are just getting it to play with, flea markets or craiglist is probably a fairly good place to look for real cheap hardware.

I'd say don't go older than a P4 tho....

Is wireless a requirement for you?  I'd say *most* servers do not utilize wifi because of security and latency/overall slowness.  You certainly can if you want, but I'd say most run their servers thru a hardline cable.  I do for performance reasons.

I'd grab the 32-bit 10.04 download of the server edition and start plugging away.

Heck, if you have even a modestly powerful desktop/laptop you can run Ubuntu entirely inside of a virtual machine, letting you preview and play with Ubuntu without buying any additional hardware.  Just food for thought, your post was pretty open-ended ;).

---

### Post by volkswagner on 2011-02-18
Locating an old machine should not be difficult. 

Freecycle, Craigslist, your local recycle center, etc.

Things to consider are power consumption if you will be running it 24/7.  You can get much joy from a Pentium 2/3 machine.  The more RAM, the better.  Reason I say Pent2 or Pent3, is they use roughly a third of a Pentium 4.  Also looking for an older laptop with a Pent3 or Mobile processor may be an option.  Perhaps one with a broken screen.

Ask around, friends and family usually have an old box laying around.

You can alway add an inexpensive SATA controller card if you want to load it up with large drives.

Resources:
[Sticky on this forum]("http://ubuntuforums.org/showthread.php?t=1046738"). 
Howtoforge has some [How-to's]("http://www.howtoforge.com/virtual-hosting-with-pureftpd-and-mysql-incl-quota-and-bandwidth-management-on-ubuntu-10.10-maverick-meerkat").

Stick with wired networking... You can set up the unit then move it close to your router with no screen, keyboard and just use ssh to administer it.

---


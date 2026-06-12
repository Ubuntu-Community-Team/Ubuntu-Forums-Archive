---
title: "RT2500 drivers"
date: 2005-09-30
forum: Requests
---

### Post by Nasso on 2005-09-30
Is it possible to make this into a package?
[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

Whould be "super sweet" :)

---

### Post by mlomker on 2005-09-30
It doubt it'd be feasible for it to be handled as a community-supported .deb because it has to be recompiled with each kernel release.  I'm not sure why Ubuntu hasn't put it into the restricted-modules package, though, it looks like the driver is open source.

---

### Post by essexman on 2005-10-04
I have installed the Breezy preview and my RT2500 based edimax 7128g card worked out of the box.  no compliling, no wiki. Just: > System>>Administration>>Networking  Select device ra0>>properties  tick configure, enter WEP and IP settings, OK, then activate.  I had already had a trial run with the Live CD, which worked fine. After installing breezy I was connected to my wireless network and the Internet in under 1 minute.

So I'm very pleased with Breezy.

---

### Post by Nasso on 2005-10-07
omg, that is sweet news! Thanks ubuntu-dev-team! :D

---


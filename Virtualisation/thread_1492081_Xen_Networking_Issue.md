---
title: "Xen Networking Issue"
date: 2010-05-24
forum: Virtualisation
---

### Post by ctimko on 2010-05-24
I have recently setup my server to act as a Xen dom0 and I am having issues getting my networking to work in Jaunty. The dom0 itself has internet, that isn't the issue, but the domU is bridged through and they don't have network for some reason.  The domU has a static IP address for a different subnet than that of the dom0.  I do a tcpdump when I ping the gateway for the domU subnet from the domU, and I see the arp-reply with the gateway's MAC address, however, ping doesn't print the time or anything, and I can't resolve any domains or ping my dom0.  So that said, any thoughts on what is wrong?

---

### Post by ctimko on 2010-05-24
And it is working now that I deleted all the old VM images and started over... Idk why that happened.

---


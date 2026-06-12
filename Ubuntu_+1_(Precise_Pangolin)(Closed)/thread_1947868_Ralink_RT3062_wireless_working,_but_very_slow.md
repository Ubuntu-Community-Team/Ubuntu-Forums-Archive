---
title: "Ralink RT3062 wireless working, but very slow"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ratcheer on 2012-03-27
I wasn't sure whether to post this in Networking and Wireless or Ubuntu +1, but since it is Precise, I figured I should post it here.

I just did a fresh install of the Precise Beta and, *for the first time ever*, my wireless connection is working with the standard kernel driver rt2800pci. In all past versions and installations of Ubuntu, including my old installation of Precise, I have had to install the chipset maker's driver rt3562sta in order to get a working connection.

However, the rt2800pci connection is very slow. With the rt3562sta driver, it connects at 134 mbps, but my current rt2800pci connection says it is 13 mbps.

I wanted to do a clean installation of Precise and keep it as clean as possible. So I hesitate to reinstall the 3rd party driver. However, I would like for it to be able to make a full-speed connection. I wonder if I need updated firmware, or if some settings could be tweaked with the standard driver to get it up to speed?

Tim

---

### Post by ratcheer on 2012-03-27
Ok, after more than four hours, I got no other suggestions, so I installed the driver from Ralink (rt3562sta) and now my wireless connection is at 130 mbps. I wish rt2800pci would work better so I wouldn't always have to mess with this. Sigh.

Tim

---


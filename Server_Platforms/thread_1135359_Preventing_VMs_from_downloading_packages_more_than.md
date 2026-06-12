---
title: "Preventing VMs from downloading packages more than once"
date: 2009-04-24
forum: Server Platforms
---

### Post by theyranos on 2009-04-24
I'm using virsh and kvm to run two Ubunutu guests on an Ubunut host. As I write this, all three machines are in the middle of their dist-upgrade to 9.04. 

This means that many of the packages that've changed from 8.10 to 9.04 are being downloaded three times. This kind of thing seems to come up a lot, and I was wondering whether there was an easy way to make one of the machines cache stuff for the other two, so the 100-odd debs I need every time I dist-upgrade get downloaded once instead of thrice, saving on Ubuntu's bandwidth and my time.

I don't have a clue where I would even start looking for an answer to this. If you respond with something I can google or RTFM and a link, I'll be satisfied.

---

### Post by vfclists on 2009-04-24
Lookup apt-proxy and apt-cacher.

I believe you can also copy /var/apt/cache files from on machine to the other.

/vfclists

---


---
title: "System 76 Repo"
date: 2009-07-16
forum: System76 Support
---

### Post by wrender on 2009-07-16
I get this error when I reload synaptic

> W: GPG error: [http://planet76.com](http://planet76.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 176A5C84ED67C9ED



is this right for the source

> [http://planet76.com/repositories/](http://planet76.com/repositories/)

---

### Post by thomasaaron on 2009-07-16
To fix the GPG key error, please run the following command:

wget -q [http://planet76.com/repositories/system76_dev.pub](http://planet76.com/repositories/system76_dev.pub) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by gila_monster on 2009-07-16
What's the current correct version of the driver for a panp4n under Jaunty?

---

### Post by thomasaaron on 2009-07-17
If you go to...

planet76.com/repositories

...the current version will always be the second link from the bottom.

---


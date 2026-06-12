---
title: "P2P-like Tahoe filesystem offers secure storage in the cloud"
date: 2009-08-04
forum: The Cafe
---

### Post by Jags_FL on 2009-08-04
Tahoe is a secure cloud filesystem that is licensed under the GPL. Its distributed storage model, which resembles peer-to-peer networking, makes it possible to build a shared storage pool using excess drive capacity from multiple computers across the Internet.

When a file is deployed to Tahoe, it is encrypted and split into pieces that are spread out across ten separate nodes. Using a variation of Reed-Solomon error correction, **it can reconstruct a file using only three of the original ten nodes**. This helps to ensure data integrity when some nodes are unavailable. This is a bit similar to how RAID storage works. Tahoe uses a library called zfec that provides an efficient implementation of the error correction code and exposes it through a Python API.

There is a [**simple interactive mockup**]("http://bigasterisk.com/tahoe-playground/") that illustrates visually how Tahoe's distributed storage works.

More at [ARS Technica]("http://arstechnica.com/open-source/news/2009/08/p2p-like-tahoe-filesystem-offers-secure-storage-in-the-cloud.ars")

---

### Post by The Real Dave on 2009-08-04
Sounds like a great idea, considering were moving more and more into cloud computing, that P2P like system will allow for much higher transfer speeds, as anyone who uses torrent technology. And the redundancy aspect to it sounds great, like an online RAID.

---


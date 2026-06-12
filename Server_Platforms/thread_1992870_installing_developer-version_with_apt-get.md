---
title: "installing developer-version with apt-get?"
date: 2012-06-01
forum: Server Platforms
---

### Post by yavuz.maslak on 2012-06-01
I use ubuntu-12.04LTS server.
Naturally when we install a program, apt-get install latest stable.
But I wish to install the latest snapshot version of a tool using apt-get.
How can I do that ?

---

### Post by lykwydchykyn on 2012-06-01
The first method is to find a PPA that has developer snapshots.  I think launchpad has a search tool for that, but I usually just google PPA + whatever the name of the software is.

If there isn't a PPA, my favorite approach is to use apt-src to download the source from the development version of Ubuntu and build it from that.

If that's not an option (because of unavailable dependencies or the source not updated in Ubuntu+1), then you're beyond the scope of what APT can do for you.  You'll probably need to download the source from the developer and compile with something like checkinstall.

---


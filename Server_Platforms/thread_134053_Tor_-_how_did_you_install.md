---
title: "Tor - how did you install?"
date: 2006-02-21
forum: Server Platforms
---

### Post by PeterHarbo on 2006-02-21
I am looking to install tor but according to the tor web page the tor copy in the Ubuntu repositories is old.  If anyone is running tor how did you do install it?

---

### Post by AgenT on 2006-02-21
First make sure you have all the extra repositories enabled. Second, add the backports repository. That should have a new version of tor. See the Backports forum for more details.

---

### Post by j-strap2 on 2006-02-22
PeterHarbo,

You can use the repository at [http://mirror.noreply.org/pub/tor/](http://mirror.noreply.org/pub/tor/) for latest stable and experimental versions of TOR.

Add the these lines to /etc/apt/sources.list:

deb     [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) breezy main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) breezy main
deb [http://mirror.noreply.org/pub/tor/](http://mirror.noreply.org/pub/tor/) experimental-0.1.1.x-breezy main
deb-src [http://mirror.noreply.org/pub/tor/](http://mirror.noreply.org/pub/tor/) experimental-0.1.1.x-breezy main

---


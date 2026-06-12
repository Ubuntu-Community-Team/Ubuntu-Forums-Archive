---
title: "Mixing repositories on server?"
date: 2009-01-27
forum: Server Platforms
---

### Post by wyldfury on 2009-01-27
Hi,

I've go two mail gateways running on Hardy, but I've got a source package I want to install that requires libev. Libev is available in the Intrepid repositories.
Would it be safe to just add the Intrepid - universe repositories to sources.list and install libev or is it a better idea to do the release upgrade to Intrepid?
Did the same upgrade on two laptops and a desktop without any problems, but this is a server that I'd rather not accidentally break things on.

Thanks for any advice.
Guy

---

### Post by netztier on 2009-01-27
> **wyldfury said:**
> 
Would it be safe to just add the Intrepid - universe repositories to sources.list and install libev or is it a better idea to do the release upgrade to Intrepid?


Does that package happen to be available the **hardy-backports**? Might be easier that way - and you have some form of confirmation that it interoperates with hardy.

regards

Marc

---

### Post by wyldfury on 2009-01-27
> **netztier said:**
> Does that packet happen to be available the **hardy-backports**? Might be easier that way - and you have some form of confirmation that it interoperates with hardy.


Unfortunately it isn't. Checked that. So a full release upgrade is less likely to be problematic?
Haven't had an issue with the desktop ones, so I imagine the server upgrade will be just as smooth.

---

### Post by netztier on 2009-01-27
> **wyldfury said:**
> Unfortunately it isn't. Checked that. So a full release upgrade is less likely to be problematic?
Haven't had an issue with the desktop ones, so I imagine the server upgrade will be just as smooth.

Depends on your environment and server software (upgrade) policy. The problem could be this: Intrepid might become end-of-support even before Hardy does. So you if you upgrade to Intrepid, you might have to upgrade sooner than if you stayed with hardy.

Another solution could be apt-pinning: [http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning) and [http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html) , but this might as well stand againgst policies in your environment. If libev doesn't have a lot of dependencies, it might work, but if it starts pulling in a lot of things, you might end up with a difficult-to-maintain release mixup.


regards

Marc

---


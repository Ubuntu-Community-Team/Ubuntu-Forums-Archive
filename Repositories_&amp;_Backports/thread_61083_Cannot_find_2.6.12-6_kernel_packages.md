---
title: "Cannot find 2.6.12-6 kernel packages"
date: 2005-08-30
forum: Repositories &amp; Backports
---

### Post by alloydog on 2005-08-30
OK, I know this is not 100% Ubuntu but...
I have been playing with a Debian/Ubuntu based distribution called [BeatrIX](http://www.watsky.net), which currently installs with the with 2.6.7 kernel.

A few weeks back, I ran Synaptic to ugrade the kernel, which installed 2.6.12-6.  This worked fine.

Today, I did a clean re-installation of Beatrix, and I upgraded the kernel, which turned out to be 2.6.12-7.
Unfortunately, on reboot, neither the mouse or touchpad works.  I have tried it several times, but problem happens every time.
 
I want to use kernel 2.6.12-6, as I know it works on my laptop.  However, I cannot find it again:

The repositories I have looked at show:
 
Warty
2.6.8-3
 
Hoary:
2.6.10-5
2.6.11-1
 
Breezy:
2.6.12-7
 
How can I get the 2.6.12-6 kernel packages (headers & image) again?

---

### Post by ispmarin on 2005-08-30
Try 
apt-cache search linux-headers

---

### Post by alloydog on 2005-08-30
It just gives me the same results as searching with Synaptic, as in the first post.

---

### Post by alloydog on 2005-08-31
I just did search for **linux-headers-2.6.12-6-686** and got :
[http://us.releases.ubuntu.com/ubuntu/indices/override.breezy.main](http://us.releases.ubuntu.com/ubuntu/indices/override.breezy.main)

I put **[http://us.releases.ubuntu.com/ubuntu/](http://us.releases.ubuntu.com/ubuntu/)** into *Synaptic*, and it worked.
The kernel has been updated and the mouse & touchpad still work.
 O:)

---


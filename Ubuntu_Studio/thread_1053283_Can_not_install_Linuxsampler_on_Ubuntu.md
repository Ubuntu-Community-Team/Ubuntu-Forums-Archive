---
title: "Can not install Linuxsampler on Ubuntu"
date: 2009-01-28
forum: Ubuntu Studio
---

### Post by alectheface on 2009-01-28
I have ubuntu, upgraded to ubuntu studio with the liveCD (Which will not boot on my laptop).
I can't get the LinuxSampler to appear in my Synaptic Packet Manager, so I have found the individual files and am attempting to install them, in the right order.
When attempting to install libgig with the debian packet manager (found here) [http://download.linuxsampler.org/packages/debian/libgig_3.1.0-1_i386.deb]("http://download.linuxsampler.org/packages/debian/libgig_3.1.0-1_i386.deb"), I immediately get an "installation failed", the terminal window attached to it is blank.
I have been trying for almost a week now any getting nowhere, can someone please help, I'm new to Linux and this is all rather difficult! :(

Many thanks, Alec

---

### Post by raboofje on 2009-01-29
The instructions at [https://bugs.launchpad.net/ubuntu/+source/linuxsampler/+bug/252330/comments/8](https://bugs.launchpad.net/ubuntu/+source/linuxsampler/+bug/252330/comments/8) are useful.

---

### Post by raboofje on 2009-01-31
> **julian5 said:**
> probably you cannot install your Debian built packages on a Ubuntu machine. But you'll find out by trying. ;-) Usually dpkg will simply complain if you try to install a package which misses certain dependencies.

The link i posted documents using edit-deb-control.sh to `fix' the dependencies. An alternative would be using equivs.

That way (in my case using equivs) the linuxsampler debian package worked fine for me.

You might also want to check out 'specimen': for some reason it seems less popular, but it's very nice, too.

---


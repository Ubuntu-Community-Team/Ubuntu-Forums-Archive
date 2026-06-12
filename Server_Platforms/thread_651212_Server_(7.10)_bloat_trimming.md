---
title: "Server (7.10) bloat trimming"
date: 2007-12-27
forum: Server Platforms
---

### Post by mdog on 2007-12-27
First, I realize the Ubuntu Server Edition 7.10 actually is pretty un-bloated compared to a lot of other things out there (so hold the flames). How ever, I still feel there is room for improvement, 500mb is nice, but 2-300 would be nicer, Maybe even less.

So did somebody already make a script that will take out the "bloat" from a fresh installation, so I don't have to do the work?

Or does somebody have canonical list of packages required for an absolutely minimal Ubuntu Server with networking?

I'm interested in a minimal server, basically a kernel, shell, gnu utils, network utils, basic software like vi, grub, etc. and libs to support the aforementioned. Everything else should be optional and can be installed afterwards.

---

### Post by UbuWu on 2007-12-27
Install only [ubuntu-minimal]("http://packages.ubuntu.com/feisty/metapackages/ubuntu-minimal.html") and then add everything you want.

---

### Post by mdog on 2007-12-27
Thank you! Pretty new to Ubuntu in its current form, so didn't even realize this option existed and any of my searches turned up nothing :)

---

### Post by craigp84 on 2007-12-27
At that point, you're going to be more of an "embedded" distro than a "server" distro.

I'd rather install a few extra tools to make managing the server a bit easier, i.e. packages like sysstat spring to mind.

Horses for courses i guess, not everyone wants to run a mail server or web server, and in some cases it'll make best sense to trim down what gets installed.

To save disk space is rarely a good reason to waste time triming down a distro though.

---

### Post by jtc on 2007-12-27
I guess you could always take a look at Ubuntu JeOS

[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)

---

### Post by koenn on 2007-12-27
A  fully functional debian installation without any additional software (i.e. skip the step 'select and install packages' in the installer) takes about 250 - 300 MB. It has all you need (basic OS tools, a text editor, and apt to install additional software). I never bothered to trim it down any further. 
I suppose an ubuntu-minimal would be about the same. 

Starting from a minimal install and adding what's needed is my preferred way ot setting up a server. After all, if you know what you need, why would you rely on what the packager gueses the 'average server' needs ?

---

### Post by UbuWu on 2007-12-28
> **jtc said:**
> I guess you could always take a look at Ubuntu JeOS

[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)

That is meant for virtual machines only, it misses a lot of hardware support that is not needed on virtual machines.

---


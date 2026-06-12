---
title: "LVM Encryption - massive performance hit?"
date: 2012-07-23
forum: Security
---

### Post by proximac on 2012-07-23
Hello,

I'm fairly new to Ubuntu (and very new to this forum).  I'll try to explain my situation before getting to the question(s).

I have an old server which has been running a pre-historic installation of Fedora Core for at least 5 years, probably longer.  It has SAMBA installed, and has been acting as my fileserver all this time.  The hardware is a 2005 single core PC with 1GB RAM.

I've now decided to get a bit more up to date, and beef up my security at the same time.  I've got a new-ish quad-core machine with 4GB RAM, onto which I've installed Ubuntu desktop via the alternate installer, and encrypted the filesystem using LVM (*not* the home directory encryption).  And again, I'm running SAMBA.  The whole installation went flawlessly - I'm totally impressed. 

Both systems are accessible from my Windows desktop (XP) via SAMBA - so they're acting as fileservers (I used the Ubuntu 'desktop' install as I want some of the desktop functionality too).  

Doing a 'real world' test from my Windows desktop, I discover something disappointing and surprising.  A full compile of one of my projects, from a SAMBA mapped filesystem, which takes 33s on the old server, takes 1m22s on the new one.  That's the second compile - so the files should mostly be in Ubuntu's cache anyway second time around?

Obviously, I realise that an encrypting filesystem adds an overhead and will be a performance hit, but I wasn't expecting it to be that bad.  I also realise that I'm not doing a perfect like-for-like test, and there are numerous other factors that are different between the two systems.  But the new system is far more powerful, has more RAM, and is running a modern version of Ubuntu (12.04 LTS) as opposed to an ancient Fedora Core.

My questions are:

- Should I expect performance on an encrypting filesystem to be that much slower, i.e. a factor of 3 slower, than an unencrypting filesystem?

- On Ubuntu, is the data in the cache encrypted or unencrypted, i.e. has data in the cache already been unencrypted by then?  So if I run the same compile twice, it's not having to do as much decryption second time around, assuming the files on the server are cached?

- Any other ideas what I could look at for improving this?

Thanks, and regards.
proximac

---

### Post by proximac on 2012-07-23
I'm pleased to be able to report that this was a false alarm - the short version is that the encrypting filesystem is not at fault.  In fact, the new server with the encrypting filesystem is actually faster than the old non-encrypting one (to be fair, as I said, it is a much newer machine, with 4 times as many CPU cores and 4 times more RAM).

After several hours of investigation, the problem turned out to be something completely else - a dodgy network connection to the room where the new server is.  Having resolved that, all is working well.  A classic case of jumping to the wrong conclusion about what was causing a problem.

So for anyone else reading this in the future - from my experience, it seems that an LVM encrypted filesystem, on a modern box with plenty of horsepower, can be at least as fast as a non-encrypted filesystem on an older machine.

---

### Post by Hungry Man on 2012-07-23
Makes sense. Encryption on a server might give you 10-15% performance hit for a heavy I/O server, I wouldn't expect much more than that.

Glad you got this resolved.

---


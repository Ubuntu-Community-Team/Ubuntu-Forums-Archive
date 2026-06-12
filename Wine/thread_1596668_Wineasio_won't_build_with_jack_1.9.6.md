---
title: "Wineasio won't build with jack 1.9.6"
date: 2010-10-14
forum: Wine
---

### Post by conjunctivitis on 2010-10-14
Hello,

I'm trying to install wineasio to use with Sibelius 5, but I can't get it to build.  When I execute make, it returns the following error:
pkg-config --exists jack
make: *** [jack] Error 1

I use ardour2 which runs with jackdmp 1.9.6 under qjackctl and it works fine.  Any advice?

Sibelius is installed and appears to run correctly but I get no playback and no audio configuration options...

wine is 1.2.1
ubuntu 10.10 (maverick)
jackd 1.9.6

Thanks

---

### Post by mrcottonmouth on 2010-10-18
Same problem. Had it working in Kubuntu 9.10. I get the same error trying to recompile wineasio.

pkg-config --exists jack
make: *** [jack] Error 1

Wanting FL Studio to work in wine.

---

### Post by defaultstring on 2010-10-26
bump

---


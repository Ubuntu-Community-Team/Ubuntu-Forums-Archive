---
title: "DVD/CD Passthrough VERY slow in XP on Virtualbox"
date: 2014-11-21
forum: Virtualisation
---

### Post by toddk111 on 2014-11-21
I recently did a distro upgrade (not fresh install) from Ubuntu 12.04 to 14.04 and then I updated Virtualbox to 4.3.18-96516 and updated the extensions as well. I've seen other threads about virtualbox running slow on 14.04 but this isn't really my problem. Everything works fine on XP in virtualbox except the DVD/CD passthrough now runs VERY slow. Any suggestions to fix this problem would be appreciated.

Thanks,
Todd

---

### Post by bashiergui on 2014-11-23
There are a few options in virtualbox for presenting a CD to a guest. If passthrough is slow you could try presenting it as an iso.
[https://www.virtualbox.org/manual/ch05.html#storage-cds](https://www.virtualbox.org/manual/ch05.html#storage-cds)

For passthrough specifically, you might find a solution using command line instructions instead of the gui:
[https://www.virtualbox.org/manual/ch08.html#vboxmanage-storageattach](https://www.virtualbox.org/manual/ch08.html#vboxmanage-storageattach)

---


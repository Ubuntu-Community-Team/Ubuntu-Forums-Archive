---
title: "i386 or amd for AMD K6/2 450Mhz"
date: 2008-04-04
forum: Server Platforms
---

### Post by prshah on 2008-04-04
Hello all,

I am setting up (mostly as an experiment, for in-house use) ubuntu server 7.10 on an AMD K6/2 450Mhz/128Mb RAM.

I downloaded the i386 torrent, but I'm getting messages as "info: linux-server not usable on k6" and "linux-generic usable on k6". (Please see attached image). Before this, I got a lot of dependency errors.

I assumed I need the i386 cd image, but now I think I need to use the amd image.

Any suggestions? AMD K6/2 is an old, old socket 7 CPU supposed to be pin compatible with some intel processor (maybe Pentium I MMX?)

I'm targeting a simple LAMP installation.

---

### Post by kerry_s on 2008-04-04
debian makes for a better server, net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

at the package selection, uncheck the desktop and check the server stuff you want.

---

### Post by netlogic on 2008-04-04
> **prshah said:**
> Hello all,

I am setting up (mostly as an experiment, for in-house use) ubuntu server 7.10 on an AMD K6/2 450Mhz/128Mb RAM.

I downloaded the i386 torrent, but I'm getting messages as "info: linux-server not usable on k6" and "linux-generic usable on k6". (Please see attached image). Before this, I got a lot of dependency errors.

I assumed I need the i386 cd image, but now I think I need to use the amd image.

Any suggestions? AMD K6/2 is an old, old socket 7 CPU supposed to be pin compatible with some intel processor (maybe Pentium I MMX?)

I'm targeting a simple LAMP installation.

use i386. that should be fine.:)

---

### Post by r0biwan on 2008-04-05
The AMD iso is strictly for x86-64 processors like AMD's Athlon 64 and Intel's Core 2 platform.

Just stick with linux-generic

The ubuntu-server kernel is compiled with PAE (Physical Address Extension, it basically allows a 32-bit system address more than 4GiB of ram) support.

I don't think AMD included PAE support until the Athlon line.

---

### Post by netlogic on 2008-04-05
> **r0biwan said:**
> The AMD iso is strictly for x86-64 processors like AMD's Athlon 64 and Intel's Core 2 platform.

Just stick with linux-generic

The ubuntu-server kernel is compiled with PAE (Physical Address Extension, it basically allows a 32-bit system address more than 4GiB of ram) support.

I don't think AMD included PAE support until the Athlon line.

k6/2... mid 90s processor.

---


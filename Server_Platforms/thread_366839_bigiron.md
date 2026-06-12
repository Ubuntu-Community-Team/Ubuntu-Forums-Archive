---
title: "bigiron"
date: 2007-02-21
forum: Server Platforms
---

### Post by franjesus on 2007-02-21
I've installed ubuntu on a 8-way machine, with 16 cores (dual core opterons rev E6).

The chosen kernel package has been linux-image-server and all seems to run fine.

However, I was wondering about the -bigiron kernel and where it should be used. Isn't 16 cores considered to be big iron?

What is the difference between both versions? :-k

Why isn't the -bigiron kernel available for the amd64 arch? :-s

---

### Post by Brazen on 2007-02-21
Big iron generally refers to IBM mainframes, so I assume the -bigiron kernel has something to do with mainframes.

edit: hmm, the package documentation says "Supports high end x86 processors" so maybe it will work on your system, but it doesn't give any clue on what constitutes "high-end" or why it is any different than the normal server kernel.  You could try it out with "sudo apt-get install linux-image-server-bigiron" and see if it does anything.

---

### Post by PilotJLR on 2007-02-21
> **franjesus said:**
> I've installed ubuntu on a 8-way machine, with 16 cores (dual core opterons rev E6).

The chosen kernel package has been linux-image-server and all seems to run fine.

However, I was wondering about the -bigiron kernel and where it should be used. Isn't 16 cores considered to be big iron?

What is the difference between both versions? :-k

Why isn't the -bigiron kernel available for the amd64 arch? :-s


Does /proc/cpuinfo show every core correctly?? I was under the impression 8 or more cores required the bigiron kernel.

---

### Post by franjesus on 2007-02-22
> **Brazen said:**
> hmm, the package documentation says "Supports high end x86 processors" so maybe it will work on your system, but it doesn't give any clue on what constitutes "high-end" or why it is any different than the normal server kernel.  You could try it out with "sudo apt-get install linux-image-server-bigiron" and see if it does anything.

I'd like to, but it is not available for amd64, only for i386, so it is not possible to install it unless you do it by hand using dpkg --force-architecture

---

### Post by franjesus on 2007-02-22
> **PilotJLR said:**
> Does /proc/cpuinfo show every core correctly?? I was under the impression 8 or more cores required the bigiron kernel.

Yes, it has 16 processors, from 0 till 15, recognised correctly.

---


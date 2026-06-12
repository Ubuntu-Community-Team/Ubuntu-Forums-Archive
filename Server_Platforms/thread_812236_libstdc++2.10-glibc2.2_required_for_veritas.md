---
title: "libstdc++2.10-glibc2.2 required for veritas"
date: 2008-05-29
forum: Server Platforms
---

### Post by metrognome on 2008-05-29
Hello,

I'm trying to install the Veritas remote backup agent on a new 8.04 server image.  I got it working great in 6.10.  However, the agent has a requirement for the libstdc++2.10-glibc2.2 library which, after some research, apparently isn't included in Hardy.

I know very little about these libraries so I have a couple of questions:

1. Is this library available somewhere?  (I can't get backports to update for me at the moment - maybe it's there?)
2. Is there a newer library that is backwards compatible that I can create a sym-link for?
3. Any other ideas on how to get this working?  So far I see nothing new from Veritas so I think I'm stuck with this one for now.

Appreciate any suggestions.

Thanks in advance,
MetroGnome.

---

### Post by metrognome on 2008-06-05
Well, in absence of any replies I've forged ahead with some experimentation.  I copied the /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so file from my old server to the new image and made a sym-link for it.

The agent appears to start now but I haven't gotten any further than that so I don't know if it's really working yet or not.  I also don't know if installing that lib is going to break anything else.

I'll update as I go in case anyone else is trying to install the Veritas backup agent on Hardy.

---

### Post by Cloud79 on 2008-09-17
> **metrognome said:**
> Well, in absence of any replies I've forged ahead with some experimentation.  I copied the /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so file from my old server to the new image and made a sym-link for it.

The agent appears to start now but I haven't gotten any further than that so I don't know if it's really working yet or not.  I also don't know if installing that lib is going to break anything else.

I'll update as I go in case anyone else is trying to install the Veritas backup agent on Hardy.

I can confirm that this works!
(Had the same problem with HP Dataprotector)

---


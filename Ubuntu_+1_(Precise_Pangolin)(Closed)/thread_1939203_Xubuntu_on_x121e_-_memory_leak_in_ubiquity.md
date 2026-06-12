---
title: "Xubuntu on x121e - memory leak in ubiquity?"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by krimskrams on 2012-03-11
Hi,
I tried to install xubuntu precise 64bit on my Lenovo x121e and can't get it to finish installation:

I tried multiple versions (alpha2, beta1, daily 10032012), booting from an USB stick with either direct installation or try ubuntu -> install and it always ends up with a hung machine ... after entering the user credentials the systems keeps working forver, reacting slower and slower. The reason seems to be that the process ubiquity eats up all memory (after 1 hour > 4GB memory).

Any clues?

krimskrams

---

### Post by kelpdip on 2012-03-11
x120e here. Yes, there is a memory leak, and other ubiquity bugs unrelated to the memory leak. After trying for a couple hours, I decided the live install was unworkable and used the alternate install iso. The installed system isn't too bad, just don't expect too much from beta.

> **krimskrams said:**
> Hi,
I tried to install xubuntu precise 64bit on my Lenovo x121e and can't get it to finish installation:

I tried multiple versions (alpha2, beta1, daily 10032012), booting from an USB stick with either direct installation or try ubuntu -> install and it always ends up with a hung machine ... after entering the user credentials the systems keeps working forver, reacting slower and slower. The reason seems to be that the process ubiquity eats up all memory (after 1 hour > 4GB memory).

Any clues?

krimskrams

---

### Post by krimskrams on 2012-03-15
Hi,
thanks, the alternate install CD worked finally. However I found that I had to set the BIOS to legacy boot instead of UEFI boot. With UEFI boot enabled the step install software always failed with some dependency errors.
Switching to legacy and deleting the GPT table from disk did finally the trick and now 12.04 runs on my x121e.

Unfortunately the support for the builtin rtl8192ce wireless card is still far from optimal (and my hope was that it this support is getting better with kernel 3.2 ...)

Bye,
krimskrams

---


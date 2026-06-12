---
title: "Increasing Ubuntu entropy with /poolsize ?"
date: 2012-04-23
forum: Security
---

### Post by Hungry Man on 2012-04-23
/proc/sys/kernel/random/poolsize

[https://en.wikibooks.org/wiki/Grsecurity/Appendix/Grsecurity_and_PaX_Configuration_Options#Larger_entropy_pools](https://en.wikibooks.org/wiki/Grsecurity/Appendix/Grsecurity_and_PaX_Configuration_Options#Larger_entropy_pools)

> If you say Y here, the entropy pools used for many features of Linux and grsecurity will be doubled in size. Since several grsecurity features use additional randomness, it is recommended that you say Y here. Saying Y here has a similar effect as modifying /proc/sys/kernel/random/poolsize.
What are the differences between these two methods? How large can this be set?

---

### Post by rookcifer on 2012-04-23
> **Hungry Man said:**
> /proc/sys/kernel/random/poolsize

[https://en.wikibooks.org/wiki/Grsecurity/Appendix/Grsecurity_and_PaX_Configuration_Options#Larger_entropy_pools](https://en.wikibooks.org/wiki/Grsecurity/Appendix/Grsecurity_and_PaX_Configuration_Options#Larger_entropy_pools)


What are the differences between these two methods? How large can this be set?

I would imagine it could be set to any arbitrary size, at least if you messed with the source code itself.  Not sure how large it can be set without doing that.

However, I see no purpose in this, even for grsecurity.  Increasing the size of the pool does not suddenly give you "additional randomness."  All it does is make the *potential* randomness pool larger.  But if you don't have much entropy to begin with (and you wont unless you use a hardware RNG), then increasing the pool size does no good.

Of course, they are probably getting their randomness from /dev/urandom and not /dev/random.  If you understand the difference in how those two work, then it makes sense.  But still, the randomness from /dev/urandom, while probably good enough for ASLR, is not of as high of quality as what /dev/random provides.  What I am saying is increasing the pool size of /dev/random does nothing unless you have enough entropy to fill it.  And you wont without a hardware solution.

---

### Post by Hungry Man on 2012-04-23
There are other various software solutions, aren't there? One's that deal with the clock or with sound?

---

### Post by rookcifer on 2012-04-23
> **Hungry Man said:**
> There are other various software solutions, aren't there? One's that deal with the clock or with sound?

Yes.  The quality of them is questionable, but they are probably good enough to mix into the /dev/random pool.

Intel is putting a hardware TRNG on their new Ivy bridge line of processors.  That's a big step forward for crypto, imo.  Hopefully AMD does the same.

---

### Post by Hungry Man on 2012-04-23
Didn't know that about IB. Very good to know, thank you.

---

### Post by Dangertux on 2012-04-23
What was said about entropy is true. Ultimately you don't want to generate more entropy in the sense of more data, but you want it to be more random. If that makes sense.

Also note that poolsize is tied to pages, so without enabling huge pages 4096 would probably be the default (maximum). You could probably change that by recompiling the kernel though.

Hope this helps.

---

### Post by rookcifer on 2012-04-24
> **Hungry Man said:**
> Didn't know that about IB. Very good to know, thank you.

Yes, I am glad they are doing it.  You can read about their design [here.]("http://spectrum.ieee.org/computing/hardware/behind-intels-new-randomnumber-generator/0")

This fact alone will probably cause me to buy an IB processor even though I have been an avid AMD user for years.  AMD has a TRNG on their Geode processors but none on their standard desktop line.  And it doesn't appear they have any TRNG planned for any new processor line this year or next.

---


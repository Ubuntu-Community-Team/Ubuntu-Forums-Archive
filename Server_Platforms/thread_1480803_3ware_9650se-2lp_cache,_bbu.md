---
title: "3ware 9650se-2lp cache, bbu???"
date: 2010-05-11
forum: Server Platforms
---

### Post by tufcamman on 2010-05-11
Hi, quick raid question.

I understand that without a battery backup unit, a hardware raid card wont enable write caching that will be very detrimental to performance.  However, the simple, 2 port 9650se-2lp, which would be perfect for my needs seems to not support a bbu, but also has 128MB cache memory.

How will this work out, does it not have the safeguard of disabling cache memory?  Has anybody had any experience with a striped set of drives with this card?

Thanks for the input.

---

### Post by knnniggett on 2010-05-18
I just purchased and installed a 9650SE-4LPML and can tell you that one can still turn on the write cache w/o a BBU.  It gives you a warning but still lets you turn it on.

While I cannot guarantee it, I would expect the 2LPML to work the same way.

The poor man's BBU...
Note that if you have a UPS (even a cheap one) and it is configured to gracefully shutdown your machine in the event of a power failure then you can be reasonably assured you won't lose data.

Oh, and I'm running RAID 0 with three 250GB drives.  Performance is much faster than the fakeraid 0 I was previously using.

---

### Post by tufcamman on 2010-05-25
I can now verify this.  The 9650se-2lp does allow you to enable cache w/o a bbu.  Of course it gets after you about safety.

I am using two 7200 HD's in raid0 and hdparm gives me approx. 180 MB/s reads.  Not bad at all.

---


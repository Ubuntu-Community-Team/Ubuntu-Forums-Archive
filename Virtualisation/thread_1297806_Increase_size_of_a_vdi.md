---
title: "Increase size of a vdi"
date: 2009-10-22
forum: Virtualisation
---

### Post by longtom on 2009-10-22
Hi,

Is it at all possible to increase the size of a vdi?  I doubt it...

Next one.  What is the most painless way to migrate a virtual OS (Ubuntu) to a bigger vdi.

Please advise.  Any suggestions welcome.

---

### Post by oraerk on 2009-10-22
A VDI capacity is fixed. Once created, a VDI cannot be extended to a greater capacity. The work around is to create a new VDI and use 3rd party disk cloning tool to replicate the content of the initial VDI.

On how to do it, please explore:
[http://forums.virtualbox.org/viewtopic.php?f=1&t=15456#p64620](http://forums.virtualbox.org/viewtopic.php?f=1&t=15456#p64620)
[http://forums.virtualbox.org/viewtopic.php?f=1&t=8580#p70743](http://forums.virtualbox.org/viewtopic.php?f=1&t=8580#p70743)

Did it myself by the following guide [http://forums.virtualbox.org/viewtopic.php?p=65211#p65211](http://forums.virtualbox.org/viewtopic.php?p=65211#p65211) . Worked.

---

### Post by longtom on 2009-10-22
> **oraerk said:**
> A VDI capacity is fixed. Once created, a VDI cannot be extended to a greater capacity. The work around is to create a new VDI and use 3rd party disk cloning tool to replicate the content of the initial VDI.

On how to do it, please explore:
[http://forums.virtualbox.org/viewtopic.php?f=1&t=15456#p64620](http://forums.virtualbox.org/viewtopic.php?f=1&t=15456#p64620)
[http://forums.virtualbox.org/viewtopic.php?f=1&t=8580#p70743](http://forums.virtualbox.org/viewtopic.php?f=1&t=8580#p70743)

Did it myself by the following guide [http://forums.virtualbox.org/viewtopic.php?p=65211#p65211](http://forums.virtualbox.org/viewtopic.php?p=65211#p65211) . Worked.

Thank you.  This appears to be working well - up to the part I need to resize the partition.
I am in gparted, I have a 10GB unpartitioned space but somehow my cloned ext3 doesn't want to extent.

Any ideas?

---

### Post by howefield on 2009-10-22
The above is good advice, another option would be to create a second disk and slave it to the original. Add it as a second drive in your virtual machine settings.

---

### Post by oraerk on 2009-10-22
> **longtom said:**
> Thank you.  This appears to be working well - up to the part I need to resize the partition.
I am in gparted, I have a 10GB unpartitioned space but somehow my cloned ext3 doesn't want to extent.

Any ideas?
My guess you are on the stage of resizing cloned vdi with gparted, right? I had not faced problems on that stage, please post what does gparted say.

---

### Post by longtom on 2009-10-23
> **oraerk said:**
> My guess you are on the stage of resizing cloned vdi with gparted, right? I had not faced problems on that stage, please post what does gparted say.

That's correct.  However, I used a dynamically expanding virtual hdd.  I'll try it as I write with a fixed one.  If that doesn't work I'll post the screen shots and an explanation in detail of what is not working.

Thanks for your response.

---

### Post by longtom on 2009-10-23
Didn't work.  Her it goes:

On screenshot1 you see my virtual hdd with my partitions on it.  I would like to extend hdb1 using the unpartitioned space of 10GB to do so.

When I select hdb1 and press "resize", the following screen pops up and I am not able to resize the partition, as it appears to be at its maximum size...

What am I doing wrong?

---

### Post by longtom on 2009-10-23
Here we are - community did it again.

On the za irc channel somebody gave me some partition basics  I wasn't aware of.

So I deleted all partitions (incl swap) but the cloned ext3 partition.  No I could extend that partition, which was so stubborn, quite nicely.  Left enough space to recreate swap afterwards, did that - Bob's your uncle.

Anything is easy - if you know what to do...

Just wrote above for the benefit of google.  This problem is SOLVED.  Thanks to oraerk for pointing me into the correct direction!

---


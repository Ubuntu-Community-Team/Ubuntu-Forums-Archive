---
title: "Can hard disk drives melt cables?"
date: 2010-09-19
forum: The Cafe
---

### Post by piwacet on 2010-09-19
Hi. I'm setting up a new computer and my current  cable routing has some power cables and IDE cables pressing against the  hard disks. I was wondering if this is safe - can hard disks get hot  enough to melt through the cables and cause a short? I've googled, but  didn't easily find useful information. 
 
Thanks!

---

### Post by CharlesA on 2010-09-19
You should be fine. If a hard drive is hot enough to melt a cable, then you've got bigger problems then just a melted/ruined cable.

---

### Post by Dustin2128 on 2010-09-19
hard disks usually don't get too warm compared to G/CPUs.

---

### Post by Goolie on 2010-09-19
> **piwacet said:**
> Hi. I'm setting up a new computer and my current  cable routing has some power cables and IDE cables pressing against the  hard disks. I was wondering if this is safe - can hard disks get hot  enough to melt through the cables and cause a short? I've googled, but  didn't easily find useful information. 
 
Thanks!

You won't need to worry about melting cables, but messy and disorganized cables *will* effect airflow inside your PC, potentially increasing the temperature of your GPU/CPU which can lead to overheating.  Try to keep any front side fans or vents as clear as possible, even if it means a little adjusting of your cables.  (I've had to buy an extension here and there to get some satisfying organization.  But this is just me being a little sadistic with seeing no wires.

---

### Post by 23meg on 2010-09-19
> **Dustin2128 said:**
> hard disks usually don't get too warm compared to G/CPUs.

That doesn't mean they aren't equally or more prone to failure due to overheating, though. Hard disks have very different manufacturer ratings regarding how hot they can safely operate; both in absolute numbers, and in terms of relative safety (GPUs and CPUs can operate safely in the "does not melt yet" margin, whereas running hard disks close to their maximum safe operating temperature is discouraged).

Relevant reading: 

[http://www.codinghorror.com/blog/2006/12/hard-drive-temperatures-be-afraid.html](http://www.codinghorror.com/blog/2006/12/hard-drive-temperatures-be-afraid.html)

---

### Post by Dustin2128 on 2010-09-19
> **mgunes said:**
> That doesn't mean they aren't equally or more prone to failure due to overheating, though. Hard disks have very different manufacturer ratings regarding how hot they can safely operate; both in absolute numbers, and in terms of relative safety (GPUs and CPUs can operate safely in the "does not melt yet" margin, whereas running hard disks close to their maximum safe operating temperature is discouraged).

Relevant reading: 

[http://www.codinghorror.com/blog/2006/12/hard-drive-temperatures-be-afraid.html](http://www.codinghorror.com/blog/2006/12/hard-drive-temperatures-be-afraid.html)
 Running them at high temperatures is far from advisable, but the OP was worried about cables melting, not hardware overheats.

---

### Post by 23meg on 2010-09-19
> **Dustin2128 said:**
> Running them at high temperatures is far from advisable, but the OP was worried about cables melting, not hardware overheats.

The point is that if the OP is worried about cables melting, they *should* also be worried about hard disk overheating.

---

### Post by Frogs Hair on 2010-09-19
From what can find plastic melts about 200-400 degrees C ,  depending on the type. If you would like view hdd temp. type   sudo hddtemp /dev/sda        into the terminal or open disk utility and select smart data.

---

### Post by blueturtl on 2010-09-19
> **mgunes said:**
> That doesn't mean they aren't equally or more prone to failure due to overheating, though. Hard disks have very different manufacturer ratings regarding how hot they can safely operate; both in absolute numbers, and in terms of relative safety (GPUs and CPUs can operate safely in the "does not melt yet" margin, whereas running hard disks close to their maximum safe operating temperature is discouraged).

Relevant reading: 

[http://www.codinghorror.com/blog/2006/12/hard-drive-temperatures-be-afraid.html](http://www.codinghorror.com/blog/2006/12/hard-drive-temperatures-be-afraid.html)

Google found temperatures did not correlate with hard drive failures. In fact drives running cool seemed slightly more prone to failure than drives running hot.

[Source]("http://labs.google.com/papers/disk_failures.pdf")

...and to the OP, no you can't melt your HDD cables. You'll start noticing other things fail before the cables melt. :)

---

### Post by 23meg on 2010-09-20
> **blueturtl said:**
> Google found temperatures did not correlate with hard drive failures. In fact drives running cool seemed slightly more prone to failure than drives running hot.

[Source]("http://labs.google.com/papers/disk_failures.pdf")

Yes, I had read that; it's linked to from the post I had cited in my first post.

It would be wrong to conclude that "temperatures did not correlate with failures", though; it's just that the correlation is not as strong as was previously estimated. You'll note that the 45 to 50 degree slice, which is the "really hot" rating for most drives, is associated with a significant rise in failures, especially in older drives.

---

### Post by piwacet on 2010-09-20
Thanks everybody.   That will simplify cable routing a lot.

---


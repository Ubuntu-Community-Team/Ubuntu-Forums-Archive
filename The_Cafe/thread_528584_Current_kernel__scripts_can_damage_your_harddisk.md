---
title: "Current kernel / scripts can damage your harddisk"
date: 2007-08-18
forum: The Cafe
---

### Post by jongkind on 2007-08-18
Some posts on this can be found elsewhere,  but I think the subject is important enough to make a summary of it, since it can prevent hardware damage. The point is that the current Ubuntu Kernel (or scripts?) can damage your harddisk. When I power off my laptop I hear a loud click from the hd, in the same way as if I powered it off using the switch. That is what is called emergency parking of heads, and could damage hardware in the long run.

Methods for **diagnoses** are given here (Christian Schlauer said on 2007-07-18 )
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810")

That **emergency parking** really is not good for your harddisk is described here:
[http://www.hitachigst.com/tech/techlib.nsf/techdocs/85CC1FF9F3F11FE187256C4F0052E6B6/$file/80GNSpec2.0.pdf]("http://www.hitachigst.com/tech/techlib.nsf/techdocs/85CC1FF9F3F11FE187256C4F0052E6B6/$file/80GNSpec2.0.pdf")

"Use of emergency unload reduces the start/stop life of the drive at a rate at least 100 times faster than that of normal unload and may damage the drive."

A **workaround** and details are given here (same link as above, but a workaround from Martin Koßler who said on 2007-04-09):
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810")

This problem is not unique for Ubuntu, some Googling will tell you that other distro's have the same issue. This will be fixed in the 2.6.22 kernel.

---

### Post by heimo on 2007-08-18
> **jongkind said:**
> I did not find posts that described this issue.

Here, found by searching:
[http://ubuntuforums.org/showthread.php?t=417047](http://ubuntuforums.org/showthread.php?t=417047)
[http://ubuntuforums.org/showthread.php?t=309185](http://ubuntuforums.org/showthread.php?t=309185)

---

### Post by jongkind on 2007-08-18
> **heimo said:**
> Here, found by searching:
[http://ubuntuforums.org/showthread.php?t=417047](http://ubuntuforums.org/showthread.php?t=417047)
[http://ubuntuforums.org/showthread.php?t=309185](http://ubuntuforums.org/showthread.php?t=309185)

Good, I'll edit my previous post and remove the description, thanks.

---

### Post by heimo on 2007-08-18
> **jongkind said:**
> Good, I'll edit my previous post and remove the description, thanks.

Argh... No no... That was a good post summarizing it. It's a very valid point and serious problem and deserves some attention. You could have kept it as is.

---

### Post by jongkind on 2007-08-18
> **heimo said:**
> Argh... No no... That was a good post summarizing it. It's a very valid point and serious problem and deserves some attention. You could have kept it as is.

Hm, probably you're right. OK, I re-edited the post again with more or less the original text.

---

### Post by maniacmusician on 2007-08-18
hmm, do you just mean the kernel in Feisty? Because Gutsy is already using the 26.22-8 kernel...

---

### Post by bapoumba on 2007-08-18
[http://ubuntuforums.org/showthread.php?t=508576]("http://ubuntuforums.org/showthread.php?t=508576")
There is already a very long thread in the "Hardware & Laptop" section. I'm closing here (not merge) for a redirect :)

Please contribute to the pre-existing thread, thanks.

---


---
title: "Gutsy: where have all the developers gone?"
date: 2007-11-24
forum: The Cafe
---

### Post by vmsda on 2007-11-24
I have recently installed Gutsy, have had mixed experiences, although some people do seem to have basic problems which I have not experienced at all.

But being new to Linux, let me ask: what happens to an Ubuntu version after it is released? No fixes any longer? Where can I find feedback concerning problems eventually corrected after release date?

Judging by much of what I have read, once a particular version is released, it falls - along with its users - into a black hole, from which one can be rescued only by the 'community'. Somehow, this sounds a bit too vague to assure the world at large that Linux can be reckoned as a force in the desktop arena.

---

### Post by 23meg on 2007-11-24
[QUOTE=vmsda]
But being new to Linux, let me ask: what happens to an Ubuntu version after it is released? No fixes any longer? [/QUOTE]

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

[QUOTE=vmsda]Judging by much of what I have read, once a particular version is released, it falls - along with its users - into a black hole, from which one can be rescued only by the 'community'. [/QUOTE]

How did you reach that conclusion?

The "main" component of each regular Ubuntu release is supported for 18 months by Canonical (much longer in long term support releases), and the [components]("http://www.ubuntu.com/community/ubuntustory/components") that aren't supported by Canonical are maintained by the community.

---

### Post by vmsda on 2007-11-24
I did not reach a "conclusion", I voiced a concern. But it would not be difficult to reach a conclusion of sorts, after one reads a whole raft of threads in which some people report problems, others chime in with the same concerns, some more or less expert community members do their best to help ... and nothing happens by way of resolution.

---

### Post by kellemes on 2007-11-24
> **vmsda said:**
> I did not reach a "conclusion", I voiced a concern. But it would not be difficult to reach a conclusion of sorts, after one reads a whole raft of threads in which some people report problems, others chime in with the same concerns, some more or less expert community members do their best to help ... and nothing happens by way of resolution.

Can you give an example?

---

### Post by dips_xe on 2007-11-24
> **kellemes said:**
> Can you give an example?

the majority of threads? :)

---

### Post by kellemes on 2007-11-24
> **dips_xe said:**
> the majority of threads? :)

I can assume you can't?
Most posts don't really report problems with Ubuntu as they do report problems with setting-up or maintaining the system.

Still I'd be interested in an example.

---

### Post by 23meg on 2007-11-24
[QUOTE=vmsda]But it would not be difficult to reach a conclusion of sorts, after one reads a whole raft of threads in which some people report problems, others chime in with the same concerns, some more or less expert community members do their best to help ... and nothing happens by way of resolution.[/QUOTE]

1) Not all problems people are having originate from bugs; the fact that people are having problems isn't proof that there's a bug in the software
2) Not all problems that do originate from bugs get reported as proper bug reports in the bug tracker (not the forums)
3) As described in [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates), not all bugs *can* be fixed in stable releases

If you run into reproducible problems, the thing to do is to [file a bug report]("https://bugs.launchpad.net/ubuntu/+filebug").

---

### Post by boast on 2007-11-24
> **kellemes said:**
> Can you give an example?

[http://ubuntuforums.org/showthread.php?t=585635](http://ubuntuforums.org/showthread.php?t=585635) [Gutsy GNOME login takes a long time]

---

### Post by bruce89 on 2007-11-24
> **boast said:**
> [http://ubuntuforums.org/showthread.php?t=585635](http://ubuntuforums.org/showthread.php?t=585635) [Gutsy GNOME login takes a long time]

Not a bug in the sense that there is no specific program at fault.

---

### Post by boast on 2007-11-24
> **bruce89 said:**
> Not a bug in the sense that there is no specific program at fault.

still confirmed as a bug none the less

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544)

---

### Post by p_quarles on 2007-11-24
Ubuntu's mission is to provide up-to-date software, up-to-date hardware support, and easy setup. Those last two items are almost mutually exclusive. If you want a bug-free system, try Debian Stable. 

In response to the original question, though: No. Developers are still working on Gutsy bugs. Go to Gutsy's launchpad page to see which problems are currently being worked on.

---

### Post by vmsda on 2007-11-25
> **kellemes said:**
> Can you give an example?

You can have a look in Hardware & Laptops, thread "xrandr rotates display but doesn't rescale screen", as a fairly simple but quite illustrative sample.

---

### Post by vmsda on 2007-11-25
Thank you for calling my attention to the StableReleaseUpdates url. May I comment in passing that "... updates will only be issued ... for bugs [causing] security vulnerability ... severe regression ... loss of user data ...". The problem is that people complain that they have lost functionality going from, say, 7.0.4 to 7.10 (I have too) which may not qualify for 'severe regression' but which nonetheless affects hundreds (or even thousands) of users.
The real underlying issue at stake here is credibility, and it is that which must ultimately be addressed, for Ubuntu's and Linux's sake.

---

### Post by bailout on 2007-11-25
I think Ubuntu's policy has always been to only issue security and essential bugs. LTS releases are no different, they just issue security bugs for a longer period after release but the release is no more stable or bug free than any other. Similarly if software has new versions these aren't released for an already released version.

---


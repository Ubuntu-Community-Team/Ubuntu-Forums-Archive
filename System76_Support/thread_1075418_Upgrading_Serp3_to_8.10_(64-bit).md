---
title: "Upgrading Serp3 to 8.10 (64-bit?)"
date: 2009-02-20
forum: System76 Support
---

### Post by Trevor Bramble on 2009-02-20
76ers,

I'm looking into upgrading the Ubuntu 8.04 install on my Serp3 but I have some concerns.

First, under the release notes "[known issues]("http://www.ubuntu.com/getubuntu/releasenotes/810#Other%20known%20issues")" section, there are some items which appear to apply to [this hardware]("http://knowledge76.com/index.php/Serp3").  I realize that document is likely frozen in time and these may or may not still be issues, but I have no other reference.

Second, I'd like to make the switch from 32-bit to 64 in the process.  Is this not a viable upgrade path?  I'm considering replacing the hard disk with a larger one when making the move, both to allow a quick retreat and to facilitate the 32->64 move if it's otherwise not available or inadvisable (which I'd guessing is the case).

Potential Third, if I do upgrade the hard disk, what are the parameters I should stick to?  The SATA controller is version 1, right?  It can handle SATA II drives though, right?  (At the lower bandwidth, of course.)  Is 7200 RPM going to generate too much heat?

Thanks!

---

### Post by thomasaaron on 2009-02-20
> First, under the release notes "known issues" section, there are some items which appear to apply to this hardware. I realize that document is likely frozen in time and these may or may not still be issues, but I have no other reference.

The SerP3 works fine with 8.10. There is a freezing bug that surfaced, but it is an easy fix via: sudo apt-get install linux-backports-modules-intrepid

> Second, I'd like to make the switch from 32-bit to 64 in the process. Is this not a viable upgrade path? I'm considering replacing the hard disk with a larger one when making the move, both to allow a quick retreat and to facilitate the 32->64 move if it's otherwise not available or inadvisable (which I'd guessing is the case).

You can't really go from 32 bit Hardy to 64-bit Intrepid. There is a fan throttling issue after resuming from hibernate in 32-bit (Hardy or Intrepid), so I encourage going to 64-bit, where the problem doesn't exist.


> Potential Third, if I do upgrade the hard disk, what are the parameters I should stick to? The SATA controller is version 1, right? It can handle SATA II drives though, right? (At the lower bandwidth, of course.) Is 7200 RPM going to generate too much heat?

You'll get better battery life out of a 5400 RPM drive if you do a lot of hard-drive intensive stuff. If you're not doing hard-drive intensive tasks, you probably would notice the speed benefit of a 7200 RPM drive at boot up.

---

### Post by Trevor Bramble on 2009-02-20
> **thomasaaron said:**
> The SerP3 works fine with 8.10. There is a freezing bug that surfaced, but it is an easy fix via: sudo apt-get install linux-backports-modules-intrepid

Excellent.

> **thomasaaron said:**
> You can't really go from 32 bit Hardy to 64-bit Intrepid. There is a fan throttling issue after resuming from hibernate in 32-bit (Hardy or Intrepid), so I encourage going to 64-bit, where the problem doesn't exist.

Right, that came up in one of my earlier threads.  It's one of the reasons I'm making the jump, despite expectation of some small hassles.

Side note: Every few boots the fan will remain stuck at 100% and never slow down, regardless of system load (or lack of).  Hopefully that'll disappear too....

> **thomasaaron said:**
> You'll get better battery life out of a 5400 RPM drive if you do a lot of hard-drive intensive stuff. If you're not doing hard-drive intensive tasks, you probably would notice the speed benefit of a 7200 RPM drive at boot up.

Sure, I'm probably just going to stick with 5400 for battery reasons.  Though if it would help load times with Eclipse and SQL Developer, it would *almost* be worth it just for that. ;^)

As always, thanks for your help!

---


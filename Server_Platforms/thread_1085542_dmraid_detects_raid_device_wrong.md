---
title: "dmraid detects raid device wrong"
date: 2009-03-03
forum: Server Platforms
---

### Post by alkisx on 2009-03-03
I have an adaptec hostraid (asr) - fakeraid.

The problem is that dmraid instead of asr it detects it as dff1.
Using the -f asr option to check for asr, it says No RAID disks found. It only detects it as ddf1.

And because my array is raid10, and ddf1 does not support raid10,
I ended up having the options to mirror 1 disk 4 times....

Any one knows how to do the dmraid see the device right?

---


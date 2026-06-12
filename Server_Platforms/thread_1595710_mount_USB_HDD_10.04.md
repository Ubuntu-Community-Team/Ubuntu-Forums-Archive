---
title: "mount USB HDD 10.04"
date: 2010-10-13
forum: Server Platforms
---

### Post by cj13579 on 2010-10-13
Hi all,

So I have been hunting around a little on this one but can't figure it out. 

Mounting my HDD(Maxtor500Gb) should be a doddle and works (manual and auto-mount) on my desktop and lappy. But I can't for the life of me get it to mount on my server.

The thing is, my system doesn't even seem to generate (if that is what happens) a /dev entry for it e.g. /dev/sdb1 etc.

How am I meant to go about mounting this bugger if I don't have one of those? And, if the case may be, how do I create one of those?

Your help as always is greatly appreciated.

Chris

---

### Post by cj13579 on 2010-10-13
Ok, done it.

Installed ```
udev
``` on my system and a /dev entry was created. All is well.

Marked as solved.

---


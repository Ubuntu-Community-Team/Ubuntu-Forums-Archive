---
title: "inconsistencies with installing new kernel images in ubuntu"
date: 2010-10-12
forum: The Cafe
---

### Post by user1397 on 2010-10-12
So I've noticed that as ubuntu installs new kernel images there is a certain inconsistency with the version numbers.

For example, right now I have the following packages installed:

linux-image ver 2.6.32.25.27
linux-image-generic ver 2.6.32.25.27

and this one:
linux-image-2.6.32-25-generic ver 2.6.32-25.44

what is up with the 27 and the 44...

I know this isn't a big deal, just something I noticed.

---

### Post by user1397 on 2010-10-14
nothing? :(

---

### Post by Bölvaður on 2010-10-14
I dont get it... the number is increasing, so that is quite good. Not sure what more you would like. Those are the versions picked by the ubuntu team.

---

### Post by FuturePilot on 2010-10-14
2.6.32 is the upstream version.
-25 is the ABI version
.44 is the sequence number of the upload

The first two packages you mentioned
> linux-image ver 2.6.32.25.27
linux-image-generic ver 2.6.32.25.27

are meta-packages and have a slightly different versioning.

---

### Post by user1397 on 2010-10-14
> **FuturePilot said:**
> 2.6.32 is the upstream version.
-25 is the ABI version
.44 is the sequence number of the upload

The first two packages you mentioned

are meta-packages and have a slightly different versioning.
ah I see, thread solved then.

---


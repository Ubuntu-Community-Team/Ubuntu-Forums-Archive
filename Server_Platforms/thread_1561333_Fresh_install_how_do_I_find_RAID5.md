---
title: "Fresh install: how do I find RAID5?"
date: 2010-08-26
forum: Server Platforms
---

### Post by disconap on 2010-08-26
So the server crash/corruptions I posted about earlier, I finally gave up and reinstalled/configured my server.  Everything went fine, it's running great; however, I plugged in my RAID5 sotrage box (via eSata) and I can't find the RAID5.  It's not listed anywhere under /dev/, though the individual drives are, and mdadm either can't see it or, for some reason, can't assemble it.  There are files I really need off it (which is why it was set up as a RAID5 in the first place, and why it was external).  How can I mount the RAID?  I searched around/read through mdadm manuals and forums/sites for the past couple hours and didn't find anything that worked...

EDIT TO ADD MORE INFO:
RAID5 built on devices sda2-5 (3 active, one parity) using mdadm

---

### Post by craigp84 on 2010-08-26
```

sudo mdadm -A /dev/md0 /dev/sda2 /dev/sda3 /dev/sda4 /dev/sda5

```

---

### Post by disconap on 2010-09-11
Sorry for the bump, just realized I never responded.  I ended up having to rebuild the raid but it all worked out fine.  Thank you for the help!  :)

---


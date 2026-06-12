---
title: "How to remove botched RAID setup?"
date: 2009-08-25
forum: Server Platforms
---

### Post by DejitaruJin on 2009-08-25
Okay, at some point I attempted to follow some ludicrously complicated setup instructions, for a SATA PCI card that straddles the line between hardware RAID and software RAID. It didn't work, so I gave up.

Now, I see that I am left with devices dm-0 through dm-3; they're quite clearly two pseudo-duplicates of the two actual hard drives, only containing partition data fdisk can't make any sense of.

Now, I want those gone. Just, completely gone, and I don't care if it wipes out all data on both hard drives in the process. What steps do I take to accomplish that?

---


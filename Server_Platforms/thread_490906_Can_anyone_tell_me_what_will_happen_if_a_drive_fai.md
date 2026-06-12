---
title: "Can anyone tell me what will happen if a drive fails in a LVM set using XFS?"
date: 2007-07-03
forum: Server Platforms
---

### Post by evilspoons on 2007-07-03
As the subject says...

I have a LVM set up on my fileserver. It's basically a bunch of old hard drives concatenated together using LVM so that I can have a single SAMBA file share for storing all my family's crap in a central location without losing it on so many different hard drives.

I have a ~600 GB volume formatted with XFS, and I'm looking to add another 500 GB drive to it. Right now, it's made up of a 120, a 160, and a 320.

What will happen if, say, the 160 GB hard drive dies? Will the files on the 120 and the 320 (provided they didn't span into the 160) still work? Will I be able to recover anything the "normal" way with dd and whatnot provided the 160 doesn't die entirely?

Is there any way to specify one of the drives as a "parity volume" for redundancy, or will that limit me to the size of the smallest disk (which would stink, having a 120 and a 500...).

Please forgive me if this is common knowledge. I've spent the last two hours attempting to figure this out, and in spite of my intense googling, have not found any useful information. Thanks!

---

### Post by ShiftyPowers on 2007-07-05
I have a similar problem...one very large LVM array running ReiserFS on it which just recently started giving me a bunch of reiserfsck errors

---


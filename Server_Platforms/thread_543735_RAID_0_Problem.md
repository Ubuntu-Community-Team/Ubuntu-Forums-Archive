---
title: "RAID 0 Problem"
date: 2007-09-05
forum: Server Platforms
---

### Post by JeffElkins on 2007-09-05
I have a media server setup with 4 400GB SATA drives connected to a SiI 3114 card. It's setup via mdadm as RAID 0, formatted as ext3. I'm generally happy with this setup speedwise, over a gigabit network.

Just recently after a power failure, I started to experience problems writing new content to the RAID array. Using scp, data would start out copying at full speed, then eventually stall. Same problem when doing a local cp from the server's boot drive to the array.

I'd like to repair this problem w/o rebuilding the array and reloading my content, although luckily I'm all backed up.

Any help appreciated!

---

### Post by Brazen on 2007-09-05
try fsck-ing it.

---

### Post by JeffElkins on 2007-09-05
Thanks, did that. The drive array is clean according to fsck and mdadm.

---

### Post by JeffElkins on 2007-09-06
Additionally, this filesystem has mysteriously mounted itself as read-only!?

No clue as to what's going on here.

---


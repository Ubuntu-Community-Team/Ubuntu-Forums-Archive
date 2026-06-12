---
title: "Expanding a RAID5 array"
date: 2009-02-26
forum: Server Platforms
---

### Post by TomB19 on 2009-02-26
I have a 4 x 750GB RAID5 array (formatted ext3).

I want to move it to a RAID5 array of 6 x 750GB drives.  It looks like I can do that fairly easily.

[http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/](http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/)


If I upgrade the drives one at a time with 1.5 TB units, making the array converge each time, I assume I can get the unit to 6 x 1.5 TB drives with the legacy data, but with the same capacity as the 6 x 750 GB array.

Is there a way to then grow the array to consume all space available?  It looks like the "--grow" switch is for adding individual drives.

---

### Post by TomB19 on 2009-02-26
I found everything I need to know on this page:

[http://linux-raid.osdl.org/index.php/Growing](http://linux-raid.osdl.org/index.php/Growing)

I apologize for posting a question before I had completed the research.  :)

---


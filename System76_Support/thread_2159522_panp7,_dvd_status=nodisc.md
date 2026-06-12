---
title: "panp7, dvd status=nodisc"
date: 2013-07-03
forum: System76 Support
---

### Post by princesshammer on 2013-07-03
The dvd drive in my panp7 won't recognize some video dvds. lshw shows "status=nodisc", and the drive head makes a repetitive noise for about a minute when a video dvd is inserted.

I don't believe this is a libdvdread or css issue, because the drive has to recognize the disc before those libs can do anything with it.

I thought perhaps the drive was just broken, however it *does* recognize a double layer DVD+R video dvd (udf format), and CDs are no problem. It seems like a drive firmware thing, like region, or something. I've set the region with regionset, and it matches the dvd. Have also rebooted after doing so.

Is there anything else I can try?

---

### Post by princesshammer on 2013-07-05
It's working now, after cleaning with a lens cloth. I didn't expect that to work, since it was reading DVD+R discs without error.

---


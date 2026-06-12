---
title: "750GB Drive in PanP6"
date: 2010-08-05
forum: System76 Support
---

### Post by Noah0504 on 2010-08-05
I just installed a 750GB HDD in my PanP6 to replace the 500GB it came with.  The weird thing is that after a fresh install, it only shows I have 632GB free... this seems way too low even after you factor in what should be lost after formating.  The disk utility show that 732GB should be available and after the 18GB swap created by default, the math just doesn't come out right.

If I right click the volume in the file manager, it shows unknown next to the volume...

Is this HDD not supported, did I do something wrong or is this normal?  Does anyone have anything to contribute to this?

---

### Post by oldfred on 2010-08-05
The bigger the drive the more you do not have. MB is not MiB. Hard drives sizes are not counted the same as space. 

You also loose about 5% to formating especially for the journal.

MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)

---

### Post by Noah0504 on 2010-08-05
> **oldfred said:**
> The bigger the drive the more you do not have. MB is not MiB. Hard drives sizes are not counted the same as space. 

You also loose about 5% to formating especially for the journal.

MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
Well, I guess I know all of that, but it just surprised me of the amount.  I wanted to make sure it looked normal.  I'm used to 500GB and TB drives, so I kind of know what the amount of formated space should be.  Also, this WD drive has a bunch of features I've never heard of before including advanced formatting technology.  Haha.

I end this by saying that I am a computer power user and am actually a computer and networking technician for a living... but, we learn something new every day.  :P

I won't worry about the space concern -- it's still a ton of room, which is exactly what I wanted to accomplish.  Sadly, it's just more to backup now.  :)

---

### Post by isantop on 2010-08-06
Keep in mind that the space isn't really being taken up by anything; it simply doesn't exist. Manufacturers typically quote storage size in GB (Gigabytes), which equal one billion bytes each. Software, like Linux, calculates storage size in GiB (technically Gibibytes, although they are commonly called Gigabytes as well in the US), which equal 1,073,741,824 bytes. Thus, the size reported by the OS will appear smaller than the size reported by the manufacturer.

---

### Post by Noah0504 on 2010-08-07
> **isantop said:**
> Keep in mind that the space isn't really being taken up by anything; it simply doesn't exist. Manufacturers typically quote storage size in GB (Gigabytes), which equal one billion bytes each. Software, like Linux, calculates storage size in GiB (technically Gibibytes, although they are commonly called Gigabytes as well in the US), which equal 1,073,741,824 bytes. Thus, the size reported by the OS will appear smaller than the size reported by the manufacturer.
Like I said, I knew that the marketed size is never the same after formating, but it just seemed like a little more than usual.  :P

---


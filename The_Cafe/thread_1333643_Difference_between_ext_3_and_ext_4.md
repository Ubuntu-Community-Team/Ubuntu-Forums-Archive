---
title: "Difference between ext 3 and ext 4?"
date: 2009-11-21
forum: The Cafe
---

### Post by Eagles18 on 2009-11-21
I know there are differences between them,but what are they?

---

### Post by RiceMonster on 2009-11-21
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by SunnyRabbiera on 2009-11-21
Here are wikipedia articles on the matter:
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

What you use in the end is up to you, there is no real advantage to "upgrade" from ext3 to 4 other then speed and power, but EXT3 is the more stable right now in my opinion.

---

### Post by Eagles18 on 2009-11-21
Thanks guys, I thought I was missing out on something by staying with ext 3.

---

### Post by SunnyRabbiera on 2009-11-21
> **Eagles18 said:**
> Thanks guys, I thought I was missing out on something by staying with ext 3.

Nah you are not missing out on much by using EXT3, like I said speed is a big advantage of EXT4.
Its not a security update and nor will EXT3 go out of style anytime soon.
Heck EXT2 is still around, and one can use it without issue...
But it does suffer when power outages happen.

---

### Post by BuffaloX on 2009-11-21
I'm a bit confused.
The Wiki page for Ext4 states that it exceeds ext3 64 bit address limit.
[FONT="Courier New"]
2^64 = 18, 446, 744, 073, 709, 551, 616
______Exa,Peta,Tera,Giga,Mega,Kilo,Byte
[/FONT]

That is 18 Exabyte! That's more than 18 million Terabyte!
Who need more than that?

But then they continue to say Ext 4 can "only" handle 1 Exabyte?

None the less, I'm VERY pleased with Ext4, it's fast, and when disk checks run, they take only about 1/10 th. the time they did on ext3.
I didn't time it, but that's about how it feels to me.

Edit:
Saw Ext 3 actually is maxed at 16 Terabyte disks, which is far from 64 bit!

---

### Post by Zoot7 on 2009-11-21
The main difference i've noticed is that fsck completes a LOT faster than ext3.
I've also noticed it's substantially more snappy when copying large amounts of small files.

---


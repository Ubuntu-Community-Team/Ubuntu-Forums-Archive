---
title: "Opening the case of a Koala?"
date: 2007-12-05
forum: System76 Support
---

### Post by Paradoxdruid on 2007-12-05
My little media center (a first edition Koala) has recently been making an awful noise...  a little canned air helped some, and convinced me that a dust clod is stuck in the system fan.

My google-fu is weak, though, because I haven't been able to find a manual of guide to opening the Koala's case--  it looks like I'll need to push 6 plastic pins out at once, but maybe there's a proper way to do it.

Any thanks is much appreciated!

---

### Post by thomasaaron on 2007-12-06
Actually, you just have to release the three clips on one side. Then that side will lift. Then you can work on the other side.

---

### Post by Paradoxdruid on 2007-12-06
I tried opening the case tonight...  used butter knives, credit cards, etc, and managed to lift the three clips (and actually, all six clips).  The case still wouldn't budge, and where it meets the back panel, seems glued or otherwise still tightly fastened.

What else would you suggest?

Failing that, would it be possible to mail the Koala to system76 for repair?  I'd rather not, but it's not a very good media center making horrible wheezing noise whenever the fan engages (and I worry about long term damage or fire hazard).

Thanks for any advice!

---

### Post by thomasaaron on 2007-12-07
I'm a bit confused about "the case meeting the back panel..." part. Essentially, you remove the plastic lid from the top. Then you can access everything beneath it by removing a screw or two (or three, can't remember).

The way I do it is to pry back the three "latches" on the side (not front or back) of the plastic cover and pop the cover up on one side. Then fiddle with the other side.

If that doesn't help, you might want to contact me via email to figure out how to deal with it. If it is making that bad of noise, you may end up needing parts.

---

### Post by Paradoxdruid on 2007-12-07
Hi Thomasaaron, and thanks for the help.  I couldn't find your e-mail address, so I sent you a private message on this forum.

If I resolve this situation, I'll be sure to post the final verdict for others!

---

### Post by Paradoxdruid on 2007-12-09
So...  I wasn't aware that the padding on the underside plastic was removable.

Once that was removed, I saw the four case screws, removed those, and got the case open.  Well, half open--  the front slid off easily, but the rear panel area wouldn't come free.  There's a lot (harddrive, CD drive, etc) mounted to the top gray plastic lid, and some connections in the back weren't coming free--  and I didn't want to force them too much.  So I reassembled it.

Since then, the wheezing sound has stopped, but the system actually overheated and powered off once.  So I installed lm-sensors, and it looks like the CPU fan is valiantly struggling, because the case fan isn't turning on at all anymore.

I think at this point, I've exhausted my ability to properly treat the Koala, and need to get in touch with System76 about possible repair and replacement of the fan.

---

### Post by thomasaaron on 2007-12-10
You can email me at support(at)system76(dot)com.
When you do, please send the output of: acpi -t

Best,
T

---


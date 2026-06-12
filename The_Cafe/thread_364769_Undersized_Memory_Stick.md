---
title: "Undersized Memory Stick??"
date: 2007-02-18
forum: The Cafe
---

### Post by baillie on 2007-02-18
* Not sure if this is the right section or not, please move if I'm wrong.

Hi, 

I bought a new USB memory stick today, 2gb integral, and am wondering if the stick is undersized/fautly, when viewing it under windows xp, it shows as being 1.46gb.

[img]http://www.imagemule.com/uploads/undersizedCTYz.jpg[/img]

The one on the left is my old 256mb stick, and on the right the new "2GB" stick. I'm used to manufacturers using 1024bytes, and windows using 1000bytes (or is it the other way around), but to lose 500mb on a 2gb stick?! Surley it should be at least 1.8gb, no? The new drive is partitioned into 2, but the other partition is only 1.5mb. 

Should the free space not be closer to 2,000,000,000 bytes?

This is what i was expecting, taken from a 2gb CF memory card:
[img]http://www.imagemule.com/uploads/undersized2HMa8.jpg[/img]

I thought about it being a hidden partition, security and all that, so I tried it in Ubuntu (i'm still mainly windows but am gradually switching), and it won't mount at all, not even recognized, but my other two drives are automounted fine. Just flashes at me (the usb flash drive that is).

So simple question is this a faulty usb drive?

---

### Post by Omnios on 2007-02-18
Actually this is common my 120 gig hardrive shows up as 111g. Apperently the manufactured rating and how it is measured by the computer is different,  personally I think this is bad marketing.

---

### Post by baillie on 2007-02-18
> **Omnios said:**
> Actually this is common my 120 gig hardrive shows up as 111g. Apperently the manufactured rating and how it is measured by the computer is different,  personally I think this is bad marketing.

Yeah but using my drive as an example, I'm losing 25% of the advertised capacity, so that would make you 120Gb drive show as 90Gb. 

Losing 500mb (roughly) can't be right, can it?

---

### Post by Anthem on 2007-02-18
Depends on how you count.  A "kilobyte" sounds like 1,000 bytes, but it's not.  It's actually 2^10 = 1,024 bytes.  A megabyte is 2^20 = 1,048,576 bytes.  A gigabyte is 2^30 = 1,073,741,824 bytes.  2 gigabytes, then should be 2,147,483,648 bytes.  Manufacturers commonly call 1,000,000 bytes a gigabyte, when in actuality it's actually less.  

**A drive that's advertised as a 2-gig drive, then, is actually only 1.86 gigabytes.**

Yours it way less than that.  You got jobbed.  Return it.

---

### Post by Anthem on 2007-02-18
> **baillie said:**
> I thought about it being a hidden partition, security and all that, so I tried it in Ubuntu (i'm still mainly windows but am gradually switching), and it won't mount at all, not even recognized, but my other two drives are automounted fine. Just flashes at me (the usb flash drive that is).
This is interesting, actually, and makes me re-think my previous statement.  The hidden partition thing would make sense.  Did the packaging imply anything like that?

You sure it won't mount in Ubuntu?  Do you know how to mount it manually?

---

### Post by Polygon on 2007-02-18
ive heard about this, i think its because what the company believes to be a gigabyte and what you think a gigabyte is are different things

here is an example that i think is right:

megabyte is 1024 kb (i think...) but then some companies format and make teh disks so a megabyte is 1000 kb.

multiply this by a lot, and you will notice a considerable difference in size

---


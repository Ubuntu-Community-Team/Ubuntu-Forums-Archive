---
title: "Could you &quot;force&quot; a CD drive to erase a CD-R?"
date: 2010-02-15
forum: The Cafe
---

### Post by TheOnlyMrK on 2010-02-15
I know I know I've read it a thousand times over the web that you can not erase/rewrite to a CD-**R** but I've always wondered could you somehow **force** a CD drive to burn to the CD again to destroy the original data on it? This question is out of pure curiosity, I don't actually need to do this, if I did I'd just sit the CD over a candle or something to destroy it.

---

### Post by bhaverkamp on 2010-02-15
I have to believe the answer to this question is yes. This is the basis of the labeling feature used on some CD/DVD burners. My guess is that there are safeguards to prevent this

---

### Post by NightwishFan on 2010-02-15
Edit: Irrelavant

---

### Post by TheOnlyMrK on 2010-02-15
> **NightwishFan said:**
> I use this command to blank a cd/dvd:

If you only have one drive:
```
wodim -force blank=fast
```If you have more than one: (to pick one name is like /dev/sr0 /sev/sr1 etc..)
```
wodim -force dev=/dev/name blank=fast
```If you want to delete all the contents for security reasons, not just to "reburn" then use:
```
wodim -force blank=all
```
And this works on CD/DVD-Rs? (Not just CD/DVD-RWs)

---

### Post by NightwishFan on 2010-02-15
EDIT: I missread your post! I think you could SOMEHOW manually force it to try, but it would not work.

---

### Post by Grenage on 2010-02-15
> **TheOnlyMrK said:**
> And this works on CD/DVD-Rs?

No.

---

### Post by TheOnlyMrK on 2010-02-15
I know this has to be possible... All it has to do is ignore the fact it's a used CD-R and do a full erase (Basically fill it with zeros, right? At least that's how it works with hard drives.) and there you go, you've got a destroyed CD-R.

---

### Post by NightwishFan on 2010-02-15
I do not think it is designed to. I am sorry I misread your post, I have terrible vision so I tend to "guess" at times.

---

### Post by Psumi on 2010-02-15
> **TheOnlyMrK said:**
> I know this has to be possible... All it has to do is ignore the fact it's a used CD-R and do a full erase (Basically fill it with zeros, right? At least that's how it works with hard drives.) and there you go, you've got a destroyed CD-R.

You can still recover data on it, but filling it with zeros doesn't make it empty.

---

### Post by Grenage on 2010-02-15
Considering that there has already been data written, I have no idea how receptive the disk would be to another write.  Other than that, it would be possible; I doubt if anyone has written such a program - it would be of no real use.

---

### Post by TheOnlyMrK on 2010-02-15
> **NightwishFan said:**
> I do not think it is designed to. I am sorry I misread your post, I have terrible vision so I tend to "guess" at times.
It's cool. I'm sure you won't be the last, the one letter difference between CD-R and CD-RW don't help much.

---

### Post by Psumi on 2010-02-15
> **TheOnlyMrK said:**
> It's cool. I'm sure you won't be the last, the **_one letter difference_** between CD-R and CD-RW don't help much.

Do you even know what Acronym means?

---

### Post by TheOnlyMrK on 2010-02-15
> **Grenage said:**
> Considering that there has already been data written, I have no idea how receptive the disk would be to another write.  Other than that, it would be possible; I doubt if anyone has written such a program - it would be of no real use.
I'm reading up on how CD-Rs hold data to see if once data is written to the disk it is something that the laser doesn't have enough power to change (destroy) anymore. As I said this whole question is out of curiosity, if I wanted to destroy a CD I'd hold it over a candle and admire the pretty colors it melts into.

---

### Post by TheOnlyMrK on 2010-02-15
> **Psumi said:**
> Do you even know what Acronym means?
Nope. But I went to Google and now I do.

---

### Post by Grenage on 2010-02-15
> if I wanted to destroy a CD I'd hold it over a candle and admire the pretty colors it melts into

I wouldn't, the chemicals given off are incredibly bad for you.

---

### Post by TheOnlyMrK on 2010-02-15
> **Grenage said:**
> I wouldn't, the chemicals given off are incredibly bad for you.
Well, I was trying to give a funny alternative. The smoke detectors in this place already don't like me, I'm not giving them more reasons.

---

### Post by TheOnlyMrK on 2010-02-15
Okay after some research, and HowStuffWorks dumbing things down a bit. I found out that CD-Rs are made of a reflective material that basically the drive writes (burns) to it and makes some parts to where it's not reflective anymore (thus making it 1's and 0's). So basically if you made the laser stay on and just continuously write to the CD to where nothing would be reflective anymore not only would the data be erased, I'm pretty sure their is no way it would be recoverable.

EDIT: Reflective = 1, Nonreflective (burned) = 0, so it literally would be the same as zeroing out a hard drive.

---

### Post by hessiess on 2010-02-15
> **TheOnlyMrK said:**
> Okay after some research, and HowStuffWorks dumbing things down a bit. I found out that CD-Rs are made of a reflective material that basically the drive writes (burns) to it and makes some parts to where it's not reflective anymore (thus making it 1's and 0's). So basically if you made the laser stay on and just continuously write to the CD to where nothing would be reflective anymore not only would the data be erased, I'm pretty sure their is no way it would be recoverable.

EDIT: Reflective = 1, Nonreflective (burned) = 0, so it literally would be the same as zeroing out a hard drive.

My guess is that double heating the die in a -R disk would burn the parts of the surface which were previously not burnt, but double-burn the places that were. Meaning that there would potentially still be a ``ghost'' of the data on the disk, which may or may not be possible to recover. To avoid this you would have to burn the negative of whatever the disk currently contains.

---

### Post by madhi19 on 2010-02-15
I got a lowtech two seconds solution to that question pop the CD out and just break it!

---


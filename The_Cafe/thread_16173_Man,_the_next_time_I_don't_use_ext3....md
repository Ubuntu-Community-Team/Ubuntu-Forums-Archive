---
title: "Man, the next time I don't use ext3..."
date: 2005-02-19
forum: The Cafe
---

### Post by jdong on 2005-02-19
**PLEASE SLAP ME**

I chose reiserfs for my 5-disk RAID5... Today, I accidentally performed a hard reset during backports compiling, and that threw most of /var into /dev/null......


Reformatting....

---

### Post by BWF89 on 2005-02-19
EDIT: Why are there different file systems if every one except ext3 suck?

---

### Post by az on 2005-02-19
There are many different file systems because there are different needs.  Reiserfs is quite fast at handling many many small files.  Much faster than ext3.  Ext2 and ext3 are sort of middle of the road in terms of speed.

It's give and take.  There is no filesystem that has it all.

There is a chart somewhere on the internet showing the different benchmark results for various filesystems.

---

### Post by slackerj on 2005-02-19
[QUOTE=BWF89]EDIT: Why are there different file systems if every one except ext3 suck?[/QUOTE]
 Choice I suppose.

I love ext3 but my father likes resier fs. They both do basically the same job but he has always used resier and I have always used ext3.

Same could be said for editors. vi, emacs, pico, nano. All edit files; but some like one more than the other.

6 to one. Half a dozen to another really :)

---

### Post by zenwhen on 2005-02-19
Reiser has never failed me.

---

### Post by TravisNewman on 2005-02-20
jdong, were you using reiser 4? if so that's probably the problem.

reiser3.2 or whatever has always done well for me, but it seems that ext3 is still the most stable.

---

### Post by tim1 on 2005-02-20
[QUOTE=jdong]**PLEASE SLAP ME**

I chose reiserfs for my 5-disk RAID5... Today, I accidentally performed a hard reset during backports compiling, and that threw most of /var into /dev/null......


Reformatting....[/QUOTE]

I don't understand your point. You say you used reiserfs but the topic says that you won't use ext3 the next time, so what will you use?

greets, tim

---

### Post by TravisNewman on 2005-02-20
No, he said "Man the next time I don't use ext3... PLEASE SLAP ME"
So we should slap him if he ever uses anything but ext3 again, get it?
He broke up a sentence between the subject and the post.

---

### Post by Jad on 2005-02-20
Dear jdong, 
Please attach your face to be able to slap you.
Regards
Ubuntu forums users.
:-)

---

### Post by az on 2005-02-20
Face?

I though he meant ass.

---

### Post by Jad on 2005-02-20
Well, it depends How pretty his ass is.

---


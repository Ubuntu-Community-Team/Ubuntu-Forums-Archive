---
title: "Join 2 ogg files"
date: 2008-07-21
forum: Ubuntu Studio
---

### Post by pshah.mumbai on 2008-07-21
How do I join 2 ogg files (screencast) ?

I am looking for days, but cannot find any suitable method to do that.

Thanks in advance

:guitar:

---

### Post by thorgal on 2008-07-21
... mmmm ... you could try the good old 'cat >' command in a terminal :

cat file1.ogg file2.ogg > file3.ogg

see if it works.

---

### Post by pshah.mumbai on 2008-07-22
nope. it does not play after the 1st file ends.

---

### Post by thorgal on 2008-07-22
ah too bad. OK, a more complex way :

- open audacity
- import file1.ogg, this will create a track
- import file2.ogg, this will create a second track
- time-shift one of the track with the time-shifting tool
- once you're happy about the timing, select mixdown or something called like that from the main window menu. This will create a mixed down track of the whole session.
- export back to ogg from the export menu audacity comes with

That's a rather quick way too if you know audacity a bit.

---


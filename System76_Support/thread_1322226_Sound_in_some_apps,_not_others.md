---
title: "Sound in some apps, not others"
date: 2009-11-10
forum: System76 Support
---

### Post by SteveFoerster on 2009-11-10
Most of my apps make sound normally.  A few, however, do not make sound at all, namely MuseScore and NoteEdit.  Can anyone suggest why this might be and what I might do about it?  I have a Meerkat NetTop running Karmic.

Thanks,

-=Steve=-

---

### Post by corey.abshire on 2009-11-10
> **SteveFoerster said:**
> Most of my apps make sound normally.  A few, however, do not make sound at all, namely MuseScore and NoteEdit.  Can anyone suggest why this might be and what I might do about it?  I have a Meerkat NetTop running Karmic.

Thanks,

-=Steve=-

Not sure about NoteEdit, but to get MuseScore working I had to open up the prefs and adjust the I/O settings appropriately before it would work. The defaults didn't work.

---

### Post by SteveFoerster on 2009-11-14
I kept searching and eventually found a reference to something called TiMidity.  Then I saw this thread: 

[http://ubuntuforums.org/archive/index.php/t-770148.html](http://ubuntuforums.org/archive/index.php/t-770148.html)

Scroll down to the post from lloydkuhnle on February 22nd, 2009.  His info helped a lot. 

1. I downloaded and installed TiMidity, then started it in terminal like this:

**timidity -iA -B2,8 -Os -EFreverb=0 2>&1 &**

2. I started NoteEdit and went to Settings -> Configure NoteEdit... 

3. In the box I clicked on Sounds then clicked on **TiMidity port 0 128:0**

After that NoteEdit could be heard!  Yay!  Weirdly, nothing else can be heard while NoteEdit is open.  But I would much rather have a NoteEdit that monopolizes sounds while it's running than none at all.

MuseScore, meanwhile, still doesn't utter a peep no matter what I do.  But I only need one of them, so I guess I'm as good to go as I'm going to get.

-=Steve=-

---


---
title: "Wine not recognizing CD"
date: 2011-06-05
forum: Wine
---

### Post by Drate on 2011-06-05
I am using Ubuntu 11.04, Wine 1.2.2 and testing with [Infrarecorder]("http://infrarecorder.org/").

Simply put, Infrarecorder is not recognizing the CD player, and worse still, I cannot get Wine (via the configuration tool) to detect it either.

Based on [other issues]("http://ubuntuforums.org/showthread.php?t=1775346") I'm having, I am gathering this has something to do with the way Natty handles the cdrom?

I have run practically all tests listed in this post and indicated in the other thread on two machines with identical results.

Anybody have any clues as to how I can get Wine (and thus infrarecorder) to recognize the cdrom?

---

### Post by mc4man on 2011-06-05
I believe that your Infrarecorder will have issues with audio cd's, maybe be ok with data disc's.
(data disc's can be autodetected in wine - will show up as /media/<volume label>, this is because of the new way of dynamically mounting optical media vs old one of fstab entry and static mount point

Not sure why you can't copy an audio cd with brasero, should work but then again brasero is very inconsistent across installs (works here but I never use - screen 1

From a wine perspective you may find ImgBurn better suited - will rip an audio cd to a .bin and cue which then can easily be burned back to disk
(audio cd's should/can not be ripped to .iso
ImgBurn has an I/O option that allows direct access to drive - winecfg is irrelevant and not needed -  Tools > Settings > I/O -  screen 2

screen 3 shows ImgBurn in 'read' mode on an audio cd

If inclined to try ImgBurn then this post outlines basic install, some links ect.
[http://ubuntuforums.org/showthread.php?p=10847725#post1084772](http://ubuntuforums.org/showthread.php?p=10847725#post1084772)

---

### Post by Drate on 2011-06-05
Well would you look at that... why on earth is it seeing the CD differently for being an audio cd?

I see now that this also relates to my questions in the other post.  Thank you SO much for this information.  Now I know the catalyst for my issues I can begin looking into proper fixes and work arounds!

Seriously! Thank you!

---


---
title: "Coincidences do happen."
date: 2008-07-14
forum: The Cafe
---

### Post by dondad on 2008-07-14
Scenario:

Applied updates from update manager
rebooted
No task bars and a gnome error, OK, now what happened? Some bad update?;-)
power down completely and then back on. Task bars back, ok, all is well.
about 5 minutes later, click on a menu and get some really weird stuff at the cursor location...huh?
Play around a bit, nothing, so restart gdm
Everything back to normal
Look around to see what is running, cannot find anything abnormal.
a few minutes later, weird stuff on cursor again, play around a bit, then white screen of death.
Get out of that by rebooting and now black screen and nothing. ;-( no text, nothing.
Think, why won't it boot?
Try a couple more times, an still nothing, but hard drive sounds normal for a boot.
Open computer and reseat connections, still nothing.
Move monitor from digital to analog card output and get some (not correct) display, but enough to see that it was booting. Hmmm........ Looks like bad video card.

Replace video card and all is well again.

Moral of story: Coincidences do happen. Problem happened right after update, but unrelated. The hardware can have a significant effect on stuff that you might not expect. The card was causing gnome errors, and a bunch of other problems that seemed unrelated and were initially blamed on updates.

---

### Post by Canis familiaris on 2008-07-14
That is why we should think scientifically as you did and not come to conclusions too early.

---

### Post by madjr on 2008-07-14
> **dondad said:**
> Scenario:

Applied updates from update manager
rebooted
No task bars and a gnome error, OK, now what happened? Some bad update?;-)
power down completely and then back on. Task bars back, ok, all is well.
about 5 minutes later, click on a menu and get some really weird stuff at the cursor location...huh?
Play around a bit, nothing, so restart gdm
Everything back to normal
Look around to see what is running, cannot find anything abnormal.
a few minutes later, weird stuff on cursor again, play around a bit, then white screen of death.
Get out of that by rebooting and now black screen and nothing. ;-( no text, nothing.
Think, why won't it boot?
Try a couple more times, an still nothing, but hard drive sounds normal for a boot.
Open computer and reseat connections, still nothing.
Move monitor from digital to analog card output and get some (not correct) display, but enough to see that it was booting. Hmmm........ Looks like bad video card.

Replace video card and all is well again.

Moral of story: Coincidences do happen. Problem happened right after update, but unrelated. The hardware can have a significant effect on stuff that you might not expect. The card was causing gnome errors, and a bunch of other problems that seemed unrelated and were initially blamed on updates.

you may also want to check that your disk is not **FULL** or very low on space before updating.

**Ubuntu does not warn you when you run out of space.**

i had those same **symptoms** for hours till i realized that. Worst part was **firefox acted weird and kept crashing**. So getting an answer to the problem was hard.

---

### Post by dondad on 2008-07-14
> **madjr said:**
> you may also want to check that your disk is not **FULL** or very low on space before updating.

**Ubuntu does not warn you when you run out of space.**

i had those same **symptoms** for hours till i realized that. Worst part was **firefox acted weird and kept crashing**. So getting an answer to the problem was hard.

Thanks, could be also, but I have about 100 gig free on the root partition and about 250 gig free on /home. (have 2 500 gig drives in the computer.)

---

### Post by Polygon on 2008-07-14
ubuntu does warn you when you run out of space...at least on /home . I had a libnotify pop up telling me "Space is running out on /home!" or something similiar

---


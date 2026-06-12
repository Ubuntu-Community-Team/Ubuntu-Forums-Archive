---
title: "move windows between workspaces in compiz issue"
date: 2012-04-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by pqwoerituytrueiwoq on 2012-04-19
anyone know a fix for this
when i move a windows from one workspace to another the mouse end up a long way away from the window ([desktop recording 9.3MB]("http://www.filedropper.com/out-2ogvtar"))
in the mean time i need to find out if that python script i have works with python 2.7 (completely unrelated this this)

---

### Post by mc4man on 2012-04-20
I use a 4X1  & in the past there was a disconnect between the cursor & window when dragging a window to another WS. That seemed to be fixed with the current compiz,though I use rotate instead of wall.
(can't view your video, just downloads 177 bytes

---

### Post by pqwoerituytrueiwoq on 2012-04-20
That is the exact issue i am having how (or better yet where) can i get the fixed version of compiz for 12.04
guess i wont be using that file hosting site again... why did mediafire have to require accounts, it makes me sad
compiz --version
Compiz 0.9.7.6

version 0.8.4-5.1 works flawlessly on lmde

i don't care if i down grade compiz or upgrade it as long as it works correctly

---

### Post by pqwoerituytrueiwoq on 2012-04-21
fixed the video link in post 1
put it on a different site

---

### Post by mc4man on 2012-04-21
Those sites drive me crazy - if your file is there beats me

Anyway - what do you use, wall or rotate?
How old is your install?
If you create a new user or use Guest does this still happen?

While I do use a modified compiz, -  0.9.7.6+r3008 I don't think that matters, pretty sure this stopped happening with the 0.9.7.6 upgrade, both in unity 5.8 & 5.10

---

### Post by pqwoerituytrueiwoq on 2012-04-21
> **mc4man said:**
> Those sites drive me crazy - if your file is there beats me

Anyway - what do you use, wall or rotate?
How old is your install?
If you create a new user or use Guest does this still happen?

While I do use a modified compiz, -  0.9.7.6+r3008 I don't think that matters, pretty sure this stopped happening with the 0.9.7.6 upgrade, both in unity 5.8 & 5.10
maybe 2 weeks updates  every day
will this work?
[http://youtu.be/etB_9B1EZGg](http://youtu.be/etB_9B1EZGg)
for the record it does happen in unity guest session just enable edge flip in wall and disable grid

---

### Post by mc4man on 2012-04-21
Well - I set up a new user using the default wall & enabled edge flipping in wall
Sometimes the cursor stays & many times it gets disconnected. Also grid seems to interfere at times.

(forgot to enable wobbly windows, maybe also involved?

Other than that can't help, as mentioned I use rotate instead of wall & a vertical size of 1, thats works just fine with edge flips, the cursor stays where placed

Edit: went back & enabled wobbly & disabled snapping windows - in that case works pretty well, cursor stays connected
Maybe create a new user & try there (enable wobbly, enable edge fipping,  nothing else changed from default

---

### Post by pqwoerituytrueiwoq on 2012-04-21
> **mc4man said:**
> Well - I set up a new user using the default wall & enabled edge flipping in wall
Sometimes the cursor stays & many times it gets disconnected. Also grid seems to interfere at times.

(forgot to enable wobbly windows, maybe also involved?

Other than that can't help, as mentioned I use rotate instead of wall & a vertical size of 1, thats works just fine with edge flips, the cursor stays where placed

Edit: went back & enabled wobbly & disabled snapping windows - in that case works pretty well, cursor stays connected
Maybe create a new user & try there (enable wobbly, enable edge fipping,  nothing else changed from default
found a bug report:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/965577](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/965577)

---

### Post by mc4man on 2012-04-21
I bit the bullet & returned compiz to the current repo build & yep - the cursor disconnects on edge flipping.
As soon as I re-install the patched compiz the cursor stays put

So while not listed in this bug, when they get around to fixing it should also fix this issue, depending if the current evolving fix doesn't screw it up

[https://bugs.launchpad.net/compiz-core/+bug/862430](https://bugs.launchpad.net/compiz-core/+bug/862430)

The bug you linked may have a prior one, seems likely as the disconnect has been occurring for some time

---

### Post by pqwoerituytrueiwoq on 2012-04-21
wonder if i can install the version (0.8.X.X) on the current version of LMDE that version runs flawlessly for me

happen to know a way to make scale work on minimized windows?

---

### Post by dentaku65 on 2012-04-25
I fixed this issue on ccsm with:
> Window management -> Move window -> Uncheck Lazy Positioning
Without Lazy Positioning I'm able to move my windows with the mouse between cube faces
):P

---

### Post by pqwoerituytrueiwoq on 2012-04-26
> **dentaku65 said:**
> I fixed this issue on ccsm with:

Without Lazy Positioning I'm able to move my windows with the mouse between cube faces
):P
wish i saw this before i wiped mt testing partition and replaced it with xubuntu 12.04
goes to install compiz and try it
EDIT 
FINALLY compiz is usable for me :D

edit
it does still happen just not as 100% of the time

---


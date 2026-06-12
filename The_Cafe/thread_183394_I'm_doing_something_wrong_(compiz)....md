---
title: "I'm doing something wrong (compiz)..."
date: 2006-05-27
forum: The Cafe
---

### Post by therunnyman on 2006-05-27
The Dapper install, some of you may know, went terribly, ending ultimately with an rewiring of my hard disks, this after messing with udev for days.  But it's installed, running good, knock wood, and the long nightmare is close to an end.

As a responsible member of the Ubuntu community, I installed compiz, for testing purposes.  That went just fine; flawlessly, even.  The thing is - and give a moment to explain after I utter this - what's the bfd?  Clearly, a great deal of effort went into this project, and I think I can safely say all of us profoundly appreciate the time that went, and goes, into compiz.

Compiz is, I grant you, fun, but only for like ten minutes.  The flurry of activity around it, though, leads me to believe I'm doing something wrong here; everyone appears to love it, I got bored, fast.

My question is this, then: what can I do to come to love compiz as much as the others?

runny

PS, hey look! 100 posts!

---

### Post by GarethMB on 2006-05-28
You need to tweak the settings so they are acceptable for you. Then compiz is spangly and nice. For instance i can't stand windows wobbling for like an hour, so i have it so they barely wobble. The more just flop into place. Perhaps you should edit the post title to suggestions for glx-conf. settings?

---

### Post by Kimm on 2006-05-28
I also tried Compiz right after I got Dapper... and just like you, I found it nice for a short while.. then got rid of it.

I just dont see the point with it, I acctually prefer the look of my desktop when windows are ridgid.

---

### Post by brt on 2006-05-28
hmm, well may be compiz' eyecandy is just too much for purists ?

imho, compiz is much more than just an eyecandy wm with impressive effects, first of all it represents a milestone in the DE-development: **Xgl / aiglx **

until Xgl / aiglx was born, the xserver used to talk "2D" to a GPU even when it was optimized to talk "3D", thats why compiz performs so well also on slower computers if it has an actual 3D graphics card. Why let the CPU do all the work if the GPU does it much better. Its about optimizing, yes and i like it optimized very much!

this technology effort will also be used for new usability features and i believe thats what compiz developers have tried to achieve. (F12 is not just very nice looking, its very usefull too)

---

### Post by GarethMB on 2006-05-28
[QUOTE=brt]hmm, well may be compiz' eyecandy is just too much for purists ?

imho, compiz is much more than just an eyecandy wm with impressive effects, first of all it represents a milestone in the DE-development: **Xgl / aiglx **

until Xgl / aiglx was born, the xserver used to talk "2D" to a GPU even when it was optimized to talk "3D", thats why compiz performs so well also on slower computers if it has an actual 3D graphics card. Why let the CPU do all the work if the GPU does it much better. Its about optimizing, yes and i like it optimized very much!

this technology effort will also be used for new usability features and i believe thats what compiz developers have tried to achieve. (F12 is not just very nice looking, its very usefull too)[/QUOTE]Some really good points.

I'm using compiz + aiglx on:

1.3ghz celeron m
1 gig ram
intel 852 graphics

And despite my crappy motherboard, i'd say its as fast as gnome + metacity. And any slowness is actually due to the effects rather than hardware limits.

And F10 and F12 are awesome.

---

### Post by therunnyman on 2006-05-28
[QUOTE=brt]hmm, well may be compiz' eyecandy is just too much for purists ?

imho, compiz is much more than just an eyecandy wm with impressive effects, first of all it represents a milestone in the DE-development: **Xgl / aiglx **

until Xgl / aiglx was born, the xserver used to talk "2D" to a GPU even when it was optimized to talk "3D", thats why compiz performs so well also on slower computers if it has an actual 3D graphics card. Why let the CPU do all the work if the GPU does it much better. Its about optimizing, yes and i like it optimized very much!

this technology effort will also be used for new usability features and i believe thats what compiz developers have tried to achieve. (F12 is not just very nice looking, its very usefull too)[/QUOTE]

Very well put.  I'm rethinking my position right now (gimme a sec to become an advocate, it's hard to turn 180 right away, except in the cube, of course).  In terms of technology, it is a leap comparable to recordable CD; in the early days, media cost $100 a piece, and you had to burn from 2000 pound tape-drive machines.  In other words, it was something novel, but finally unwieldy and boring, relegated to a hot room with pasty guys in it.  Then, boom.

Lesson taken.  Thanks for that.

Maybe I should look toward developing things, instead of using them, just for the moment.

runny

PS GarethMB, post title changing...

---

### Post by dwarfy on 2006-05-28
The point is that XGL/Compiz and AIGLX are REALLY GREAT because of the 3D hardware accel for the desktop
But the wobbling effect is 'discutable'

:D

---

### Post by GarethMB on 2006-05-29
The thread title is still the same.

Here are my settings:

all plugins active except: miniwin, dock, state, water, gconf-dump.


All numbers are in order top to bottom slider unless stated
Cube: Default (i think)
Decoration: 0.91, 8.0, 1, 1, #8A91F8
Fade: 10 All windows, except fullscreen and desktop
           -urgent flashing 5(count), 15, 20, 70.
Minimise: 0.8, 0.5 for normal, dialogue, utility and toolbar. Zoom created windows (ticked).
Move: 20, 80, tick tick.
Rotate: Deafaults
Scale: 90, 100, 2, 0.1 Normal dialogue utilty toolbar. Show desktop ticked.
Resize 80, 80
Switcher i think is default.

Wobbly: 6.2, 9.1 on ALL sliders for normal windows only on move and grab maximimise effect enabled.

zoom: 1.5, 1, 1.2 no boxes ticked 0.1, 1, 2

Rest are default. You don't understand how much hassle that was lol.

---

### Post by therunnyman on 2006-05-29
Hm, GarethMB, can't figure out how to change the main title...the first post in the thread has a new title, anyway.

Yesterday, I got a chance to play with compiz a little, and while I'll still be returning to metacity here in a minute, I'll admit my mind has changed.  See, I was using a dark theme with a dark background.  Compiz doesn't work so well with that: no good drop shadows, gamma makes no difference, etc.  I nabbed a light Jackson Pollock for a background, altered it slightly, then deployed compiz.  The light background seems key (but again, light backgrounds sorta bum me out).

I'm a believer!  but I'll wait a while on compiz, at least until we can do something with those window borders.

runny

---


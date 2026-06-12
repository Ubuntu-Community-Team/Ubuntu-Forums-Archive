---
title: "Ubuntu restarted without asking after update (!)"
date: 2009-10-09
forum: The Cafe
---

### Post by chriskin on 2009-10-09
some weeks ago i took part in a thread where most of us laughed with windows' way of restarting after updates, giving you a small period of time to postpone the restart and making you re-postpone it every 4 hours
today Ubuntu restarted by itself, giving me no time at all, causing the moving of some rather large files to get stopped half-way through (everything worked perfectly afterwards though, so no harm :) )
is it something to do with me using karmic (it's beta now though, alpha didn't have that bad tendency of restarting after updates), or is it some kind of problem on my end? i sure hope it's not the new way of handling certain updates (it doesn't seem to be , by the way - i have updated more than 10 times since beta, it's the first time it happened)

---

### Post by Eisenwinter on 2009-10-09
Well, Ubuntu is trying to feel more appealing towards the Windows user, so yeah...

---

### Post by Warpnow on 2009-10-09
...If this happens to me...

bye bye ubuntu...

---

### Post by chriskin on 2009-10-09
> **Warpnow said:**
> ...If this happens to me...

bye bye ubuntu...

worse things have happened in the past, i just found it strange - i would definitely not change my os over a bug (no matter how serious it might be) on a non-stable release

---

### Post by Tibuda on 2009-10-09
I think it was not intended by the update manager, but something went wrong in your X or kernel during the update and your computer was restarted.

---

### Post by Boom!!! on 2009-10-09
It could be a bug, I know of a bug in Karmic where the system will carry out Admin commands without asking the user for password :lolflag:

These things can be usual even up to beta.

---

### Post by chriskin on 2009-10-09
> **danielrmt said:**
> I think it was not intended by the update manager, but something went wrong in your X or kernel during the update and your computer was restarted.

would updating the drivers of the graphics card cause that?
i think i saw something about nvidia on the update list

---

### Post by Warpnow on 2009-10-09
> **chriskin said:**
> worse things have happened in the past, i just found it strange - i would definitely not change my os over a bug (no matter how serious it might be) on a non-stable release

I am of course saying if it was not a bug.

---

### Post by chriskin on 2009-10-09
> **Warpnow said:**
> I am of course saying if it was not a bug.

yes, then i would consider it too
or consider downgrading at least

---

### Post by Xbehave on 2009-10-09
> **chriskin said:**
> would updating the drivers of the graphics card cause that?
i think i saw something about nvidia on the update list
It should only cause an xorg restart* however it CAN cause a kernel panic (which can restart your system aparently, but i dunno how to turn that on/or). In my expereince a gfx driver bug is likely to crash the kernel if you are using kernel mode-setting (its on by default in recent kernels).

*Well tbh it shouldn't do that as the old driver should stay in ram, but with nvidea drivers xorg crashes on updates can happen.

Whatever happened this is a bug and if you can reproduce it, you should report it! That is why your using the beta right?

---

### Post by chriskin on 2009-10-09
> **Xbehave said:**
> It should only cause an xorg restart* however it CAN cause a kernel panic (which can restart your system aparently, but i dunno how to turn that on/or). In my expereince a gfx driver bug is likely to crash the kernel if you are using kernel mode-setting (its on by default in recent kernels).

*Well tbh it shouldn't do that as the old driver should stay in ram, but with nvidea drivers xorg crashes on updates can happen.

Whatever happened this is a bug and if you can reproduce it, you should report it! That is why your using the beta right?

i don't know how to reproduce it though
i mean the drivers are updated already, can i find some error logs somewhere? if not, what am i supposed to report?

---

### Post by Xbehave on 2009-10-09
> **chriskin said:**
> i don't know how to reproduce it though
i mean the drivers are updated already, can i find some error logs somewhere? if not, what am i supposed to report?
yeah the bug is pretty much impossible to reproduce without a lot of work, you could have a look through your logs (/var/logs) in particular dmesg, messages & xorg for anything that stands out, otherwise see if you can submit a kernelcrashdump (i'm not sure where they go) along with any relevant info you can find (e.g what got updated). TBH without finding a way to reproduce it is pretty hard to find the bug let alone fix it, however if there are enough reports of this/something similar it may get looked into properly.

---

### Post by cariboo on 2009-10-09
I have to wonder why the op created this thread here, instead of in [Karmic Koala Testing & Discussion]("http://ubuntuforums.org/forumdisplay.php?f=359"). It may be an idea to request this thread be closed and start one in the proper forum.

---

### Post by chriskin on 2009-10-09
> **cariboo907 said:**
> I have to wonder why the op created this thread here, instead of in [Karmic Koala Testing & Discussion]("http://ubuntuforums.org/forumdisplay.php?f=359"). It may be an idea to request this thread be closed and start one in the proper forum.

because, since the bug has stopped (one time only) , i wanted to point out the irony of it happening, not ask for help to solve it

that is exactly why it has no place on karmic's support subforum :)

---


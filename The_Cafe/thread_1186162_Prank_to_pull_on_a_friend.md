---
title: "Prank to pull on a friend"
date: 2009-06-13
forum: The Cafe
---

### Post by cyclobs on 2009-06-13
hey guys,

ok here is the plan. i have a house mate i wanna play a trick on and i got a plan :)

basically i wanna freak him out so i decided next time i am out of the house and he is home alone i'm going to ssh into my computer and have it start playing random songs :) it's bound to freak him out since he'll have no idea why the computer is playing / stopping songs randomly 

only issue is tho is that i dunno how i would get my computer to play songs when i ssh to it :S any help with this guys?

---

### Post by Eisenwinter on 2009-06-13
Get CMUS, which is a console (curses GUI) based music player.

SSH into your machine, fire up CMUS, and play songs.

Or alternatively you could write some bash script to randomly play songs at certain times using some command-line tool like mpg123 or something.

---

### Post by cyclobs on 2009-06-13
haha, nice. it works perfect :)

---

### Post by jonathanysp on 2009-06-13
ok this may be evil but how about ssh into his computer and start playing songs on his computer? This will be 10 times freakier cause he may not care too much about your computer playing music

---

### Post by thisllub on 2009-06-13
I have done it with mpd and pms.
Freaked my daughter out.

It would work better with random sounds like breaking glass and slamming doors.

You could always use aplay as well.

---

### Post by cyclobs on 2009-06-13
> **jonathanysp said:**
> ok this may be evil but how about ssh into his computer and start playing songs on his computer? This will be 10 times freakier cause he may not care too much about your computer playing music

the only computer in this house is mine and it's usally locked when i'm not here :)

---

### Post by cyclobs on 2009-06-13
> **thisllub said:**
> I have done it with mpd and pms.
Freaked my daughter out.

It would work better with random sounds like breaking glass and slamming doors.

You could always use aplay as well.

i tried aplay but i just got white noise :S

---

### Post by Firestem4 on 2009-06-13
Do it late at night, have some haunted house sounds goin on..scary music, creepy noises, creaks lol. doors closing... mwuaha!

---

### Post by 3rdalbum on 2009-06-13
The sox package includes the "play" command - that's what I'd use.

If your friend uses Linux, you could put this command into his /etc/rc.local, or put it into a script and set it up as a Cron job:

```
while true; do sleep $(($RANDOM/1000)) && beep -f 2000 -l $(($RANDOM/100)) ; done
```

You need to install the "beep" package to get this prank to work.  If you're trying this command out in a terminal, leave it running and be patient :-)

---

### Post by Rainstride on 2009-06-13
i suggest weird 19-30/40/50's music. the weirder the better.

---

### Post by Eisenwinter on 2009-06-13
> **Rainstride said:**
> i suggest weird 19-30/40/50's music. the weirder the better.
Or music from Doom.

But your suggestion is genius, actually. It's the best one, should definitely go with that.

Something like swing and jazz. :lolflag:

---


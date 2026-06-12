---
title: "Play game form mounted iso"
date: 2009-03-20
forum: Wine
---

### Post by wlraider70 on 2009-03-20
I'm working on Disciples II Gold, the install went fine, and i can play the game.

I want to play the game from the iso.
i have gmount-iso so i mounted the iso to /media/cdrom1

Even if i open the autorun in the iso i says "cant initialize disciples II"


The entire process of mounting confuses me a little but i know that the iso is mounted, but is it mounted right?

---

### Post by Meow27 on 2009-03-20
maybe you want to try mounting it on cdrom0.... dunno if thats safe though....

---

### Post by cobaltseeker on 2009-05-21
having the same problem, 

i found this link but can't make heads or tails of the "fix" :p

any ideas?

[http://ubuntuforums.org/showthread.php?t=846551&highlight=mounting+cd](http://ubuntuforums.org/showthread.php?t=846551&highlight=mounting+cd)

---

### Post by cobaltseeker on 2009-05-21
Duh... i got mine to work - and mind you i'm by NO means an experienced linux user so i have little clue as to what i was doing here,

so if this fix is "dangerous" who knows, but i made it work :p

this is what i did :::
(in my case i was using Broodwar so i'll just do a step by step of what i did for that)

used Gmount to mount my iso file (/home/cobalt/broodwar.iso) to /media/cdrom

after "mounting" i jumped into the terminal, navigated to my wine directory (/home/.wine/dosdevices) and made sure there was no "e:" or "e::" (deleted the ones i'd created earlier)

then, following the 'fix' i posted above, 

```

ln -s /media/cdrom e:
ln -s /home/cobalt/broodwar.iso e::

```that worked! O.o

now maybe it would be "safer" to mount somewhere other than media/cdrom ? i dont know if that would work but i'll give it a shot next time :) 

Again this fix may not be the best way to do things - so i'd research a bit before doing what i said, but there you have it!

EDIT :: Okay i just tested with using another location - that does work. I think that's the safer route (I tried /home/cobalt/Mount instead of /media/cdrom)

---


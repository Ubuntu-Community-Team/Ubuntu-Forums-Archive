---
title: "[SOLVED] World of Warcraft looks weird"
date: 2008-12-15
forum: Wine
---

### Post by Gonz_91 on 2008-12-15
(maybe this was supposed to been in the gaming section. I was unsure, so I put it here. Please do not flame me)

Hi everyone!

There are less and less things hooking me to windows, they are so few I don't even run windows on my main computer.

The problem is one of those things: WoW.

So, I'll cut to the point: I copied the installation of a windows box, and did this:
> Open it [config.wtf] using a text editor, and add the following line to it:

SET gxApi "opengl"

If you experience poor performance, graphical glitches, or the game does not run at all, then add the following options as well:

SET ffxDeath "0"
SET ffxGlow "0"

Note that disabling ffxGlow may also enable antialiasing for some users.

If you experience a problem with missing character and object models, and/or the login windows background is black, add:

SET M2UseShaders "0"

And now the game started. Yay didn't last long, because after login, came this. (view screenshot)

For anyone who know the game, these are the Badlands, in the Eastern Kingdoms. Supposedly, they look like a desert, not like the surface of the sun.


So, what could this be? Maybe my graphics card is just bad?
I heard WoW runs on really low-end computers, and I've seen it running on computers just like mine, but with windows, so I'm supposing this is OS/user-related.


Any help would be appreciated :)

---

### Post by Gonz_91 on 2008-12-15
Bump





Anyone?

---

### Post by hikaricore on 2008-12-15
Patience young grasshopper.

Please allow 24-48 hours before bumping a post.
It never even left the first page of the WINE forum. :p

---

### Post by Gonz_91 on 2008-12-15
Sorry, sorry, o great master ;)



I'll be more careful in the future



:D

---

### Post by hikaricore on 2008-12-15
You replied just to bump your thread again :p

Stop that.

---

### Post by themusicalduck on 2008-12-15
Try running in d3d to see if you get the same problem?

SET gxApi "d3d"

---

### Post by Gonz_91 on 2008-12-16
Well, d3d actually made it better, for like 10 seconds. Then it started looking weird again, some textures disappeared, others got messed up.

:(


(ps:but thanks for your help anyway!)

---

### Post by pedro_orange on 2008-12-16
What version of WINE are you using?
What graphics card are you running?
What driver?
What does you xorg.conf look like?

Have you tried turning off Desktop effects etc?

---

### Post by Gonz_91 on 2008-12-16
Ok, turning off the desktop effects did the trick. The game now runs!


Heheh



Thank you 


*marks thread as solved*

---


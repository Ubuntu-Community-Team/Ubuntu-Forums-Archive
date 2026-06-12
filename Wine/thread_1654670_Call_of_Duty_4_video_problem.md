---
title: "Call of Duty 4 video problem"
date: 2010-12-28
forum: Wine
---

### Post by Mirror Shades on 2010-12-28
I installed Call of Duty 4 Modern Warfare through wine and game launches, menu works perfectly and everythings is fine, but when I start a mission my half of the screen shows blocks of pixels in wrong places, as if some of them were moved to the right of the screen. Left side of the screen shows video completely fine though. I remember I had this problem with World of Warcraft, but to fix it I had to make game run on opengl instead of directx. Maybe this is also the problem with this game? If so, how can I make Call of Duty 4 run on OpenGL (if it even supports it)? Or maybe there is other problem that needs to be solved? I am looking forward to your suggestions.

---

### Post by Aterus on 2010-12-29
I'm not sure what exactly causes the graphical problems, but if you want to take a shot at enforcing OpenGL, i presume this is how you do it:

Go in to console and type winetricks
Scroll down untill you find a function called "ddr=opengl" and tick it
Press OK

I think this is how you do it

If it doesn't help, you might want to come back in to winetricks to the same spot in the list and continue scrolling down. There are loads of other funtionings, such as enabling ad disabling multisampling etc. You might want to check them too and see if they make a difference.

---

### Post by Mirror Shades on 2010-12-30
Thanks for your suggestion.
"ddr=opengl" indeed made it work, but now the problem is, i cannot set resolution to my default one (1024x768), because game runs in fullscreen mode, but top and bottom menu panels still are there. And if i change resolution to that through config files, game once again becomes unplayable (same bug as before). Maybe you have more ideas about this?

---

### Post by Aterus on 2010-12-30
1024x768 - as i understand you are using a desktop PC and not a laptop, right?

---

### Post by Mirror Shades on 2010-12-30
Yes, I am using desktop PC + Ubuntu 10.04 32bit Desktop Edition. Wine version is 1.3.8

---


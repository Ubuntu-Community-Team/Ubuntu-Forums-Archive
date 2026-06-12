---
title: "Elder Scrolls IV: Oblivion graphics problem (screenshot inside)"
date: 2009-06-07
forum: Wine
---

### Post by DaftPyramid on 2009-06-07
I installed Oblivion with little trouble, and aside from some minor quirks (the game momentarily freezes when an enemy sees you), it worked quite well. I played the entire introductory level with no problems.

However, as soon as I stepped outside into the game world, I encountered a nasty graphics error. If I look in one direction, everything seems to be fine. But if I look in the other direction, all I see is a nasty pile of intersecting lines and polygons. 

See: [Screenshot]("http://i7.photobucket.com/albums/y299/mrhoeivo/Screenshot.png")

I know there have been threads about this game in the past, but they are long and contain mostly irrelevant information. If you know of a solution, or if you could link me to a specific thread or post that solves this problem, I would be very grateful. Thanks in advance.

Info: 
Wine 1.0.1
Ubuntu 9.04 32-bit (64-bit processor)
Nvidia 7600 GT (with appropriate drivers)

Aside: I've come across some posts regarding tweaks to the .ini and such. There was no file named Oblivion.ini in my game folder, only Oblivian_Default.ini. I created Oblivion.ini and changed the settings in both files, but I don't feel they took hold. For instance, I attempted to turn the opening cinematics off, but they still play. 

Also, I followed another post and created these strings in HKEY_CURRENT_USER/Software/Wine/Direct3D key in regedit:
DirectDrawRender | opengl
OffscreenRenderingMode | fbo
UseGLSL | enabled
VideoMemorySize | 256

Thanks again.

---

### Post by NightMKoder on 2009-06-07
Well most of those registry keys are defaults now, but whatever.

Get wine 1.1.23. 1.0.1 is just too old. [www.winehq.org/download/deb](www.winehq.org/download/deb)

---

### Post by DaftPyramid on 2009-06-07
Thanks for the quick response. 

I'm not sure if a Wine update will do much good, but I guess it couldn't hurt.

---

### Post by DaftPyramid on 2009-06-07
Wow. That totally fixed it. I can't believe it was that simple. Thank you very much. 

This thread now serves no purpose. I request it closed.

---

### Post by DaftPyramid on 2009-06-07
Scratch that. There's new problem.

Now, instead of momentarily freezing when I kill an enemy, most of the time the game crashes. 

Any tips?

---

### Post by DaftPyramid on 2009-06-07
Wow, sorry for the quadruple post here, but I've been doing some reading.

Apparently this is an issue with the fact that the music changes when you enter "battle mode." Most people seem to get around this by disabling music in the .ini.

But I have no Oblivion.ini!

This doesn't make much sense, but I don't have the .ini file, so I can't change any settings. Help?

---

### Post by oedipuss on 2009-06-07
The ini file should be located under your home dir, /home/user/My Games/Bethesda , or somewhere similar. 
I think wine sets the home folder as an equivalent for "Documents and Settings".

There's an easier way to disable music, though. Just rename the Music folder under oblivion/Data, to something else.

---

### Post by DaftPyramid on 2009-06-07
Thanks. I was looking in wine's c: drive, which has an Oblivion folder. The My Games folder contained the correct file.

---

### Post by u235sentinel on 2009-06-08
I have spent a considerable amount of time trying to make this work under Wine.  All versions of wine from 1.0.1 to 1.1.22.  It's painful and yes I've gone through the main howto's suggested in the wine.com/appdb.

This weekend I tried Crossover games 7.1.2 and 7.2.0.  7.1.2 had similar problems (such as the screen shot) however 7.2.0 has worked nearly perfectly since installing it.

Download and try their demo for a week and see if this resolves your issues.  I know it's not free however it does work and so far seems to work well.

Just a thought.

---

### Post by DaftPyramid on 2009-06-08
Thanks for the tip, but I've got it working flawlessly now. Good luck.

---


---
title: "WoW Login Screen/Window Probs with Ubuntu"
date: 2009-04-16
forum: Wine
---

### Post by lunanueva on 2009-04-16
Hello everyone, 

Like many people I would like to run WoW on my laptop without installing a windows partition.  I have read and done everything on the help.ubuntu.com/community/WorldofWarcraft page and have successfully installed the game.  However, when I click 'Play' I get the full login screen, **except** for the actual login window.  I've been through the forums searching for someone with a similar problem but was unable to find what I was looking for, so I posted here.  It seems as if I am very close to getting this game running, but I don't know where to go from here.  I would be very grateful for any assistance.  Thanks in advance for your help!

---

### Post by hikaricore on 2009-04-16
Video hardware/drivers?
Are you running the game in OpenGL mode?
Why are you running the game from Launcher.exe when you should be running WoW.exe direct?
Have you disabled desktop effects?
What terminal output do you get?

---

### Post by lunanueva on 2009-04-17
```
om glDrawElements @ drawprim.c / 49
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 49
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 49
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawElements @ drawprim.c / 49
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) fr
```

This is what I get in the terminal when I open the game, it repeats.  I am running off the wow.exe, just can't login cause there is no login window.

---

### Post by lunanueva on 2009-04-17
> Video hardware/drivers?
Are you running the game in OpenGL mode?
Why are you running the game from Launcher.exe when you should be running WoW.exe direct?
Have you disabled desktop effects?
What terminal output do you get?


yes, i am running in OpenGL, and through wow.exe, and my desktop effects are disabled.  my terminal output is in the reply above.

---

### Post by lunanueva on 2009-04-17
Any help would be appreciated!!!

---

### Post by alexandari on 2009-04-17
you`r runing it under wine right? 
here`s my Config.wtf file [http://www.turboupload.com/ez1pm9h4sst0/Config.wtf.html](http://www.turboupload.com/ez1pm9h4sst0/Config.wtf.html)
try replacing it with yours and dont forget to change the resolution to the one you want. and try runing it without opengl and see what happens :)

---

### Post by lunanueva on 2009-05-10
Cool.  Thanks alexandari.  I'm actually dual booting right now, but i still want to get this working with Ubuntu.

---

### Post by hikaricore on 2009-05-10
You still never mentioned what video hardware you have and if you properly configured/installed the drivers for it.

---


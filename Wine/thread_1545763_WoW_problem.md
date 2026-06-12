---
title: "WoW problem"
date: 2010-08-04
forum: Wine
---

### Post by reveger on 2010-08-04
Hi all...

Im trying to switch to linux - in my case its Jolicloud based on Ubuntu. But im experiencing straneg WoW problem.

In my case if i add  SET gxapi "OpenGL" to the config.wtf file when the game starts, everything is blurred, laggy or blacked out. If i start the game without this argument everything is ok.

But i read that the FPS will increase if i add that argument. I searched the forums but didnt find the solution.

Ive got really bad graphic card - intel gma945 but without opengl i can run it with 6-10FPS outside (warsong gulch eg) and without any problems inside.

Whats my problem with opengl? :)

---

### Post by hikaricore on 2010-08-04
With your current drivers and that "video" hardware you're more than likely not going to be able to run wow at a decent framerate.
The problem is probably the lack of proper opengl support for your hardware/drivers. You will either need to dual boot or buy a real video card.

Have you tried any of the bleeding edge Xorg/intel repos?  Some have had luck with these.

---

### Post by reveger on 2010-08-04
reporting that they cant ...i thought that getting d3d to work is harder than getting opengl to work :D...i get 15FPS without opengl...so with opengl i thought i could get a decent 20FPS...

well...im going to try a few other drivers...is there some command/benchmark which can tell me whether the problem is in drivers or smthing else?

---

### Post by stephlar on 2010-08-06
I am having a similar problem with an Intel card...  However, my game crashes if i have the openGL argument.

This is my post on the topic:

[http://ubuntuforums.org/showthread.php?t=1543870](http://ubuntuforums.org/showthread.php?t=1543870)

---


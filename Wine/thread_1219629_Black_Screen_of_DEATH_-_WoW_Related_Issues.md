---
title: "Black Screen of DEATH - WoW Related Issues"
date: 2009-07-22
forum: Wine
---

### Post by Incadescent on 2009-07-22
Alright, just so you guys know, I HAVE been lurking the forums. And I couldn't find any posts pertaining to my issue, if I missed a thread by some miracle, please post the link.

    My issue: I installed Wine (1.1.26, I believe), all went well, all went according to plan. I installed WoW, it ran fine, the installer popped up, all was good. I clicked play..and got the cinematic, all was good, ran fine (if not a bit slow). And then.. *drum roll*..a completely blank, black screen. I could hear the frost dragon sound thing, but absolutely nothing showed. There is no way to login. The only way I can close this black screen of death is by pressing ESC.

    Any specs you may need to figure out what's wrong will be happily provided..I..I've just been working on this for five days, you guys. I really need help. I've tried everything I can think of.

---

### Post by pedro_orange on 2009-07-22
> **Incadescent said:**
> Alright, just so you guys know, I HAVE been lurking the forums. And I couldn't find any posts pertaining to my issue, if I missed a thread by some miracle, please post the link.

    My issue: I installed Wine (1.1.26, I believe), all went well, all went according to plan. I installed WoW, it ran fine, the installer popped up, all was good. I clicked play..and got the cinematic, all was good, ran fine (if not a bit slow). And then.. *drum roll*..a completely blank, black screen. I could hear the frost dragon sound thing, but absolutely nothing showed. There is no way to login. The only way I can close this black screen of death is by pressing ESC.

    Any specs you may need to figure out what's wrong will be happily provided..I..I've just been working on this for five days, you guys. I really need help. I've tried everything I can think of.

Have you tried running it under OpenGL & D3D?
Quick way to do it is just to run it from a terminal as:

```
wine 'C:\Program Files\path\to\WoW.exe' -opengl
```

Post the output from the terminal for both opengl & d3d.

Presumably you've seen the big wiki post with all the tweaks etc. You should post your hardware as well, especially graphics card.

---

### Post by Incadescent on 2009-07-22
Lo and behold, I actually fixed it last night. Took me a couple of hours. I had to re-install my nVidia 9800 graphics card drivers, and when I started up (with the SET gxAPI "OpenGL") in my config.wtf, everything was good. I could see the login screen!

---


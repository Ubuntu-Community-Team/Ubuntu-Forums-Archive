---
title: "World of Warcraft: black and white screen."
date: 2009-07-14
forum: Wine
---

### Post by tye959 on 2009-07-14
I have Wine v.1.1.25 and successfully installed World of Warcraft into c:/Program Files/World of Warcraft. But I installed it by copying it in my window's partition and pasting it in program files (if that makes a difference.)

Anyway, I start the game and the launcher works just fine, but when the sign in screen comes up it's black and white, but don't get me wrong. It's not like black and white screened, there are just black and white spots throughout the screen. The sound works perfectly though. 

When I put in ```
 glxinfo | grep render 
```

I get ```
 direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2

```

Any ideas? Thanks.

---

### Post by themattbeballin on 2009-07-14
Have you made WoW run in OpenGL?

To do this, go to your WoW installation directory and go to the WTF folder and open the config file. 

Add this in anywhere in the document.

```
SET gxApi "OpenGL"
```

The reason you do this is because the Windows version of WoW uses DirectX as a default renderer. Since DirectX is a Windows product, you need to use OpenGL for linux.

---

### Post by themattbeballin on 2009-07-14
If that also doesn't work you might just not meet the requirements for OpenGL.

I know that probably doesn't make too much sense but I had issues running WoW in my GeForce FX 5200 in WoW because it ran OpenGL 1.4 instead of OpenGL 2.

---

### Post by tye959 on 2009-07-14
Okay, I set it to Open GL, and it's a little better. I can see everything and get to my character page. I didn't get past there because it was maintenance time. But here is a picture of what it looks like.[IMG]http://i28.tinypic.com/rt3k3a.png[/IMG] The moving things stick, as you can see.

---

### Post by themattbeballin on 2009-07-14
Hmmm..... Don't know what to tell you there. I have never had that issue.

---


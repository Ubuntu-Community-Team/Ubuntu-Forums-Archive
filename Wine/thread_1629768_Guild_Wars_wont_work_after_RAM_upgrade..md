---
title: "Guild Wars wont work after RAM upgrade."
date: 2010-11-24
forum: Wine
---

### Post by Zubb on 2010-11-24
Hey,

I'm running Ubuntu Maverick (10.10) and running Guild Wars through the latest Wine 1.3. Everything was working fine until I upgraded my RAM from 1 gig to 2 gig. Now I just get a black screen on login. I've tried changing the regedit, OffscreenRenderingMode = "backbuffer" but nothing is working. The only thing that works is when I got into the wine config and turn pixel shader off, this shows me the login screen and is a really good FPS but the game is unplayable because there is no chat menu and the graphics are awful.

Why is my new RAM change affecting the game to show a black screen?

My regedit;
DirectDrawRenderer = opengl
Multisampling = enabled
opengl = enabled
PixelShaderMode = disabled
RenderTargetLockMode = auto
UseGLSL = disabled
VideoMemorySize = 512

Please help me

~Jason

---

### Post by Woody1987 on 2010-11-24
Does the game still work if you put back in the old RAM?

---

### Post by Zubb on 2010-11-24
Yes it's just the RAM. but I have fixed it now :D
I turned off Pixel shading and turned the Graphics quality in GW's to the lowest and it works perfect :)

I'll mark as solved.

---


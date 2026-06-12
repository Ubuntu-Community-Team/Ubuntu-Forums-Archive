---
title: "Ghost Recon iPixelFormat"
date: 2009-07-01
forum: Wine
---

### Post by g3brownsc on 2009-07-01
Hey all

I'm trying to get Ghost Recon up and running in Wine, and I've had some luck so far, but I'm stuck. 

The game loads fine, but when I start an actual mission, the graphics render incorrectly. Surfaces don't get textured right, so patches of textures show up sometimes, but when I move the mouse to look around, most of the textures on the map disappear, leaving me staring at the skybox. 

Here's a picture:
[IMG]http://photos-c.ak.fbcdn.net/hphotos-ak-snc1/hs103.snc1/5018_1138059246845_1088280870_30779426_1954389_n.jpg[/IMG]

Errors from the terminal, cross-referenced to terminal feedback from somebody else's working copy, tells me this is messing me up:

```
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
```

A google search of this doesn't give me much to work with. 

My details-
Ubuntu 9.04 Jaunty
2 ghz, 2 mb ram
intel GMA X3100, GM965 card
This may or may not be relevant, but turning Compiz on/off has no effect on the graphics. 

Any help would be really appreciated, thanks in advance.

---

### Post by Th3_uN1Qu3 on 2009-07-02
I believe it doesn't like your GMA. That's what you get for going with Intel video... Try unchecking "Enable Pixel Shader" in Wine configuration.

---

### Post by g3brownsc on 2009-07-02
Thanks for the reply.

I already tried that, along with turning off vertex shader support; still no dice.
The game has worked before on this computer with other versions of wine/ubuntu, but it was so long ago that I don't remember which ones. 

I don't think this is just my graphics card misbehaving.

---

### Post by NightMKoder on 2009-07-02
It is, try offscreenrenderingmode=backbuffer. GMA's are notorious for misbehaving. I just hope gallium becomes a little more stable so we can have a little saner support.

---

### Post by g3brownsc on 2009-07-03
Thanks for the feedback. 

If I followed your advice correctly (unlikely), it did not work right. 

Here's what I did:
Opened regedit, navigated to 
HKEY_CURRENT_USER/Software/Wine/

Created a new folder, Direct3D
the key in that folder is now
Name: (Default)    Type: REG_SZ    Data: OffscreenRenderingMode=backbuffer

Sorry if I messed it up, I've just never done much registry editing. 

If I did do that right, which I'm not sure I did, it isn't the fix. This is an interesting problem, especially since it's worked before. 

Thanks for any more insight.

---

### Post by Th3_uN1Qu3 on 2009-07-03
The key's NAME should be OffscreenRenderingMode (not (Default)) and the VALUE (data) should be backbuffer. So rename that (Default) and in the Value screen leave only backbuffer.

---

### Post by g3brownsc on 2009-07-05
The editing area for (Default) is greyed out, so I can't change it. I can create a new key, but the default one would still be there. What should I do? Thanks for the help.

---

### Post by Th3_uN1Qu3 on 2009-07-07
Is this the first time you're messing around with the registry editor? I believe so, because the (Default) string has always been there, from Win95 on. You generally leave it alone.

Right click in the right-hand panel -> New -> String Value.

---

### Post by g3brownsc on 2009-07-07
Yeah, I've never messed around with registry stuff too much. I made the new key, leaving the default one alone, and fired up the game. No luck. 

Anything else that might fix it, or is there any more information that'd help diagnose the problem?

Thanks for all your help, sorry this is taking a while.

---

### Post by g3brownsc on 2009-07-16
Anyone? Any more information that'd help?

---


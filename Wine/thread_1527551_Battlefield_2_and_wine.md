---
title: "Battlefield 2 and wine"
date: 2010-07-09
forum: Wine
---

### Post by oleink on 2010-07-09
Hey I keep getting this error....

> Debug assertion failed!   
Version:  1.0.2442.0 Build date:2005-5-23 0:42 
Module:  RendDX9  
File:  c:\dice\projects\bf2\Code\BF2\RendDX9\Effect.cpp  Line:173  
Text:  Failed to set up technique roadcompiledFull in effect Shaders/RoadCompiled technique not found  Current confile:

---

### Post by oleink on 2010-07-09
Sorry I didn't have it written down right before

---

### Post by philinux on 2010-07-09
Moved to Wine forum.

---

### Post by asdfoo on 2010-07-09
> **oleink said:**
> Hey I keep getting this error....

Hey... which version of Wine do you have? open a terminal and type 'wine --version'

The most recent is wine-1.2-rc7.
To me it sounds like you don't have your video drivers installed correctly, if you have 64bit ubuntu you will need 32bit compat drivers installed alongside (as nvidia provides for example).

---

### Post by oleink on 2010-07-11
> **asdfoo said:**
> Hey... which version of Wine do you have? open a terminal and type 'wine --version'

The most recent is wine-1.2-rc7.
To me it sounds like you don't have your video drivers installed correctly, if you have 64bit ubuntu you will need 32bit compat drivers installed alongside (as nvidia provides for example).

Looks like I've got an older version: 1.1.42

---

### Post by oleink on 2010-07-14
honestly I don't think this is a wine problem which is why I originally didn't post it in wine

---

### Post by asdfoo on 2010-07-14
> **oleink said:**
> honestly I don't think this is a wine problem which is why I originally didn't post it in wine

did you update to a more recent version of Wine?

The second issue it could be is that you don't have correct video drivers installed, which could be the reason the game aborted with a mention of d3d9.

Which video card do you have?
(check the output of glxinfo)

---

### Post by oleink on 2010-07-15
> **asdfoo said:**
> did you update to a more recent version of Wine?

The second issue it could be is that you don't have correct video drivers installed, which could be the reason the game aborted with a mention of d3d9.

Which video card do you have?
(check the output of glxinfo)

I updated wine.  I have an integrated ati that doesn't require drivers

---

### Post by asdfoo on 2010-07-15
> **oleink said:**
> I updated wine.  I have an integrated ati that doesn't require drivers

haha, that's very amusing.

If you don't have any drivers then you don't have any proper OpenGL support which Wine uses for Direct3D graphics, hence the game fails to run.

So if you think it doesn't require drivers then you don't require to run the game.

---

### Post by oleink on 2010-07-15
> **asdfoo said:**
> haha, that's very amusing.

If you don't have any drivers then you don't have any proper OpenGL support which Wine uses for Direct3D graphics, hence the game fails to run.

So if you think it doesn't require drivers then you don't require to run the game.

thanks b_ you could have just said that. honestly I don't know much about wine because I don't really use it for anything at all.  It's just on my system being useless because I don't use windows applications at all anymore.  I've completely ditched windows... Plus I got this computer pretty much for free which is why it has an integrated card.  I wouldn't of spent money on something with an integrated card except for how much I spent on this-$90 for a new hard drive.  That explains why Cedega's site says they don't support integrated cards too because they use Wine coding

---


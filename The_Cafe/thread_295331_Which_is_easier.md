---
title: "Which is easier?"
date: 2006-11-07
forum: The Cafe
---

### Post by Wafflesomd on 2006-11-07
Idk, I'm sure its been thought of.

But what's easier:

Emulating directx, or actually embedding directx support into Linux.

IDK, I'm kinda bored.

---

### Post by TheRingmaster on 2006-11-07
porting to opengl

lol

---

### Post by DoctorMO on 2006-11-07
DirectX is a layer on top of the ati/intel/nvidia drivers which are all based on opengl.

I don ged it why stupid games companies don't make games in opengl anyway since it avoids an abstracted layer. strikes me a being lazy.

DirectX is heathen as far as programming it in wine, I've been debugging a DX3 issue for ages but it's just absurd the amount of complications and exceptions they've put in. without documenting most of them.

---

### Post by Wafflesomd on 2006-11-08
So directx is an extra layer?  Over already opengl drivers?!


Huh.

---

### Post by chaosgeisterchen on 2006-11-08
DirectX makes programming easer I assume. Calling functions of the graphics cards manually would be a more complex task to program.

Just wildly guessing.

---

### Post by DoctorMO on 2006-11-08
It's the processors (GPUs) to the graphics cards, OpenGL has been built and designed by the Graphics Chip makers as a graphics standard.

you didn't think it just came out of thin air did you.

DirectX does provide other things like Mouse, Keyboard, Joystick and a few other extras all bundeled into one include. sort of like SDL Game platform but with their own 3D jiggery pokery to make things dificult to cause vendor lock in.

---


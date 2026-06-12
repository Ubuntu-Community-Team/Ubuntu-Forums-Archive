---
title: "Guild Wars crashes on launch"
date: 2009-12-15
forum: Wine
---

### Post by BoneSmash on 2009-12-15
When I launch Guild wars I get an error saying "Unable to initialize 3D output.  Please verify that you have installed DirectX 8 and an updated video driver."  I've played Guild Wars before with Wine without any problems.  Can anyone help me?

---

### Post by beastrace91 on 2009-12-16
Has anything changed on your setup recently? What Wine version, what graphics card, and what driver version? Also do native 3D applications/games work fine on the system?

Regards,
~Jeff

---

### Post by BoneSmash on 2009-12-16
Identical hardware as before.  I took a break from Linux for a while and used Windows 7 for a few months, Guild Wars worked before, now it doesn't.  I can play the native Linux Heroes of Newerth client.

Wine 1.1.34
NVIDIA Driver 190.42

---

### Post by beastrace91 on 2009-12-16
What Wine version had you used before? I'm not personally aware of any issues with GW on the latest Wine version but some may exist, try reverting your version perhaps.

Also do you have any other 3D apps you could try through Wine to see if they work?

~Jeff

---

### Post by BoneSmash on 2009-12-16
Other games don't work either, but their installers do, so it seems to be a problem limited to DirectX.  When I tried to run Warcraft 3 I got this message "Warcraft III was unable to initialize DirectX.  Please ensure that you have DirectX 8.1 installed and that your display drivers are current."

This is the Wine console output from when I run Warcraft 3:

fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
err:ole:CoCreateInstance apartment not initialised
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:advapi:SetSecurityInfo stub
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D8 is not available without opengl
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D8 is not available without opengl

---

### Post by BoneSmash on 2009-12-17
I fixed it!  Apparently since I am running in 64-bit I had to install some lib32 NVIDIA files.  Thanks for all the help anyways though!

---

### Post by beastrace91 on 2009-12-18
> **BoneSmash said:**
> I fixed it!  Apparently since I am running in 64-bit I had to install some lib32 NVIDIA files.  Thanks for all the help anyways though!

Ahh, that will do it - thats why I asked if other applications where working :)

~Jeff

---

### Post by Bwathke on 2009-12-18
Sounds like your using a virtual machine. Try using just wine and make sure its not creating its own. Also you can add the flag -dx8 I did this and it helped the performance and it fixed alot of my issues. Hope this helped!

---

### Post by beastrace91 on 2009-12-18
> **Bwathke said:**
> Sounds like your using a virtual machine. Try using just wine and make sure its not creating its own. Also you can add the flag -dx8 I did this and it helped the performance and it fixed alot of my issues. Hope this helped!

Haha did you read the rest of his thread? Issue was needing to add the 32bit compatibility libraries on his 64bit system :)

~Jeff

---

### Post by jedipyro on 2009-12-23
Hey! I seem to be getting the same messages when i run left 4 dead 2. I also have a 64bit machine. what did you do to fix it?

---


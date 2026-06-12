---
title: "Sims 3 problems"
date: 2011-02-27
forum: Wine
---

### Post by misselain on 2011-02-27
Okay I have been very patiently trying through comments on the wine Sims 3 page to resolve the problem. I turn here in hopes that someone here will be able to help. Please note that I am extremely new to linux and more then a little hopeless. My mother though is good with it so she should be able to understand what you guys say.

Here's the problem. I added all the winetricks that were suggested.  The game installed and started up fine. I get through the opening video into the area where one would select a city. A box pops up before being able to select anything. It has no words but has two clickable buttons. The one on the right closes the program and the one on the left dose nothing. I did just a few minutes ago add the no cd/dvd crack but it has changed nothing.

Could someone please, _please_, help me. :cry:

---

### Post by cogadh on 2011-02-27
Run the game from the terminal and post Wine's error output, it might explain what is happening.

---

### Post by misselain on 2011-02-27
fixme:d3d:context_check_fbo_status      Location SFLAG_INTEXTURE (0x40).
fixme:d3d:context_check_fbo_status      Color attachment 0: (0x14fce0) WINED3DFMT_B8G8R8A8_UNORM 1024x768
fixme:d3d:context_check_fbo_status      Depth attachment: (0x1395a0) WINED3DFMT_D24_UNORM_S8_UINT 1024x768
err:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION (0x506) from glDrawElements @ drawprim.c / 43
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_UNSUPPORTED (0x8cdd
)
fixme:d3d:context_check_fbo_status      Location SFLAG_INTEXTURE (0x40).
fixme:d3d:context_check_fbo_status      Color attachment 0: (0x14fce0) WINED3DFMT_B8G8R8A8_UNORM 1024x768
fixme:d3d:context_check_fbo_status      Depth attachment: (0x1395a0) WINED3DFMT_D24_UNORM_S8_UINT 1024x768
err:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION (0x506) from glDrawElements @ drawprim.c / 43

This just goes on and on.

Sorry for the delay. Had some problems. My mother thinks there might be some problems with the graphics setting. The game now will start and function just all images and words are gone. Also now all the colours on my desktop are bolder and stronger, all the darks are darker and the lights seem lighter.

---

### Post by cogadh on 2011-02-27
What do you have for a video card?

---

### Post by misselain on 2011-02-27
Intel Graphics Media Accelerator 4500MHD

I did run windows 7 on this laptop previously and on it Sims 3 worked **perfectly** so I doubt it has anything to do with my hardware.

---

### Post by cogadh on 2011-02-27
You cannot compare how a game ran on Windows to how it might run on Linux. Linux is not Windows and while the hardware might be the same, the operating system, and more importantly, the hardware drivers, are completely different. That being said, the Linux drivers for Intel graphics hardware are pretty crappy. If you want to do any non-native gaming on Linux, you're really better of using a machine with an Nvidia graphics hardware solution (their drivers are great).

---

### Post by misselain on 2011-02-27
I understand that just because it runs under windows it doesn't have to run under linux. I merely wanted to say that the graphics processor and the game were compatible. However I am on a laptop so it's not like I can rip it open and slap a new one it. Probably should have said that earlier my mistake. That being said is there anything else to be done to remedy the situation? :|

---

### Post by misselain on 2011-02-28
Thanks for the help cogadh. 

If anyone else has suggestions on how to solve my graphics problem, without getting a new graphics processor, please do post here with your advise. To put the problem more clearly (I did try taking screen shots unsuccessfully) the game loads and runs perfectly fine. Unfortunately there are no words or moving images, which between those two is the game. Things like the dashboard and non moving images work fine. Thank you in advance for your help.

---

### Post by tigerblue on 2011-03-13
Have you installed driconf and set "Enable S3TC texture compression even if software support is not available" to "Yes" in the Image Quality section? Seems to be required with certain intel chipsets.

---


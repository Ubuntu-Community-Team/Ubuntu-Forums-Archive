---
title: "Help, can't run Warcraft III. undefined symbol: glConvolutionFilter1D"
date: 2009-12-26
forum: Wine
---

### Post by andile999 on 2009-12-26
Thx for reading guys!!!  ^_

So,
I am using Kubuntu 9.10 amd64 (I have AMD TurionX2 64). then I installed wine and warcraft III.

I can't run the game because there is some error that says, "Can't open game.dll".

And in the terminal,. there is this code.

```
andy@AndyKubuntu:~/Dokumente/.wine/drive_c/Programme/Warcraft$ wine war3.exe
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": /usr/bin/../lib32/wine/opengl32.dll.so: undefined symbol: glConvolutionFilter1D
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"H:\\Dokumente\\.wine\\drive_c\\Programme\\Warcraft\\Game.dll") failed (error c000007a).

```

What could be the problem? I have searched everywhere, but i cant find any guy that got the same error like me. There are case that are similiar to this, but it's not the same. 

What should I do? 

Thx in advance.

---

### Post by tolostoi on 2009-12-26
Maybe is good idea to try PlayOnlinux, works fine [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---


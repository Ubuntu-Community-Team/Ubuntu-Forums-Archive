---
title: "How do I install llvmpipe for New Unity Concept?"
date: 2012-08-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-08-16
Just picking up where effenberg left off. I have had the same problems. Tried to look for llvmpipe in synaptic. Haven't tried fresh install as of yet. Why do I need fresh install to enable this new Unity 3D?

---

### Post by effenberg0x0 on 2012-08-17
Hi Ventrical, I couldn't find much info about llvmpipe yet, running against time on work stuff. I think we will only have a lot of blogs, howtos,wiki, with detailed info about it after Ubuntu 12.10 is released and more people get to know about it. 

Here's all I know (or think I know) about it so far. Keep in mind I might be completely wrong :)

- Gallium llvmpipe has to provide some sort of libGLsomething.so for indirect rendering.
- libgl1-mesa-dri-experimental depends on libgl1-mesa-dri. libgl1-mesa-swx11 provides libgl1, libgl1-mesa-swrast, mesag3. It conflicts with nvidia-current, fglrx, etc. Looks like it.
- So it's not like you have to do a reinstall of the whole system. If you look at depends, rdepends and conflicts/breaks of libgl1-mesa-dri-experimental, you can't have in parallel of other GLX drivers.
- I think it's weird because I thought it would be a xserver-xorg-llvmpipesomething and we would be able to modprobe load and modprobe remove llvmpipe, so we would alternate between real GLX and indirect GL to test.
- I haven't looked at Jockey code, I think we need to see what's in the handlers. My guess is that if it detects a GPU that is not capable of OpenGL 2.0, or no GPU, it will apt-get libgl1-mesa-dri-experimental. If a GPU that is capable of OpenGL 2.0 is detected, the proper driver (nvidia-current, intel, fglrx, etc) is installed, and that removes libgl1-mesa-dri-experimental.
- I don't know if it needs a specific /etc/X11/xorg.conf but I will guess it does not. 
- Once you have it installed, you can use the same environment variables that are documented for previous mesa swrast to test it when running OpenGL (LIBGL_ALWAYS_SOFTWARE, LIBGL_DRIVERS_PATH). Example:
```
[08:36:36] ahsl@AL-DESK01:[/usr/lib]: LIBGL_ALWAYS_SOFTWARE=1 glxgears -info

```
- You can use glxgears (from mesa-utils package) to test if llvmpipe is being used. Look at the first 3 output lines (GL_RENDERER, GL_VERSION, GL_VENDOR). You can also test with /usr/lib/nux/unity_support_test -p from nux-tools package.
- **EDIT:** Maybe the faster way to test is to create a basic script/one-liner to stop lightdm, unload nvidia/ati/intel vga modules and blacklist them, install libgl1-mesa-dri-experimental, maybe test/fix some symlinks in /usr/lib/*GL* to point to llvmpipe. And undo it after testing. 
- **EDIT 2:** I have some old dusty laptops I can use to test this... I'll post results and more precise info as soon as possible.
- **EDIT 3:** Found a working HP Pavilion ZE2410 :) I'll test it later. It has a It has an ATI Radeon Xpress 200M, so I can script something to switch between the Open Source Radeon Driver and llvmpipe and compare performance. I think it's a viable test subject, considering llvmpipe is aimed at supporting older hardware.
 
That's all I got. It would be nice if others could add more info and correct me if I'm wrong in what I posted above.

Regards,
Effenberg

---

### Post by lucazade on 2012-08-17
Just tried the daily live cd on my Intel Gma500 netbook (it doesn't have 3D opengl extensions but only a KMS kernel driver and the fbdev/modesetting X driver without any accel).

Unity with llvmpipe works out of the box without any manual installation or tuning, just start the livecd and a standard Unity session with llvmpipe as backend is engaged.

Unfortunately everything is slow as hell and full of artefacts and graphical glitches, it is probably running at 1/2 frames for seconds.

On the same machine Quantal with Kde 4.9 is really fast and snappy...

---

### Post by effenberg0x0 on 2012-08-17
> **lucazade said:**
> Just tried the daily live cd on my Intel Gma500 netbook (it doesn't have 3D opengl extensions but only a KMS kernel driver and the fbdev/modesetting X driver without any accel).

Unity with llvmpipe works out of the box without any manual installation or tuning, just start the livecd and a standard Unity session with llvmpipe as backend is engaged.

Unfortunately everything is slow as hell and full of artefacts and graphical glitches, it is probably running at 1/2 frames for seconds.

On the same machine Quantal with Kde 4.9 is really fast and snappy...

Luca, I found a EeePC 4G here, it has a Intel GMA, I'll test it in that too. I think we will need to learn about xorg.conf specifics and compiz switches, in order to make the best out of llvmpipe. 

Regards,
Effenberg

---

### Post by dino99 on 2012-08-17
> **effenberg0x0 said:**
> 
- I haven't looked at Jockey code, I think we need to see what's in the handlers. My guess is that if it detects a GPU that is not capable of OpenGL 2.0, or no GPU, it will apt-get libgl1-mesa-dri-experimental. 

Jockey GTK has been superseded by software-properties, which now handles
third-party driver configuration.

You can safely remove this transitional package after upgrading.

---

### Post by lucazade on 2012-08-17
> **effenberg0x0 said:**
> Luca, I found a EeePC 4G here, it has a Intel GMA, I'll test it in that too. I think we will need to learn about xorg.conf specifics and compiz switches, in order to make the best out of llvmpipe. 

Regards,
Effenberg

If I remember correctly only the Asus EEEPC 1101ha and 1201ha shipped the Gma500, the other eeepc are Intel i915 based (so with a pretty decent 2D/3D accel driver).

About xorg switches I believe I cannot do anything else (maybe just force 16bit depth instead of 24bit, getting some more frames.. but nothing trascendental!).

Gnome shell with llvmpipe on fedora was a bit faster so probably we lack some different llvmpipe libs or it is just needed some compiz tuning.

---

### Post by lucazade on 2012-08-17
interesting benchmarks of unity and llvmpipe made by phoronix:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_unity2d_defenestrate&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_unity2d_defenestrate&num=1)

---

### Post by ronacc on 2012-08-17
I have an eeepc and I confirm it has I915 graphics ( a non standard setup as I recall but the ubuntu driver handles it ) .

---


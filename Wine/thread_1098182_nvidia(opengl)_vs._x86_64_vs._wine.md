---
title: "nvidia(opengl) vs. x86_64 vs. wine"
date: 2009-03-16
forum: Wine
---

### Post by xpatch on 2009-03-16
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7e7dcc46

I seem to get this error with every opengl chunk of code I try to run.
this only seems to happen on x86_64 archs. ( yes I've installed ia32 )

I've used winehq deb pkgs for ubuntu and followed the instructions.
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

I've dloaded and custom compiled several version of wine.
(used the  install-wine-deps.sh ) 

I have a feeling that this is a combination of nvidia drivers vs. wine vs. x86_64 arch's

I managed to get wow launcher working but as soon as opengl gets into the mix it falls over. I coded a simple opengl (using sdl) app and compiled it on windows works fine, same code compiles on linux and runs fine. attempt to use wine to run the windows version it explodes. I think it's during SDL_SetVideoMode(...) if SDL_OPENGL is passed into the flags param.

----- UPDATE -----

I was using nvidia's drivers off the nvidia website. This seems to have unpredictable results.
I attempted to use System -> Administration -> Hardware drivers to enable the one provided by ubuntu (Nvidia 173) was listed but that completely 
hooped my gdm so I had to boot to single user mode, tried to run NVIDIA's install to overwrite bad ubuntu 173 drivers.
Which didn't work either, I saw in the apt repository ubuntu nvidia 180.11 driver (which was closer version to nvidia's 180.29 that I was using)
gnome came back up but I had no glx until I manually. in both 32 and 64bit dirs resymlinked the right libGL.so.1 etc...

My guess is that you need to install nvidia drivers (manufacturer or ubuntu's) after installing the ia32 stuff so the libGL.so.1 gets linked properly for both arch's



root@sin:/usr/lib32# ls libGL*
libGLcore.so    libGLcore.so.180.11  libGL.la  libGL.so.1       libGL.so.180.29  libGLU.so.1
libGLcore.so.1  libGLcore.so.180.29  libGL.so  libGL.so.180.11  libGLU.so        libGLU.so.1.3.070200
root@sin:/usr/lib32# rm libGL.so.1
root@sin:/usr/lib32# ln -s libGL.so.180.11 libGL.so.1 
root@sin:/usr/lib32# ls -l libGL*
lrwxrwxrwx 1 root root       19 2009-03-16 17:27 libGLcore.so -> libGLcore.so.180.11
lrwxrwxrwx 1 root root       19 2009-03-16 17:28 libGLcore.so.1 -> libGLcore.so.180.11
-rw-r--r-- 1 root root 15074804 2009-01-06 13:13 libGLcore.so.180.11
-rwxr-xr-x 1 root root 15782884 2009-03-16 17:18 libGLcore.so.180.29
-rw-r--r-- 1 root root      655 2009-03-16 17:18 libGL.la
lrwxrwxrwx 1 root root       15 2009-03-16 17:27 libGL.so -> libGL.so.180.11
lrwxrwxrwx 1 root root       15 2009-03-16 17:47 libGL.so.1 -> libGL.so.180.11
-rw-r--r-- 1 root root   701784 2009-01-06 13:13 libGL.so.180.11
-rwxr-xr-x 1 root root   701784 2009-03-16 17:18 libGL.so.180.29
lrwxrwxrwx 1 root root       22 2009-03-16 14:42 libGLU.so -> /usr/lib32/libGLU.so.1
lrwxrwxrwx 1 root root       20 2009-02-17 21:20 libGLU.so.1 -> libGLU.so.1.3.070200
-rw-r--r-- 1 root root   460432 2008-10-21 20:54 libGLU.so.1.3.070200

---


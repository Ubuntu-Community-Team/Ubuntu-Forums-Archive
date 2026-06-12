---
title: "ubuntu on odroid XU (exynos 5)"
date: 2014-01-06
forum: Server Platforms
---

### Post by borgotretre on 2014-01-06
Hi!


After months of ubuntu on my dedicated x86 hw (for an specific application), i take an odroid xu (arm A15/A7 big.little octa core) and ported my application on it, but i have some issues:


1) pulseaudio does not work ( on ARM , kernel 3.4 and ubuntu 13.10) as on 13.10 with intel and official kernel. In particular, using ffmpeg to acquire through pulse audio ( ffmpeg -f alsa -i .... pulse) , I can not in any way by alsamixer switch between one source and another . It seems as if some devices were " locked" and can not be turned on and off to send the capture line or mic on stream recording of ffmpeg. My system is headless , so I have no way to use gui for managing the pulseaudio mixer and I have not found other mixers pulseaudio running on shell . Currently the process is started automatically by the user, when he launches mplayer inside Xvfb (in the framebuffer).




Could it be missing some kernel module or some package in order to have the opportunity into using pulseaudio as a real mixer with the ability to modify input-output on the fly by the user, without the need to save the default source ( which, moreover, i don't understand how i can do it) ?


2) using arch linux I have the same problems with pulseaudio and various other troubles, but I get through ffmpeg DOUBLE fps, so I suppose this is due to a different compilation of ffmpeg . You can link me some guide on how to compile ffmpeg on ARM with support for rtmp , rtsp and aac and h264 codec?

---


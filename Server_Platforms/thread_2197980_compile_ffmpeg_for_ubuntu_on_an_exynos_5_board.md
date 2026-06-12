---
title: "compile ffmpeg for ubuntu on an exynos 5 board"
date: 2014-01-06
forum: Server Platforms
---

### Post by borgotretre on 2014-01-06
Hi,

can someone explain me how i can obtain all i need to compile ffmpeg for my odroid-xu board (compile inside it, not cross-compile)?

I need h264,h263,aac,rtmp/rtsp,x11grab, profile support and cpu modules?

there is something specific to do for obtain best performance for ffmpeg on an exynos 5 soc, or is equal to compile ffmpeg for x86 and i can follow some guide to compile ffmpeg on an x86 machine?

---

### Post by FakeOutdoorsman on 2014-01-06
> **borgotretre said:**
> can someone explain me how i can obtain all i need to compile ffmpeg for my odroid-xu board (compile inside it, not cross-compile)?
I do not have any ARMv7-a devices but I do not see why you could not compile on it. Refer to the ARMv7a builds at [FATE](http://fate.ffmpeg.org/) for examples of what configure options were used. Perhaps something like:
```
./configure --enable-gpl --enable-x11grab --enable-libx264 --cc='ccache gcc-4.6' --extra-cflags='-mfpu=neon' --cpu=cortex-a7
```
You will need the dependencies for x264 and x11grab. See [How To Compile FFmpeg and x264 on Ubuntu](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) for additional ideas.

> **borgotretre said:**
> I need h264,h263,aac,rtmp/rtsp,x11grab, profile support and cpu modules?
Please be more specific. Do you need only decoding support or encoding as well for H.264 and AAC?

---


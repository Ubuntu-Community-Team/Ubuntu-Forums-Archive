---
title: "The Sims 3 Video Errors"
date: 2010-04-04
forum: Wine
---

### Post by Glunn11 on 2010-04-04
Hello Ubuntu Forums! :)

I have recently installed The Sims 3 and its expansion pack, World Adventures, and patched them both to the most recent versions manually (1.11.7/2.6.11) through PlayOnLinux. When I try to start the World Adventures executable, I am given the following error message:

```
Unable to start game.

Device 0 cannot run this title.
No supported graphics card detected. Please check your system hardware.

```

When I look in the terminal for clues, I get this message:
```

Checking python : 				[ Ok ]
Running The Sims 3 World Adventures
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:593:(snd_pcm_dsnoop_open) unable to open slave
fixme:win:EnumDisplayDevicesW ((null),0,0x32eaa4,0x00000000), stub!

```

I have an NVIDIA 8400 GS graphics card that is currently using the version 185 driver, as is recommended.

Any help is greatly appreciated. Thank you for your time! ;)

---

### Post by turbos4 on 2010-04-05
Try download the driver from nvidia.

[http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

---

### Post by Glunn11 on 2010-04-05
Well, I downloaded the newest drivers from NVIDIA (195) as recommended. They are working, as nvidia-settings says, but the game still says the same thing.

---

### Post by asdfoo on 2010-04-05
which version of Wine are you using? 1.1.42 is the newest

please attach terminal output also

---

### Post by Glunn11 on 2010-04-06
I'm currently using Wine 1.1.41. 
Also, my terminal output from PoL is this:
```

PlayOnLinux v3.7.3

Checking python : 				[ Ok ]
PlayOnLinux repository need to be updated
Running The Sims 3 World Adventures
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
fixme:win:EnumDisplayDevicesW ((null),0,0x32eaa4,0x00000000), stub!

```

---

### Post by smd0665 on 2010-06-23
Has anyone gotten this to work? I had The Sims 3 working just fine on the same hardware, but then had to reinstall the OS. Now, I'm getting the same graphics error that Glunn11 is getting. Nvidia seems to be working okay.

glxinfo | grep rendering
direct rendering: Yes

---

### Post by smd0665 on 2010-06-24
I was able to get mine working again. For me, I needed the lib32 libraries (I'm running amd64).

---


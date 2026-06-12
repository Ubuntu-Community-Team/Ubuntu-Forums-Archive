---
title: "Counter Strike: Condition Zero crash on connecting to a server"
date: 2009-05-24
forum: Wine
---

### Post by Bensky on 2009-05-24
Hi all. I started using Ubuntu 9.04 yesterday and everything appears to be working fine with Wine except for Counter Strike: Condition Zero. Something seems to be wrong with PulseAudio and Wine, as I'm getting the following error followed by a Windows-esque messagebox saying "hl.exe has encountered a problem and needs to close, to report this blah blah blah."

This is encountered during the "precaching resources" stage of connecting to a game:
```
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: memblock.c: Assertion 'b' failed at pulsecore/memblock.c:438, function pa_memblock_acquire(). Aborting.

```

I've already seen a bug on launchpad related to this, but I'm just wondering if anyone has a solution. I really don't want to REMOVE pulseaudio as it works fine for everything but Wine, and I don't want to break my sound by trying to remove something that seems like its part of the ubuntu-desktop package.

Any help is appreciated.

Bensky

---

### Post by Bensky on 2009-05-24
Hmm, a little progress.

I disabled the auto spawning of the pulseaudio process in client.conf, then did a "killall pulseaudio" - I noticed my volume level shot way down, but this time when I launched Condition Zero I actually got in to the game. I hit ok to join a team, picked Counter Terrorist, noticed some sounds and players moving around, then the game just completely froze and kept playing the same sound over and over. I had to do a hard shutdown to get out of it.

Is there a better solution?

---

### Post by NightMKoder on 2009-05-24
just remove pulseaudio. It is not compatible with wine. Once removed make everything work with alsa instead and all will be well.

---

### Post by Bensky on 2009-05-24
> **NightMKoder said:**
> just remove pulseaudio. It is not compatible with wine. Once removed make everything work with alsa instead and all will be well.

How do I do this?

Earlier I tried the usual "sudo aptitude remove pulseaudio" but I got some messages saying "ubuntu-desktop" would be broken and some other random things would be removed, so I pressed "q" to quit out of it. Is this the proper way to remove it? Should I have continued?

---

### Post by NightMKoder on 2009-05-24
Yep, just continue. ubuntu-desktop is a meta package, doesn't actually have anything in it.

> 
If you decide you no longer like PulseAudio and would like to disable it: Remove the added lines to /etc/asound.conf If /etc/asound.conf did not exist when you installed PulseAudio, you may remove /etc/asound.conf entirely.

After this, you may remove all of the installed PulseAudio packages. 

---

### Post by Bensky on 2009-05-24
> **NightMKoder said:**
> Yep, just continue. ubuntu-desktop is a meta package, doesn't actually have anything in it.

I don't have a /etc/asound.conf apparently. I also did a "find / -name 'asound.conf'" and that turned up nothing. I guess I'll go ahead and just remove it.

---

### Post by Bensky on 2009-05-24
More problems.

Pulseaudio was removed completely. That part was fine. I then tried to launch Condition Zero again. This time it completely loaded and started the game, then when I picked "Counter Terrorist" for team it froze again. That was fixed by setting the game to run in Windows 98 mode. I was then able to play at around 20 FPS, which was somewhat playable. However, I started getting random crashes every few minutes. Sometimes I can't even spawn before it crashes and locks up my whole system.

I have an ATI card (ATI Radeon 9600 XT), which I'm guessing is the main problem since I've heard of a bunch of other people with the same problem. I also don't think I'm using the right driver. Most people seem to have flgrx and I have something else. I can't even find the restricted drivers program.

glxinfo:

```
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.4
```

---

### Post by mikezila on 2009-05-24
> **Bensky said:**
> ....I have an ATI card (ATI Radeon 9600 XT)....

Found your problem.

You're not using the actual 3D driver.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by Bensky on 2009-05-28
> **mikezila said:**
> Found your problem.

You're not using the actual 3D driver.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

That driver did not support the kernel version I had for some reason - it gave me an error message about something not being compatible after I unpacked it. Thanks anyway. I've moved back to Windows XP for now, I'll wait until I get a new computer with a NVIDIA video card to try this again, ATI + Linux = too much hassle

---

### Post by mossman44 on 2009-05-28
Having problems installing the ATI driver? Most likely, you don't have the pakages the installer needs installed. The necessary packages can be found in the driver readme. Also this website has helpful information about properly installing the drivers:
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by Bensky on 2009-05-28
> **mossman44 said:**
> Having problems installing the ATI driver? Most likely, you don't have the pakages the installer needs installed. The necessary packages can be found in the driver readme. Also this website has helpful information about properly installing the drivers:
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Thanks for the info, but:

"Which cards does ATI no longer support? The ATI Radeon 9500-9800,X300-X2100,Xpress. See the complete list [1] here. If your card is on that list, you are restricted to the 9.3 driver - however since 9.3 driver doesn't support xorg-xserver 1.6, it will not work with Jaunty! This guide currently is for installing 9.5. !!!SO BE CAREFUL!!! "

I have an ATI Radeon 9600 XT, so I won't be able to use this guide or any of the drivers on ATI's site because the ones that WILL work with my graphics card don't support xorg-xserver 1.6 apparently (at least according to this guy) :(

---


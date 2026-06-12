---
title: "Wine freetype problem"
date: 2009-06-21
forum: Wine
---

### Post by Tjaalie on 2009-06-21
Since wine 1.2.23 which is in the repository doesn't support my games installers and I don't want to revert back to version 1 I decided to build wine myself. I did this many times before and I never had a problem with it on ubuntu 8.10 x64. But now with 9.04 it won't work any more since it can't find the freetype library. The weird thing is when I go to the directory '/usr/lib32/' libfreetype.a is there. I tried to add it to the library search path manually with no succes. Here is a part of the configure output that contains the info about the error.

```

checking for sane/sane.h... yes
checking for -lsane... libsane.so.1
checking for gphoto2-config... gphoto2-config
checking for gphoto2-port-config... gphoto2-port-config
checking gphoto2-camera.h usability... yes
checking gphoto2-camera.h presence... yes
checking for gphoto2-camera.h... yes
checking for gp_camera_new in -lgphoto2... yes
checking for cmsOpenProfileFromFile in -llcms... yes
checking for freetype-config... freetype-config
checking for -lfreetype... not found
configure: error: FreeType 32-bit development files not found. Fonts will not be built.
Use the --without-freetype option if you really want this.

```

Now I can disable freetype and it works but there must be a reason freetype is included? Won't it make fonts ugly or something?

---

### Post by ackanao on 2009-06-21
Just do: --without-freetype you'll still have fonts despite that error. This links may help you:

[http://forum.winehq.org/viewtopic.php?t=5102&highlight=freetype]("http://forum.winehq.org/viewtopic.php?t=5102&highlight=freetype")

[http://wiki.winehq.org/Recommended_Packages]("http://wiki.winehq.org/Recommended_Packages")

[http://wiki.winehq.org/WineOn64bit]("http://wiki.winehq.org/WineOn64bit")

---

### Post by NightMKoder on 2009-06-21
Doesn't support your game's installers? That's new. There is a known (not-really-issue) issue with games on bad graphics cards. If that's your problem, set offscreenrenderingmode = backbuffer. Wine changed this behavior at 1.1.23.

As for compiling wine - follow the directions for wine on 64 bit from winehq.

---

### Post by ackanao on 2009-06-21
> **NightMKoder said:**
> Doesn't support your game's installers? That's new.

Yeah, new and introduced with Wine 1.1.23 - there's something annoying with this version that makes some installers to fail - it's fixed by new commits in Git and I expect it's fixed in new version of Wine (1.1.24) also.

---

### Post by Tjaalie on 2009-06-23
I never got it to compile with freetype but since there is a 1.1.24 version ubuntu package there is no need any more. But thanks anyway for all the responses. That is the reason I post on the ubuntu forums, people actually try to help others here.

---


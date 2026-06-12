---
title: "VMPlayer linpng12.so.0 issues"
date: 2006-10-09
forum: Server Platforms
---

### Post by davidsampson on 2006-10-09
So, I have a good install of vmplayer, and it worked great.  Then suddenly, I try running it and get:
```

/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)

(vmplayer:11439): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
vmplayer: Too many arguments; only one virtual machine can be specified at a time.
Try 'vmplayer --help' for more information.

```

Does anybody know why?

---

### Post by mr_fong on 2006-10-09
Same here, only my error message is different:

hans@athlon2500:~$ vmplayer /home/hans/vm-winXP/winXP.vmx
/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
kde-config: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)
kde-config: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)

Annoying as hell as I need a winXP-vm to connect to my schoolnetwork. I reinstalled vmware-player and went back to kernel 2.6.15-26, but to no avail. Anyone a solution, please!!!

Hans

---

### Post by davidsampson on 2006-10-09
Ok, try sudo-ing it.  It still gives the error message, but it will run.

Now, I get:

```
Failed to initialize OpenGL.
/usr/lib/vmware-player/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6).
The 3-D features of the display card will be disabled.
```

It still runs, but is annoying, and I can't use any games or whatnot on XP, as they require 3d...

Apparantly, this problem occurs quite often, but I have yet to find a way to correct that.  GCC 4.2 isnt out yet, is it?

---

### Post by mr_fong on 2006-10-09
You are luckier than I am: even when sudo-ing it still doesn't work. --Hans

---

### Post by davidsampson on 2006-10-09
[http://www.ubuntuforums.org/archive/index.php/t-195102.html](http://www.ubuntuforums.org/archive/index.php/t-195102.html)

Read this, it might help. :)

---

### Post by mr_fong on 2006-10-10
I gave up: searching through the forums I also discovered issues with libhal and libdbus. I'll dual boot for now and wait until this gets sorted out. --Hans

---


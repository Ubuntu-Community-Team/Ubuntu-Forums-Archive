---
title: "lil last WoW weirdness"
date: 2008-12-03
forum: Wine
---

### Post by Ixonal on 2008-12-03
OK, so got most things working, and this isn't really TOO much of a problem, just annoying really... Whenever I close out of WoW normally, I can't run it again until I restart my x server (when it crashes I can restart it again). 

when running it in the console, I get these results:
```

ixonal@Reinverka-II:~$ wine /home/ixonal/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe -opengl
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  146
  Current serial number in output stream:  146
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7e9167c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0x7e91696e]
#2 /usr/lib/libX11.so.6 [0x7ea13619]
#3 /usr/lib/libX11.so.6(XESetCloseDisplay+0x44) [0x7e9f5294]
#4 /usr/lib/libGL.so.1 [0x7e97fdb9]
#5 [0x7cd688b8]

```

---

### Post by Ixonal on 2008-12-04
no ideas?

---

### Post by hikaricore on 2008-12-04
Looks like a driver issue just from the X error.

Please run:

> glxinfo | grep rendering

And post the results here.  Also could you tell us what type of video hardware you have?

---


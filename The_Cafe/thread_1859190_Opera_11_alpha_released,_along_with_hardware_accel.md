---
title: "Opera 11 alpha released, along with hardware acceleration"
date: 2011-10-13
forum: The Cafe
---

### Post by Quadunit404 on 2011-10-13
[http://my.opera.com/desktopteam/blog/2011/10/13/introducing-opera-12-alpha](http://my.opera.com/desktopteam/blog/2011/10/13/introducing-opera-12-alpha)

One of the most requested features for Opera since Internet Explorer 9 was announced to use hardware accelerated browsing, just that, has been added to Opera as of 12 alpha. I'm using it right now and HWA works beautifully on my nVIDIA GT 330M :D

Right now, only OpenGL is supported, but on Windows Opera will support DirectX 9 and 10 as well. Also, be aware that as this is an initial build, your mileage may vary. People have reported issues such as laggy scrolling and page and window rendering being blurry (fun fact: the entire window is drawn by your GPU.) Also, not all graphics card work; check opera:gpu to see if your browsing is being accelerated by your hardware. Ones with buggy drivers and poor OpenGL support (remember, this initial build supports only OpenGL) are blacklisted while cards with proper OGL support are not. If you experience issues with a supported card, disable hardware acceleration in opera:config. I wish all of you the best of luck with Opera's HWA implementation :D

*Update: Now reads Opera 12 rather than Opera 11. Thanks for pointing out my mistake Npl.*

---

### Post by wolfen69 on 2011-10-13
I'll stay away from it for now.

---

### Post by Npl on 2011-10-13
its opera **12**, and appart from some graphic demos running faster I dont see much difference, except regular stuttering with scrolling and such.
its also subject to the same crash-the-whole-OS issues, since its supporting WebGL now (different thing than hwa rendering, like IE has hwa rendering but no WebGL support).

gonna be a while before this is actually helping rather than hurting.

---

### Post by Claus7 on 2011-10-13
Hello,

...yet it is an indication on where things are going?

Regards!

---

### Post by Quadunit404 on 2011-10-13
> **Npl said:**
> its opera **12**, and appart from some graphic demos running faster I dont see much difference, except regular stuttering with scrolling and such.
its also subject to the same crash-the-whole-OS issues, since its supporting WebGL now (different thing than hwa rendering, like IE has hwa rendering but no WebGL support).

gonna be a while before this is actually helping rather than hurting.

Dammit #-o

Fixing right now.

---

### Post by FuturePilot on 2011-10-13
Opera being late for a change

---

### Post by Quadunit404 on 2011-10-13
> **FuturePilot said:**
> Opera being late for a change

They were also late with extensions; those weren't introduced until Opera 11.

Also, for those of you who DO decide to jump to this new build and are having issues with hardware acceleration, go to opera:config, search for hardware, set "Enable Hardware Acceleration" to 0. The same goes for WebGL if you don't want to use that either, just replace "hardware" with "webGL"

---


---
title: "Firefox better under WINE than running nativly"
date: 2010-01-18
forum: The Cafe
---

### Post by adeypoop on 2010-01-18
i just found this link which surprised me. 

[http://www.favbrowser.com/windows-vs-linux-firefox-firefox-wine-and-opera/](http://www.favbrowser.com/windows-vs-linux-firefox-firefox-wine-and-opera/)

firefox is supposed to perform better in windows than linux, not only that it seems it's faster when running the windows one with WINE!?

just wondering what peoples thoughts are on this?

---

### Post by phrostbyte on 2010-01-18
Those benchmarks are pretty old, I doubt it's true for V8 anymore.

I did some more recent benchmarks:
[http://ubuntuforums.org/showthread.php?t=1365791](http://ubuntuforums.org/showthread.php?t=1365791)

Indeed Firefox's JS performance on Wine is better. I'm pretty sure the big performance gap is because 64-bit Firefox 3.5 and below lacks a JIT'er. There might be other reasons however.

However, Firefox on Linux is beating Windows on graphics performance, which is kind of unusual (we are trained to think Xorg is primitive). Well it's only unusual until you realise Firefox on Windows renders to a GDI surface, and GDI has no hardware acceleration. Windows is doing 100% software rendering.

---

### Post by adeypoop on 2010-01-19
phew don't think i'll run to install firefox on wine just now then. thanks for the informative response

---

### Post by The Toxic Mite on 2010-01-19
FYI, I find that Firefox performs better on Linux than Windows ;)

---

### Post by Xbehave on 2010-01-19
> **phrostbyte said:**
> Indeed Firefox's JS performance on Wine is better. I'm pretty sure the big performance gap is because 64-bit Firefox 3.5 and below lacks a JIT'er. There might be other reasons however.
Doesn't it have a JIT'er just it lakcs hand optimised asm? The other weakness is the linux version doesn't get PGO (personally I think canonical should PGO it in their builds), this is party due to bugs and partly because gcc PGOs are harder than MSVC.

---


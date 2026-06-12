---
title: "Downloads: Minefield PGO Builds"
date: 2009-04-25
forum: The Cafe
---

### Post by adamlau on 2009-04-25
These are not installers, but rather standard Mozilla packages. 
Simply extract the contents of the package and run the firefox script (not firefox-bin). 
Built for portability with safe optimizations, XULRunner independent.

**Pentium M [Centrino] [color=#0000FF](Linux)[/color]**
**File:** [[color=purple]http://www.adista.net/http/PM/firefox-3.0.10.en-US.linux-i686.tar.bz2[/color]](http://www.adista.net/http/PM/firefox-3.0.10.en-US.linux-i686.tar.bz2)
**SHA1:** 3b04cd5a6b68707173a3d236c49e2d763bb973d5
**MD5:** 453b65fbd0eb27fea8f620ce3cc915d9

**Pentium 4 HT [Prescott] [color=#0000FF](Linux x86_64)[/color]**
**File:** [[color=purple]http://www.adista.net/http/P4/firefox-3.0.10.en-US.linux-x86_64.tar.bz2[/color]](http://www.adista.net/http/P4/firefox-3.0.10.en-US.linux-x86_64.tar.bz2)
**SHA1:** 1cb7e24e7375f012e16312319172dafdd25f9070
**MD5:** b6b08d5fd9d22f94c6864e9bc8ab4e3b

**Intel Core 2 Duo  [color=#0000FF](Linux x86_64)[/color] [color=red]Coming Soon[/color]**
**File:** 
**SHA1:** 
**MD5:** 

**AMD Athlon X2  [color=#0000FF](Linux x86_64)[/color]**
**File:**  [[color=purple]http://www.adista.net/http/X2/firefox-3.0.10.en-US.linux-x86_64.tar.bz2[/color]](http://www.adista.net/http/X2/firefox-3.0.10.en-US.linux-x86_64.tar.bz2)
**SHA1:** 8e361edfd8b39f2ee8d4bce7f24e24e7c1c49f88
**MD5:** d35313d2c95ca97af087963e9920dbca

export CFLAGS="-march=native -O2 -fomit-frame-pointer -Wl,--as-needed,--hash-style=gnu,--sort-common"
export CXXFLAGS="-march=native -O2 -fomit-frame-pointer -Wl,--as-needed,--hash-style=gnu,--sort-common"
ac_add_options --enable-application=browser
ac_add_options --enable-profile-guided-optimization
ac_add_options --enable-jemalloc
ac_add_options --enable-strip
ac_add_options --disable-debug
ac_add_options --disable-tests
ac_add_options --disable-logging
ac_add_options --disable-optimize
ac_add_options --disable-crashreporter
ac_add_options --disable-javaxpcom
ac_add_options --without-system-nspr
ac_add_options --without-system-zlib
ac_add_options --without-system-jpeg
ac_add_options --without-system-png
ac_add_options --enable-crypto
mk_add_options MOZ_CO_PROJECT=browser
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-@CONFIG_GUESS@
mk_add_options PROFILE_GEN_SCRIPT='$(PYTHON) $(MOZ_OBJDIR)/_profile/pgo/profileserver.py'

See also: [Portable Minefield (Firefox) 3.0.10 PGO (w/o Java) Builds](http://forums.mozillazine.org/viewtopic.php?f=42&t=863455&p=6312455#p6312455)

---

### Post by sports fan Matt on 2009-04-25
If im  running a  Lenovo IdeaCenter K Series K2.3  Pentium dual-core E2180(2.00GHz) 3GB DDR2 500GB Intel GMA 3100 Desktop which archieture should i choose?

---

### Post by adamlau on 2009-04-25
If you happen to be running Ubuntu 32-bit: **Portable Minefield 3.0.9 PGO built against Pentium M [Centrino] [color=#0000FF](unfortunately w/o SSE3)[/color]**
If you happen to be running Ubuntu 64-bit: **Portable Minefield 3.0.9 PGO built against Intel Core 2 Duo [color=#0000FF](preferred w/ SSE3)[/color]**

---

### Post by xir_ on 2009-04-25
> **adamlau said:**
> If you happen to be running Ubuntu 32-bit: **Portable Minefield 3.0.9 PGO built against Pentium M [Centrino] [COLOR=#0000ff](unfortunately w/o SSE3)[/COLOR]**
If you happen to be running Ubuntu 64-bit: **Portable Minefield 3.0.9 PGO built against Intel Core 2 Duo [COLOR=#0000ff](preferred w/ SSE3)[/COLOR]**

nice thread just got the centrino one to work on my eee, its very cool and opens slightly more snappy even from a pen drive

---

### Post by adamlau on 2009-05-02
Updated, this time w/o Java dependencies :) .

---


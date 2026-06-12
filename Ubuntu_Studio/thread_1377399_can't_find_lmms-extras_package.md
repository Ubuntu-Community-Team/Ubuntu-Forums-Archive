---
title: "can't find lmms-extras package"
date: 2010-01-10
forum: Ubuntu Studio
---

### Post by djzoid on 2010-01-10
title says it all, where the hell can i get the lmms-extras package? im using intrepid ibex and tried the tobydox PPA but it just isn't there. i want to use zynaddsubfx which is in the extras package, i compiled lmms myself from a tarball but it didn't include the extras package. 

is there a way of putting zynaddsubfx into lmms withoput extras or where can i get extras from?

thanks for any help.

---

### Post by AutoStatic on 2010-01-10
Hello djzoid, lmms-extras has been merged with lmms:
```
jeremy@soushi:~$ aptitude show lmms
Package: lmms
State: installed
Automatically installed: no
Version: 0.4.6~ppa-3
Priority: optional
Section: sound
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 8,249k
Depends: lmms-common (= 0.4.6~ppa-3), libasound2 (> 1.0.18), libc6 (>= 2.7), libfftw3-3, libfluidsynth1, libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libice6 (>= 1:1.0.0),
         libjack0 (>= 0.116.1), libogg0 (>= 1.0rc3), libpulse0 (>= 0.9.19), libqt4-xml (>= 4.5.1), libqtcore4 (>= 4.5.1), libqtgui4 (>= 4.5.1), libsamplerate0, libsdl1.2debian (>= 1.2.10-1), libsm6,
         libsndfile1, libstdc++6 (>= 4.4.0), libstk0c2a, libvorbis0a (>= 1.1.2), libvorbisenc2 (>= 1.1.2), libvorbisfile3 (>= 1.1.2), libx11-6, libxext6, libxft2 (> 2.1.1), zlib1g (>= 1:1.1.4), stk
Recommends: tap-plugins, caps, lmms-vst
Suggests: fil-plugins, mcp-plugins, omins, vcf, freepats
Conflicts: lmms-extras (<= 0.4.3)
Replaces: lmms-extras (<= 0.4.3)
```

Which version are you using now?

---


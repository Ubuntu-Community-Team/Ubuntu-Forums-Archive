---
title: "tuxpaint hang on exit (&amp; other other tux SDL apps)"
date: 2010-02-02
forum: System76 Support
---

### Post by jpv on 2010-02-02
tuxpaint sound would only work for a few seconds, and then it would hang on exit on my brand new Pangolin running S76 stock Karmic 64-bit.  The fix is easy, and is also mentioned in [http://ubuntuforums.org/showthread.php?t=1335841](http://ubuntuforums.org/showthread.php?t=1335841) "3. Problems with SDLMAME/GMAMEUI."

**_Details:_**
[INDENT][http://www.tuxpaint.org/docs/known_issues/](http://www.tuxpaint.org/docs/known_issues/)
    Tux Paint 0.9.21 (June 2009)
    [...]
    Linux ()
    No sound, too much CPU usage, and/or freeze or crash on exit

    The ALSA sound backend in SDL has problems working with the PulseAudio sound system. Install SDL built against PulseAudio instead of ALSA (which is the default for SDL on Debian and Ubuntu). For example, on Ubuntu or Debian, install the "libsdl1.2debian-pulseaudio" package. (See Bug #269082 at Ubuntu Launchpad: 'tuxpaint and other tux SDL driven apps slow down and/or freeze thin client terminals (ltsp)')

    [https://bugs.launchpad.net/ubuntu/+source/tuxpaint/+bug/269082](https://bugs.launchpad.net/ubuntu/+source/tuxpaint/+bug/269082)
[/INDENT]

**_Fix:_**
```
$ sudo aptitude install libsdl1.2debian-pulseaudio
The following NEW packages will be installed:
  libsdl1.2debian-pulseaudio 
The following packages will be REMOVED:
  libsdl1.2debian-alsa{a} 
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 211kB of archives. After unpacking 0B will be used.
```

As far as I can tell after a couple of weeks with the fix, there is no down-side.  Thomas might want to look into passing that along to R&D for the stock image.

---


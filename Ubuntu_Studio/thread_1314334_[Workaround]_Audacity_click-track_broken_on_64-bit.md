---
title: "[Workaround?] Audacity click-track broken on 64-bit"
date: 2009-11-04
forum: Ubuntu Studio
---

### Post by personman_ on 2009-11-04
Hello all,

I've had a problem for as long as I can remember where features of audacity dependent on nyquist (like the click track) don't seem to work properly on 64-bit linux. (at least under *ubuntu and debian, from my experience)

I created an attempted workaround to enable users to run the 32-bit version on 64-bit *ubuntu. It essentially consists of a package that installs the required 32-bit lib dependencies for *ubuntu 9.10.

I'd currently recommend it only to experienced users until I get more feedback on it, but so far results seem pretty good.

There are a couple issues: For LADSPA plugins or LAME exporting, you will need 32-bit versions installed under /usr/lib32 

Other than that though, it seems pretty solid. Recording and click track works, exporting to flac and ogg works.

If you'd like to give it a shot, check out [_this thread_](http://forum.audacityteam.org/viewtopic.php?f=18&t=8265&start=20#p56271) of the audacity forums for installation instructions, and the download.

Enjoy! :D

-Andy Rink

---


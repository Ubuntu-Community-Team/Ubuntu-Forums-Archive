---
title: "supertuxkart: Suzanne display error"
date: 2012-10-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-10-16
is anyone else having this glitch
i installed nvidia 310.14 today and i would like to know if this was happening in 305.51 or 304.43

---

### Post by cariboo on 2012-10-16
I'm using nvidia-current-updates 304.41, and I see the same thing. The problem only seems to be with suzanne, so I'd suggest it's a bug in the program.

---

### Post by pqwoerituytrueiwoq on 2012-10-16
i noticed my notify-send outputs were not transparent and i when and downgranted then purged the xorg edgers ppa, just to fint out it was a setting in the window manager,
i ended up checking every version of nvidia from 304.43 to 310.14
the bug was present in every version
anyone see that issue without nvidia?

---

### Post by pqwoerituytrueiwoq on 2012-10-16
[http://sourceforge.net/apps/trac/supertuxkart/ticket/659](http://sourceforge.net/apps/trac/supertuxkart/ticket/659)
found a bug report :)

---

### Post by Arthur_D on 2012-10-17
Please use the binary from the project site, or ignore until next release when we will have to force the issue about using the correct version of the Irrlicht library with STK.

---

### Post by pqwoerituytrueiwoq on 2012-10-17
[http://supertuxkart.sourceforge.net/Downloads](http://supertuxkart.sourceforge.net/Downloads) (NO COMPILING NEEDED :) )
latest 64bit copy works (download link 2)

if you are a stk dev any idea when this will end up in [playdeb](http://www.playdeb.net/updates/ubuntu/12.10/)?

---

### Post by Arthur_D on 2012-10-17
> **pqwoerituytrueiwoq said:**
> if you are a stk dev any idea when this will end up in [playdeb](http://www.playdeb.net/updates/ubuntu/12.10/)?
We don't have any control (or wish to have, really) over third party sites, and we don't package the game for the specific distributions ourselves, but rely on the wider community to do that. But as you can see, our static binaries should in most cases work fine (and at the moment considerably better than distro packages, due to various circumstances. But as said, we're hoping that all such issues will be solved for the upcoming 0.8 release).

Sorry for the inconvenience, and we hope you will keep having fun. :)

---

### Post by pqwoerituytrueiwoq on 2012-10-17
i will, could have more if there was a higher difficulty setting ;)
maybe gives the coms a handicap

---

### Post by Arthur_D on 2012-10-17
Actually, the AI has now been improved so much it was deemed neccessary to employ some subtle position-based limitations on it to keep it from zooming too far ahead. So if you want more challenge, you can look forward to 0.8. ;)

---

### Post by pqwoerituytrueiwoq on 2012-10-17
that is good news :)
how about making higher resolutions show more data instead of stretching the low res picture, because of that i play it at the default size instead of 1080p
obviously that would require more GPU power, but i think my GTX 550 TI can handle that

---

### Post by Arthur_D on 2012-10-17
It probably would, but we don't want to lose all the low-end users as well.

---

### Post by pqwoerituytrueiwoq on 2012-10-17
stretch could be optional and default, just saying

---


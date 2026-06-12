---
title: "StarCraft II settings - Wine"
date: 2010-08-06
forum: Wine
---

### Post by Emanuele_Z on 2010-08-06
Hi all,

I'm using wine 1.2 to play at this wonderful game with Ubuntu 10.04 x86-64 and an nVidia 470 GTX.

I've updated to latest drivers, 256.44 but unless I set shaders to Low, I can't get more than 15 FPS in Ultra mode full HD.

Any suggestion?
Cheers,

---

### Post by Sef on 2010-08-06
Moved to WINE forum.

---

### Post by aklo on 2010-08-06
I'm having the same problem as you. I have a lower end graphic card 8800GT capable to play HIGH / ULTRA in winxp but in ubuntu...it is quite unplayable unless i set it to low.

---

### Post by asdfoo on 2010-08-06
You can try updating to wine-1.3.0 to see if there are any improvements, there are a few small changes since 1.2.

Alternatively, you can try doing:

`winetricks orm=backbuffer`

if it says command not found then:

wget kegel.com/wine/winetricks
sh winetricks orm=backbuffer

See if the fps is any better, if not, set it back to the default
sh winetricks orm=fbo

---


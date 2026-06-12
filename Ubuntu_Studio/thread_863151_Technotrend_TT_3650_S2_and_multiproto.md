---
title: "Technotrend TT 3650 S2 and multiproto"
date: 2008-07-18
forum: Ubuntu Studio
---

### Post by alain_sat on 2008-07-18
Hi,

I'm trying to use my DVB S2 USB with Ubuntu8.04 and MyTheatre.
I found an how to [http://www.linuxtv.org/wiki/index.php/TechnoTrend_TT-connect_S2-3650_CI](http://www.linuxtv.org/wiki/index.php/TechnoTrend_TT-connect_S2-3650_CI) 
But I get stuck with the fail of the make.
It claims about the audio driver?
> make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/alain/3650/multiproto/v4l/em28xx-audio.o
In file included from /home/alain/3650/multiproto/v4l/em28xx-audio.c:39:
include/sound/core.h:281: error: 'SNDRV_CARDS' undeclared here (not in a function)
/home/alain/3650/multiproto/v4l/em28xx-audio.c:58: error: array index in initializer not of integer type
/home/alain/3650/multiproto/v4l/em28xx-audio.c:58: error: (near initialization for 'index')
make[3]: *** [/home/alain/3650/multiproto/v4l/em28xx-audio.o] Error 1


Did someone succeed?
I suppose it's due to the constant changing of the multiproto drive?

Hope someone have a solution or I will have to forget Linux and decide that it still can't replace Windows.
:lolflag:

---


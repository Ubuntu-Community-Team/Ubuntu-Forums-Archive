---
title: "running pc games with ubuntu"
date: 2008-07-23
forum: Ubuntu Gamers Arena
---

### Post by pip3 on 2008-07-23
is it possible to run gta san andreas in ubuntu? please help, it's my first day with this system and I'm slowly running out of patience!!! thanks. Pip.:confused:

---

### Post by jajan on 2008-07-26
Yes, have a look at this web page [http://sudosys.be/?q=GTA_san_andreas_on_ubuntu_8_04_wine]("http://sudosys.be/?q=GTA_san_andreas_on_ubuntu_8_04_wine")

---

### Post by airtonix on 2008-08-31
Yes I am doing it right now.

you need to setup winecfg to emulate a virtual desktop and turn off pixel shaders.

then you need to prefix "wine /path/to/san/andreas/executable" with aoss. 

So you end up with : 

"aoss wine ~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas/gta_sa.exe"

One note is that even on my 2.3ghz core duo nvidia8800gt with 2gb of ram...the frame rates start to drop *alot* when there is lots of smoke and flames around.

---


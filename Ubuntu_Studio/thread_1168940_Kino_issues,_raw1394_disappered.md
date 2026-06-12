---
title: "Kino issues, raw1394 disappered"
date: 2009-05-24
forum: Ubuntu Studio
---

### Post by WA_Garrett on 2009-05-24
Today I turned on my computer and raw1394 under /dev/ is gone. I am absolutely sure it was there yesterday. Where can you download it? 

This is related to issues I have had with capturing in Kino. I tried to capture video from my DV camera with kino last night however Kino couldn't capture video because it said > WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!
I got around that by opening kino through the terminal with sudo > sudo open kino
and then was able to capture video with kino. 

Today I started up my computer and tried to capture with kino, after opening it in the terminal using sudo the error "WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!" came up. Later I discovered that raw1394 was no longer under /dev/. Does anyone know what happened to it? 

Thanks.

---

### Post by WA_Garrett on 2009-05-24
Don't worry guy's, the problem has been solved, somewhat, at least as far as the confines of this thread.

---


---
title: "mt / tar settings for digital photo archive"
date: 2009-05-09
forum: Server Platforms
---

### Post by KewlEugene on 2009-05-09
i use these mt / tar options to archive 100's of GBs of raw/jpg  profesional digital camera images onto 200GB LTO2 tapes using ubuntu 8.10.

 mt -f /dev/nst0 setblk 65536
 # 65536 that's the max for mt as distributed in the mt-st package

 tar cvpbf 128 /dev/nst0 NikonD3Images

is the above optimal, i.e. does it fit as much data onto the tape as possible ?

thanks

---


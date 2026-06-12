---
title: "Fallout 3 and Wine Help"
date: 2009-01-31
forum: Wine
---

### Post by russianmario on 2009-01-31
My computer:
Ubuntu Itrepid
AMD Phenom 9850 Black
8 GB RAM
nVidia 9800 GX2 1 GB

A quick overview of what I've done already:
I wanted to play Fallout 3 on my linux box, so I found the tutorial on Wine's appDB and followed them through.  It worked.  I installed the patch for Fallout 3 and everything went downhill.  It required the xlive.dll and another dll.  Found the one dll (can't remember the name) and copied it to the fallout dir and the system32 dir.  Installed Windows for Games LIVE, and copied the xlive.dll to the fallout dir.  Still didn't work.

I then used winetricks to install DX9 and VC2005sp1 (I read somewhere that was the one I wanted).  Didn't work.  Installed VC2008 and broke it.  Now I get a seg fault and a whole bunch of fixme lines.  I've included as an attachment the whole execution from beginning to seg fault (the end :) ).  If you can offer any help, it would be appreciated.

Oh, and I'm using version 1.1.14 of wine.

---

### Post by RaiCoss on 2009-01-31
> **russianmario said:**
> My computer:
Ubuntu Itrepid
AMD Phenom 9850 Black
8 GB RAM
nVidia 9800 GX2 1 GB

A quick overview of what I've done already:
I wanted to play Fallout 3 on my linux box, so I found the tutorial on Wine's appDB and followed them through.  It worked.  I installed the patch for Fallout 3 and everything went downhill.  It required the xlive.dll and another dll.  Found the one dll (can't remember the name) and copied it to the fallout dir and the system32 dir.  Installed Windows for Games LIVE, and copied the xlive.dll to the fallout dir.  Still didn't work.

I then used winetricks to install DX9 and VC2005sp1 (I read somewhere that was the one I wanted).  Didn't work.  Installed VC2008 and broke it.  Now I get a seg fault and a whole bunch of fixme lines.  I've included as an attachment the whole execution from beginning to seg fault (the end :) ).  If you can offer any help, it would be appreciated.

Oh, and I'm using version 1.1.14 of wine.

If I was you I would try installing DirectX 9.0c manually, it works a trillion times better than Winetricks or Wine-Doors.

---


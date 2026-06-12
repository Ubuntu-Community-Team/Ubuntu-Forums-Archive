---
title: "Rdiff-backup ListError $RECYCLE.BIN/…[Errno 13] Permission denied: '/media/windows/$R"
date: 2014-08-20
forum: Server Platforms
---

### Post by tundmatu12345 on 2014-08-20
Hey! I facing this error : 
[http://stackoverflow.com/questions/25403535/rdiff-backup-listerror-recycle-bin-errno-13-permission-denied-media-win](http://stackoverflow.com/questions/25403535/rdiff-backup-listerror-recycle-bin-errno-13-permission-denied-media-win)
And i cant find solusion. Tryed different ways mounting drive to ubuntu and different rdiff backup commands, and still nothing. 
Maybe someone can help me out :)

---

### Post by TheFu on 2014-08-20
Add that pattern to your exclude list. It isn't like you want to backup the recycle bin.
\$RECYCLE.BIN - escaping it will be necessary.

Error 13 is permission denied - usually corrected by adding a group to the userid running the program, but i doubt that will work for this special location.

I've had issues with rdiff-backup on Windows - found it unreliable.  Much easier to just keep all data on Linux file systems and allow Windows to see the data over samba, at least that works here. Your situation might not allow it.

---

### Post by tundmatu12345 on 2014-09-14
Ty for your answer, that didnt work.

---

### Post by TheFu on 2014-09-14
> **tundmatu12345 said:**
> Ty for your answer, that didnt work.
**Much easier to just keep all data on Linux file systems and allow Windows to see the data over samba, at least that works here. Your situation might not allow it. **

BTW - what didn't work? Hard to help without new data.

---


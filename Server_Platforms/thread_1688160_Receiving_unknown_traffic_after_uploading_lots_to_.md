---
title: "Receiving unknown traffic after uploading lots to samba server"
date: 2011-02-15
forum: Server Platforms
---

### Post by kevpatts on 2011-02-15
Hey all,

I've found something strange. I'm running Maverick x64 desktop and I set up a Maverick server as a Samba NAS. I've got it mounted in fstab and all is working swimmingly.

Yesterday I uploaded 240 odd gigs of stuff up to it, and it finished at about 7pm. When I looked at my desktop today I noticed that the network monitor was still very high.

After looking at the traffic in WireShark it would seem that I'm RECEIVING about 3Mb/s FROM the NAS box! What could be causing this?

Kevpatts

---

### Post by kevpatts on 2011-02-15
Quick update on this: I notice that if I drop my network connection and re-enable it the traffic resumes, but if I reboot it stops.

This would imply to my that my desktop machine is taking this from the server as opposed to the server pushing it to me.

---

### Post by Grenage on 2011-02-15
Not necessarily, but that's an odd issue; can you replicate it?

Without capturing data, it's hard to guess what was happening.  It's likely that no files were really being sent or received, but that one of the two devices were confused and there were TCP/IP problems (lack of ACKs, perhaps).

This isn't really my forté.

---


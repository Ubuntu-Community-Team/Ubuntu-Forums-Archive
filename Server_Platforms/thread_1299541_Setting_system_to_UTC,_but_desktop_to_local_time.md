---
title: "Setting system to UTC, but desktop to local time"
date: 2009-10-24
forum: Server Platforms
---

### Post by daniel_summers on 2009-10-24
I recently obtained an Ubuntu VPS, and the time is set to UTC.  I'm really liking this setup!

I have an Ubuntu development machine that I use to create the apps that I run on this new VPS.  I'd like for the underlying system to be set at UTC as well (i.e., the PostgreSQL function "current_timestamp" would return UTC), but still be able to have XFCE display my local time (i.e., Thunderbird's displayed e-mail received times would return local time).  This would help me ensure my time zone translation code is working properly, without moving the whole machine to UTC.

Is what I'm describing  possible?  Or is it all-or-nothing?  From what I've read, it would seem to be the latter; hopefully, though, someone here can either confirm that, or describe the procedure for the former.

Thanks...

---


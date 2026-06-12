---
title: "LTSP mounting windows shares at login"
date: 2010-04-21
forum: Server Platforms
---

### Post by mappy24 on 2010-04-21
I've been asked to investigate the possibility of using LTSP in our school to provide a more "real world" programming environment to our students.  We have a Windows 2003 Server domain and no plans to change it.

I've set up the LTSP server, joined the domain and everything seems to be working fine, I can login to the LTSP server with a student account.

The next thing I want to achieve is give the students access to their "My Documents" folder on the Windows 2003 server.  Is it possible to have a student log on to the terminal server (who has never logged in before) and have it automatically mount their share on the windows server?  Login script??

---

### Post by Dayofswords on 2010-04-21
i have a feeling you'll end up using cron...

but i have yet to figure how how to use that dang feature

---


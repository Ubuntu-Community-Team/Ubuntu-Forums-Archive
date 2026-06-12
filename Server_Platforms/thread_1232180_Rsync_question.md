---
title: "Rsync question"
date: 2009-08-05
forum: Server Platforms
---

### Post by TheGameAh on 2009-08-05
Have about 300 gigs of data (just samba shares) being Rsynced to another box.  Obviously, the idea being that if the motherboard dies in Server1, I can just point users to Server2 to access their data while I fix Server1.  After the initial first Rsync, it now only takes about a minute to copy the changes.  Beautiful.

My question is that in the case of disaster, and users are now temporarily working off of Server2, after I get Server1 back up and running, is it just a matter of performing an rsync from Server1?  If so, will it take a long time?  Or will it somehow know to compare changes between Server1 and Server2, and pull only that data back?

---


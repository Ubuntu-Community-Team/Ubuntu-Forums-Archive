---
title: "Samba changes file created date on save"
date: 2011-04-06
forum: Server Platforms
---

### Post by Dave.Wynne on 2011-04-06
I'm using 9.04 server as a PDC with Samba, and I've just noticed an issue after nearly 2 years. Samba, I assume is changing the created date of the file when we save, unfortunately we are a engineering company using CAD our drawing sheets use the file created date in the title block. Does anyone know if this is a well known issue and is there a work arround?

---

### Post by dtfinch on 2011-04-06
The main issue is that for the most part file creation times don't exist on Linux. Newer filesystems (ext4, btrfs) have added support internally, but it's not very accessible yet.

[http://lwn.net/Articles/397442/](http://lwn.net/Articles/397442/)

[http://linux.die.net/man/2/stat](http://linux.die.net/man/2/stat)

---


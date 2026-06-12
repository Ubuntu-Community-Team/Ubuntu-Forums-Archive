---
title: "Trash folder for items deleted through Samba/Netatalk/proFTPd"
date: 2008-12-02
forum: Server Platforms
---

### Post by batfastad on 2008-12-02
Hi everyone

I built a new NAS about 6 months ago running Ubuntu Server 8.04 LTS. It's a 3TB monster in a RAID 6 with a 3Ware controller, working excellently so far.

It shares files out to our network using Samba and Netatalk (and soon proFTPd)
I was wondering if there's a way a Trash folder can be setup, so that whenever anyone deletes anything from a Samba/Netatalk share, it gets moved to a trash folder instead.

Is something like this possible with Ubuntu Server?

Thanks, B

---

### Post by batfastad on 2008-12-05
Hi guys
Anyone know if this is possible?

Cheers, B

---

### Post by lykwydchykyn on 2008-12-05
In samba, yes, using a vfs object.  I've tested this too so I know it works, and it's quite easy.  Here's a good howto:

[http://www.stress-free.co.nz/sambas_recycle_vfs_provides_salvage_like_functionality](http://www.stress-free.co.nz/sambas_recycle_vfs_provides_salvage_like_functionality)

Don't know about proftpd or netatalk.

---

### Post by batfastad on 2008-12-09
Ok that's cool! I'll look into that on a test server.
But there's no global way of doing this, at an OS level?

Cheers, B

---

### Post by lykwydchykyn on 2008-12-10
I don't know of a clean way of doing it, I guess you could write some kind of trash script and replace rm, but I couldn't tell you what that'd do for samba et al.  I'm guessing they delete files via some kind of system call rather than calling rm directly, but I don't really know.

---


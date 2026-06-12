---
title: "SFTP Transfer kills network connectivity"
date: 2009-07-15
forum: Server Platforms
---

### Post by papodaca on 2009-07-15
I just recently upgraded my NAS/Media server (hardware and software) running Ubuntu Server 8.10 to 9.04.  The new box is based off a Intel board (Intel BOXD945GCLF2D).  
When I transfer anything via SFTP that is relatively large networking completely dies as if some one goes and physically disconnects the machine.  After a random amount of time I will be able to log in and see this in /vat/log/syslog "Jul 15 19:56:07 Aurora kernel: [ 4019.821674] r8169: eth0: link up" meaning that the interface was brought back up.  But why is it going down in the first place?

---

### Post by papodaca on 2009-07-16
Bumb.

---

### Post by papodaca on 2009-07-16
As is would seem I found this in the Today's Posts.  [Compiling the kernel module seems to have fixed it.  ]("http://ubuntuforums.org/showthread.php?t=1022411")

---

### Post by scorp123 on 2009-07-17
> **papodaca said:**
>  When I transfer anything via SFTP that is relatively large networking completely dies as if some one goes and physically disconnects the machine. Try using **rsync** instead.

So instead of e.g. 
```
scp -r -P 2222 user@remote-target:/remote/path/* /path/to/target/
```

You could use e.g.
```
rsync -e 'ssh -p 2222' --bwlimit=2000 user@remote-target:/remote/path/* /path/to/target/ 
```

**rsync** is much "nicer" over problematic network links, especially the **--bwlimit=***number-in-KBPS* feature is useful.

---


---
title: "FreeNX - Repository - Feisty"
date: 2007-04-19
forum: Server Platforms
---

### Post by Alex^77 on 2007-04-19
Hello ubuntu users,
I would like to upgrade my server to fiesty, and I would like to stop to use NX Server and use FreeNX.

IN the last version of Ubuntu (breezy) there is in the default canonical repository the last FreeNx.

But now, in fiesty backports FreeNX there isn't.

Where can I find a GOOD repository for it??

Regards
Alex

---

### Post by Alex^77 on 2007-04-20
Up

---

### Post by Alex^77 on 2007-04-20
Up

---

### Post by b3nw on 2007-04-20
hi,

you should be able to use the .deb files provided at the free nx website (nomachine.com) to do this.

Just download the debian version and do dpkg -i

I believe there are 2 dependencies needed libdist++ and libaudio0 (from memory probably not exact names) if the dpkg -i install fails, then open aptitude, and hit g. It will install the missing packages and then install the package that failed.

Good luck :)

---

### Post by chomafin on 2007-04-20
> **Alex^77 said:**
> Up
Could try this.
[http://ubuntuforums.org/showthread.php?t=412154&highlight=freenx](http://ubuntuforums.org/showthread.php?t=412154&highlight=freenx)

---


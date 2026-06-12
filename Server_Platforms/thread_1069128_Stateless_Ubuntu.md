---
title: "Stateless Ubuntu?"
date: 2009-02-13
forum: Server Platforms
---

### Post by cayblood on 2009-02-13
I'd like to know if there is any easy way to set up Ubuntu in a way that would work well in an appliance environment where power can be cut any time without necessitating a disk check on reboot. I'd like to configure it to load all volatile files into RAM so that cutting power would have no effect on the system state.

---

### Post by cayblood on 2009-02-13
Just to clarify here, I guess what I'm looking for is something like a custom liveCD except that it would be running from my hard drive instead of a cd-rom drive, but treating the hard drive as read-only, just like a cd-rom.

---

### Post by koenn on 2009-02-13
a journaling filesystem such as ext3 is able to recover quite fast and error-free without extensive fs check; you might want to give that a try

---

### Post by jimv on 2009-02-14
You could use a small SSD.  THen you don't need to worry about hard drives getting damaged during a hard shutdown.

---

### Post by volkswagner on 2009-02-14
Not sure if this is exactly what you are looking for or not.

Take a look at Turnkey Linux.  They have several [appliances]("http://www.turnkeylinux.org/appliances"), pre-built. These are live CD's, mostly designed to be installed in a VM, I think.

They may give you a good starting point.

---


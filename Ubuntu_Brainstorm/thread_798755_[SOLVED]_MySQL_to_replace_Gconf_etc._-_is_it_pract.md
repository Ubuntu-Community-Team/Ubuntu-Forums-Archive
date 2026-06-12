---
title: "[SOLVED] MySQL to replace Gconf etc. - is it practical?"
date: 2008-05-18
forum: Ubuntu Brainstorm
---

### Post by ikarus2k on 2008-05-18
Programs these days start relying on databases, i.e. Firefox 3, MythTV, Miro, Tracker (does the index count as a DB?). From what I see it would be extremely useful to have them communicate with each other.

From what I understood, [LibElektra]("http://www.libelektra.org/") (which "is a universal hierarchical configuration store") is a start, but a powerful database to contain more than just configuration files (i.e. location of music files with their tags etc.) is what I envision.

Would such an implementation be feasible? How would system resources be affected?

---

### Post by smartboyathome on 2008-05-18
I don't think so. You are talking about transfering all of GNOME to this, which would pretty much halt GNOME development for a good few months at least. Also, would this slow down GNOME at all or anything?

---

### Post by chrisccoulson on 2008-05-18
Why would GConf need to be converted to MySQL (or any other format for that matter)? The format of the underlying GConf files is transparent to any application using them as they all manipulate GConf keys via the GConf API, so changing the storage format for these settings wouldn't make any difference to applications relying on GConf.

Besides, the beauty of GConf is that all the underlying settings are stored in human-readable XML files. Moving away from that would leave us with something more like the Windows registry. Yuck!

---

### Post by 23meg on 2008-05-18
[QUOTE=ikarus2k]a powerful database to contain more than just configuration files (i.e. location of music files with their tags etc.)[/QUOTE]

Sounds like Tracker.

---

### Post by ikarus2k on 2008-05-19
Ok, I'm sorry I wasn't clear enough

I'm thinking of a DB to replace not only Gconf, but to be another layer between the user and the PC. It should handle file management as well (I don't need t know exactly where my mp3's are).

But thanks, if it's to cumbersome, I understand.

---

### Post by stephantom on 2008-05-19
Besides from being not right for the task, MySQL would pull a massive amount of dependencies in and add a heavier daemon to your memory (gconfd-2 uses 2.5MiB, whereas mysqld uses over 18.6MiB).
So, to answer your original question: No, I don't think is anywhere near practical. But I think I've read somewhere that gconf doesn't really care how the data is stored. So it should *theoretically* even be possible to write a MySQL backend for gconfd.

---

### Post by gnomeuser on 2008-05-19
instead of ripping out the configuration backends of everything and agreeing on a suits all replacement like elektra the more sensible approach would be doing something akin to what PackageKit is doing to package management interfaces. One interface many backends, then we can have everything we want without the drawbacks of extended development and design pains. 

Such a project exists:
[http://augeas.net/](http://augeas.net/)

---

### Post by 23meg on 2008-05-19
> **ikarus2k said:**
> Ok, I'm sorry I wasn't clear enough

I'm thinking of a DB to replace not only Gconf, but to be another layer between the user and the PC. It should handle file management as well (I don't need t know exactly where my mp3's are).

But thanks, if it's to cumbersome, I understand.

You're really just describing Tracker, which has been shipping with Ubuntu by default in the last two releases, and which uses SQLite.

---

### Post by ikarus2k on 2008-05-21
Thanks everybody for your time. :D

P.S. No, I'm not describing tracker!

---


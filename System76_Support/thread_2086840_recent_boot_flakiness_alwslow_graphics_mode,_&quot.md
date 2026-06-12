---
title: "recent boot flakiness: alwslow graphics mode, &quot;scanning for btrfs filesystem&quot;"
date: 2012-11-22
forum: System76 Support
---

### Post by b7j0c on 2012-11-22
in the last week or so I am seeing continuous issues during the boot process. 

the system almost always boots into low graphics mode now, and i can manually start lightdm, but still...

I also see periodic console messages about "scanning for btrfs filesystem"...which of course I don't have and never have had

the system is a 15.6 gazelle, purchases about four months ago. all updates applied.

clues?

---

### Post by LuisGMarine on 2012-11-22
When booting up my new Wild Dog computer I notice the same thing, but mine is able to boot about 99% of the time ....  Going to keep my eye on this thread in case it is something more serious and how to fix it.

---

### Post by b7j0c on 2012-11-24
as it stands, I have correlated the issues to my installation of tor, as the problems seemed to start after installing tor, and went away after purging it. what does tor have to do with graphics detection? don't know. it does of course put a daemon into the bootup process...otherwise I can't see how they are strictly related, but just dumping this here in case it is useful to others

---

### Post by isantop on 2012-11-27
> **b7j0c said:**
> as it stands, I have correlated the issues to my installation of tor, as the problems seemed to start after installing tor, and went away after purging it. what does tor have to do with graphics detection? don't know. it does of course put a daemon into the bootup process...otherwise I can't see how they are strictly related, but just dumping this here in case it is useful to others

It may be causing a race condition and preventing the Graphics driver from loading before the Login Screen.

---


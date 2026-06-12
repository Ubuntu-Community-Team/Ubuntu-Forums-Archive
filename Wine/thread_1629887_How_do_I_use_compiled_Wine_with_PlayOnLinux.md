---
title: "How do I use compiled Wine with PlayOnLinux?"
date: 2010-11-24
forum: Wine
---

### Post by martini1179 on 2010-11-24
I had to compiled Wine (1.2.1) in order to include a specific patch. I'd like to install PoL to let me easily install other games, but I don't know how/if I can install PoL since it always asks to install Wine from the repos, and I don't want to overwrite my custom Wine install.

---

### Post by martini1179 on 2010-11-27
/bump

---

### Post by martini1179 on 2010-11-29
/bump

---

### Post by martini1179 on 2010-11-30
/bump

---

### Post by Hotch_Potch on 2010-12-19
Try to install pol *after* your custom made wine through symantec. All vanilla packages will be accessable through pol interface, though *system* wine will be also present.

Please, tell if you find a way to add several custom versions of wine simultaneously.

Sorry for poor language.

---

### Post by martini1179 on 2010-12-19
> **Hotch_Potch said:**
> Try to install pol *after* your custom made wine. All vanilla packages will be accessable through pol interface, though *system* wine will be also present.

Please, tell if you find a way to add several custom versions of wine simultaneously.

Sorry for poor language.

Your language is fine. But I don't think it's possible to install PoL after a custom/compiled Wine, at least not through Synaptic. The problem is that the system will try to install Wine from the repos, sine Wine is a dependency of PoL. This would overwrite my custom Wine directory. 

I wonder if I could just rename ~/.wine to something else and have everything still work?

---

### Post by markackerman8@gmail.com on 2011-02-13
I have never had a problem installing PoL after installing wine.

Synaptic never had problems with a dependency clash, only when uninstalling wine (it uninstals PoL, but when you reinstall wine PoL will install without loosing PoL's infrastructure or it's own wine versions which it keeps in the PoL directory.
:D

---

### Post by martini1179 on 2011-02-13
> **markackerman8@gmail.com said:**
> I have never had a problem installing PoL after installing wine.

Synaptic never had problems with a dependency clash, only when uninstalling wine (it uninstals PoL, but when you reinstall wine PoL will install without loosing PoL's infrastructure or it's own wine versions which it keeps in the PoL directory.
:D

Yes, yes, but did you *compile* Wine yourself from source, or install it through the repos or PPA? It makes all the difference when attempting to install PoL.

---

### Post by philnice on 2011-02-14
> **Hotch_Potch said:**
> 

Please, tell if you find a way to add several custom versions of wine simultaneously.


Have you tried Q4wine? It claims it can handle multiple wine versions at the same time. I have it installed but never needed to do that so far. It's in synaptic.

---

### Post by commodore256 on 2011-02-14
There should be a .playonlinux folder in home. (Ctrl+H to unhide it)

In there, there should be installed wine versions.

Try copying the wine in your /usr/lib and /usr/bin and use it to replace the playonlinux wine.

From what I understand, playonlinux just extracts a deb and all a deb does is just merge binaries from the deb to your / directory.

So, just copying your compiled wine to where playonlinux extracts the deb should work with all the patches.

---


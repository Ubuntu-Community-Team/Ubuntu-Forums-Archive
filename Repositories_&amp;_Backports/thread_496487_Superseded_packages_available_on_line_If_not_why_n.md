---
title: "Superseded packages available on line? If not why not?"
date: 2007-07-09
forum: Repositories &amp; Backports
---

### Post by ubergeeknz on 2007-07-09
I am pretty new to the Ubuntu world, although I have flirted with Linux several times over the past 7-8 years.  Ubuntu Feisty is the first time I have successfully managed to replace Windows (almost) entirely for my everyday work.

However I have a beef with the on line repository system.

If I get an update, and that update causes a problem (or I have cause to believe that it has), it seems that any time I go looking for the previously installed version of the package it is not available.  Same goes for older kernel modules/source.  Basically if I want to run anything less than the bleeding edge, I have to never update anything, which is obviously not desirable, or I have to fish out my CD and downgrade to the original version.  This doesn't leave a lot of options open for troubleshooting.

Is there any good reason that all packages are not kept on line, even if they are superseded?  is this a space issue?  Or are there special repositories I need to add to get access to older packages?  If no-one is doing this now, perhaps I could assist with getting this happening (I am sure I could find some inexpensive space).

If this was cleared up, I'd be really stoked. The Ubuntu community has, to my mind, tied up a lot of little loose ends that have been holding Linux back from widespread adoption for far too long.  Keep up the good work!!

---

### Post by moore.bryan on 2007-07-09
*most will tell you downgrading (or rolling-back) a package is a bad idea because of how it can screw-up post-installation scripts.  all the "old" packages are available in the older [repos]("http://packages.ubuntu.com/"), though; aren't they?  you could (although, once again, i wouldn't recommend it) go to the breezy release and download/reinstall the old program...*

---

### Post by ubergeeknz on 2007-07-09
Appreciate the quick and detailed reply!

> **moore.bryan said:**
> *most will tell you downgrading (or rolling-back) a package is a bad idea because of how it can screw-up post-installation scripts.  *

Fair enough; but isn't that a weakness in the packages or the packaging system that should be addressed?  I mean any system destined to be used for anything resembling mission-critical systems surely *must* have a robust rollback for updates in case they cause issues.  I suppose a clean removal of the package followed by a reinstall of the older package might do the trick, but really it should be transparent.

> **moore.bryan said:**
> *all the "old" packages are available in the older [repos]("http://packages.ubuntu.com/"), though; aren't they?*

I will try adding that repo next time I need to back something out, it might save me in a pinch (assuming it really does have all the superseded packages) :)

---

### Post by moore.bryan on 2007-07-09
> **ubergeeknz said:**
> Appreciate the quick and detailed reply!
Fair enough; but isn't that a weakness in the packages or the packaging system that should be addressed?  I mean any system destined to be used for anything resembling mission-critical systems surely *must* have a robust rollback for updates in case they cause issues.  I suppose a clean removal of the package followed by a reinstall of the older package might do the trick, but really it should be transparent.
*i don't know if i'd classify it as a "weakness," but i do think having a set rollback program would be a good idea.  alas, i am no programmer. ;-)*
> **ubergeeknz said:**
> I will try adding that repo next time I need to back something out, it might save me in a pinch (assuming it really does have all the superseded packages)
*i wouldn't add the repos, if i were you; instead, i'd just download the package i want to reinstall, download that deb and install it.*

---

### Post by venky on 2007-07-12
Also see /var/apt/archives

---


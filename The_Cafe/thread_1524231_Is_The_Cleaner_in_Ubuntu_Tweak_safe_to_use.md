---
title: "Is The Cleaner in Ubuntu Tweak safe to use?"
date: 2010-07-04
forum: The Cafe
---

### Post by TheNerdAL on 2010-07-04
So I heard Computer Janitor isn't safe to use and I head that Ubuntu Tweak has a cleaner like Computer Janitor and I was wondering if it is safe to use, thanks.

---

### Post by NightwishFan on 2010-07-04
I have never tried Ubuntu Tweak. Computer Janitor is safe, it just requires a review of what packages it is actually removing. If you removed a metapackage and just want some of the stuff it pulls in, it may target them for removal. (Which in most cases is desired).

---

### Post by cbowman57 on 2010-07-05
I use the cleaners in both Ubuntu Tweak and Bleachbit.

Janitor seems too aggressive for my taste and wants to remove things I use.

---

### Post by Giant Speck on 2010-07-05
Since the cleaners in Ubuntu Tweak don't actually uninstall any software, they are safe, if not safer than Computer Janitor.  The cleaners in Ubuntu Tweak clean the following things:
[B]
1.  Packages.[/B]    
These are packages that are no longer being used by the system and can be safely removed.

[B]2.  Cache. 
[/B] These are packages (usually in the form of .debs) that are downloaded whenever you update your system.  Since these updates have already been installed, the actual .debs themselves are no longer necessary and can be safely removed.

**3.  Config.** 
 These are configuration files for applications that are no longer installed, which can therefore be safely removed.
[B]
4.  Kernels.[/B] 
 These are unused old kernels that are no longer in use and can be safely removed.

---

### Post by TheNerdAL on 2010-07-05
> **Giant Speck said:**
> Since the cleaners in Ubuntu Tweak don't actually uninstall any software, they are safe, if not safer than Computer Janitor.  The cleaners in Ubuntu Tweak clean the following things:
[B]
1.  Packages.[/B]    
These are packages that are no longer being used by the system and can be safely removed.

[B]2.  Cache. 
[/B] These are packages (usually in the form of .debs) that are downloaded whenever you update your system.  Since these updates have already been installed, the actual .debs themselves are no longer necessary and can be safely removed.

**3.  Config.** 
 These are configuration files for applications that are no longer installed, which can therefore be safely removed.
[B]
4.  Kernels.[/B] 
 These are unused old kernels that are no longer in use and can be safely removed.

Thanks!

---

### Post by NightwishFan on 2010-07-05
Most of those tasks can be handled by aptitude/synaptic as well. Though having old kernels/cache can sometimes be useful, especially if you remove virtualbox, and suddenly decide to get it again, its right in the cache.

---

### Post by shuttleworthwannabe on 2010-07-05
I have used UT cleaner mainly to clean older kernels, and so far it has been fine.

---

### Post by Frogs Hair on 2010-07-05
I use Bleach Bit to clean up temporary files after installations and updates.

---

### Post by betrunkenaffe on 2010-07-05
Tested all but the cache, my comp didn't crash and still able to do everything so seems safe me .

---


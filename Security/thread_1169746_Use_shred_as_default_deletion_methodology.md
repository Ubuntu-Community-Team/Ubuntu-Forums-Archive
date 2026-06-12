---
title: "Use shred as default deletion methodology?"
date: 2009-05-25
forum: Security
---

### Post by Nuvious on 2009-05-25
I was curious if it was possible to have shred be the default deletion methodology for a system.  For a while I thought about using aliasing on rm, rmdir, etc, to make it so shred would be used instead of those commands.  However I heard shred doesn't work 100% of the time so an alias along these lines would be required:

alias rm='shred -n 10 -f $0 || rm $0'

I'm guessing the above is improper syntax for alias.  My next question would then be does this work for all applications or are rm and rmdir not used by all programs?

Basically my question culminates in is there a way to have ubuntu do a secure deletion whenever a file is deleted by any program?  Thanks in advance for serious replies!

---

### Post by HermanAB on 2009-05-25
Well, "shred doesn't work 100% of the time" is about right yes...
;)

Basically, you are wasting your time.  Use LUKS to encrypt your data.

---

### Post by Nuvious on 2009-05-25
It's a shared system :/ so I can't just give the encrypted system password to everyone.  Also I'm not 100% scared of data security, just don't want to delete something and decide later that I wanted to shred it.

---

### Post by HermanAB on 2009-05-25
Well, the problem is that shredding a file is not necessarily better than a simple rm.  Whereas rm always does the same thing and is predictable, the actions taken by shred is not predictable, so you cannot trust that a file is really overwritten and since you cannot trust it, why bother?

If you want a system that you can trust, use LUKS.  LUKS can have multiple keys.  Everyone using the system can have their own LUKS password for the system and another password for their own home directory.

---


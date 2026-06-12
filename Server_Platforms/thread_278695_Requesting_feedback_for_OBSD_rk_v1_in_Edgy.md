---
title: "Requesting feedback for OBSD rk v1 in Edgy"
date: 2006-10-16
forum: Server Platforms
---

### Post by lotusleaf on 2006-10-16
Is this a false positive or something more?

A user in #ubuntu-offtopic mentioned this and so I checked for myself and confirmed the same result he found, which is:

Scan result for OBSD rk v1 using chkrootkit v0.46a-3:

```
Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security
```

Scan result for OBSD rk v1 using chkrootkit v.0.47:

```
Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security
```

**If you use Edgy and have chkrootkit installed, please post back with your result for this so I may determine whether or not this is a false positive, thanks!**

Here's what the other person, LjL, in #ubuntu-offtopic was saying about this:

> <LjL> for that matter, i get    Searching for OBSD rk v1... /usr/lib/security            /usr/lib/security/classpath.security

<LjL> lotusleaf: the official chkrootkit changelogs don't mention OBSD at all. they don't even mention a 0.46a-2 or 0.46a-3 version either, for that matter, so those should just be Ubuntu package revisions...

<LjL> lotusleaf: hm, just a guess -- perhaps this "OBSD" thing is, like the name suggests, a trojan that affects BSD systems. maybe the check was removed from Dapper, since it's not a BSD, but it was not removed on Edgy

<LjL> lotusleaf: and the Debian changelog doesn't say a thing about it in the 0.46-a2 -> 0.46a-3 changes

---

### Post by lotusleaf on 2006-10-17
bump - if you have Edgy with chkrootkit installed, please test and leave feedback here with your experiences, it only takes a few seconds, thanks in advance

---

### Post by hollows2 on 2006-10-23
Same goes for me 

Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security


Hope its not a problem - rkhunter shows no problems.

Steve

---

### Post by umarmung on 2006-10-28
This is not a rootkit. Check the documentation in /usr/share/doc/chkrootkit/README.FALSE-POSITIVES

> 
below is a (non-exhaustive) list of packages that are known to cause false
positives.
[...]
contains specific files
asp: Ramen Worms contain the file /usr/bin/asp
libgcj-common: the 'OBSD rk v1' contains
/usr/lib/security,
/usr/lib/security/classpath.security
/usr/lib/security/libgcj.security. 


---

### Post by StarsAndBars14 on 2006-11-17
Yup.  Shoulda known I'd get it.

---


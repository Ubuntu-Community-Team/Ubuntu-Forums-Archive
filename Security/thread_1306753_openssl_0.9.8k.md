---
title: "openssl 0.9.8k"
date: 2009-10-30
forum: Security
---

### Post by Alex Yeh on 2009-10-30
I understand that the upstream vender (debian) doesn't offer the latest version of openssl, even though there are several security holes in the version shipped with Ubuntu and many other debian-based distros. Can anything be done about this? I realize that openssl is the basis for the entire cryptographic substructure of the system, and that it is seriously non-trivial to update it. However, given the security concerns, it seems like this (keeping up to date) should be given priority.

---

### Post by kevdog on 2009-10-31
Then compile openssl from source!!!  Its fairly easy to be done!

---

### Post by Alex Yeh on 2009-10-31
Greetings, kevdog.

I know how to compile openssl from source -- it is, as you say, very easy to do. The trouble is, since openssl is so tightly integrated with the base system, simply compiling it by hand is not going to solve anything.

If I try to replace the system openssl with my hand-compiled version, it will break my ubuntu installation, since openssl is the cryptographic backbone of the system. Replacing the system openssl would require recompiling everything that rests on top of it, and, this being a debian-based system, that is a *lot* of stuff. I suspect this is the main reason why openssl updates lag behind upstream (openssl.org) openssl development.

This is just something that bugs me. Perhaps I should have posted this to a Debian mailing list, since it's a Debian thing.

---

### Post by kevdog on 2009-10-31
Are you compiling the kernel from source?

---

### Post by aos101 on 2009-11-01
Are you sure the openssl package in Ubuntu hasn't had the security fixes backported?  Usually the Ubuntu developers prefer to patch the code to fix security flaws instead of upgrading the whole package, so they only have to make the absolute minimum number of changes to a stable release of Ubuntu.  

If you look at the Ubuntu changelog for [openssl in Ubuntu 9.10](http://packages.ubuntu.com/karmic/libssl0.9.8) you'll see that although openssl in Ubuntu isn't based on the latest release of openssl, it still has recent security fixes applied to the code because the fixes are backported.

---


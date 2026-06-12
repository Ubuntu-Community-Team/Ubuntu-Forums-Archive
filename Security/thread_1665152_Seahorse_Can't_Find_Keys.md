---
title: "Seahorse Can't Find Keys"
date: 2011-01-11
forum: Security
---

### Post by rookcifer on 2011-01-11
Ok, so I have installed the Seahorse plugin that allows the right-click "encrypt" function for Nautilus, but whenever I try to encrypt a file, I get a message that my keys cannot be found.

```
No encryption keys were found with which to perform the operation you requested.  The program Passwords and Encryption Keys will now be started so that you may either create a key or import one.
```

However, I have my keys in their usual place: ~/.gnupg.  Further, when it launches the "Password and Encryption Keys" dialog, it wont let me import any keys -- when I click on a .asc file to import, nothing happens.

GPG from the command line works just fine, but I cannot get Seahorse working. Is this a $PATH problem of some sort?  A gpg.conf issue?  Any ideas?

---

### Post by bodhi.zazen on 2011-01-12
Probably a few bug reports on this

I found this

[https://answers.launchpad.net/ubuntu/+source/seahorse-plugins/+question/67957](https://answers.launchpad.net/ubuntu/+source/seahorse-plugins/+question/67957)

but no solution was posted.

---

### Post by rookcifer on 2011-01-12
I figured it out.  I had compiled my own GnuPG version (to a later version) and apparently there was a $PATH problem, where Seahorse couldn't recognize where the keys were.  So I just uninstalled the compiled binary and all works properly now.

Marked as solved.

---


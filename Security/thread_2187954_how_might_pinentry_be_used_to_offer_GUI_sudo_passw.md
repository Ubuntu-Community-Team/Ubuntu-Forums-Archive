---
title: "how might pinentry be used to offer GUI sudo password prompt?"
date: 2013-11-14
forum: Security
---

### Post by thaitang on 2013-11-14
I would like to use the pinentry app in a bash script for prompting users to enter a password, sudo for example or LUKS passphrase even, securely. The job would be fairly easy I think using zenity but also I am quite skeptical about how secure such a solution would be, even though there are multiple examples online showing how.

I just can't seem to find any documentation on the pinentry app and the man page is bare bones info (as usual).

> PIN-Entry programs are usually invoked by the gpg-agent daemon, but can be run from the command line as well.

> This package contains a program that allows for secure entry of PINs or pass phrases. That means it tries to take care that the entered information is not swapped to disk or temporarily stored anywhere. This functionality is particularly useful for entering pass phrases when using encryption software such as GnuPG or e-mail clients using the same. It uses an open protocol and is therefore not tied to particular software.

This is about all the useful info I have found. Maybe I am looking in all the wrong places.

When 'pinentry' is run from the command line it drops into its own shell asking for a command, and if you enter 'getpin' the pinentry pop window pops allowing text to be entered which is visible in the pinentry shell (I guess) after hitting enter. Would it possible to pipe (or would that be insecure, probably), or how could that entry at the pinentry window be used by a request for a sudo passowrd?

How might I go about seeing how gpg makes use of gpa-agent that is the pinentry client? That might help but I can't find much googling that either.

---

### Post by thaitang on 2013-11-15
Thanks to Tom's helpful reply at [http://blog.sanctum.geek.nz/linux-crypto-disks/#comment-16505](http://blog.sanctum.geek.nz/linux-crypto-disks/#comment-16505), he dug up a perl script: lukspinentry.pl that works like a charm.

```
lukspinentry.pl | sudo -S cryptsetup luksOpen "$devN" "$mapN"
```

allows for LUKS passphrase entry using a GUI, which although the same thing could be done with zenity/yad, I was uncertain about the potential security risk. Pinentry's boast, "that allows for secure entry of PINs or pass phrases. That means it  tries to take care that the entered information is not swapped to disk  or temporarily stored anywhere not swapping," makes me feel much easier with this solution.

---


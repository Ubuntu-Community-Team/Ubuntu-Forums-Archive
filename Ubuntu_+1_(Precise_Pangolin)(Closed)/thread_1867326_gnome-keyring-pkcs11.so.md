---
title: "gnome-keyring-pkcs11.so"
date: 2011-10-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VinDSL on 2011-10-22
Been seeing an error in cli, the past few days, saying the above file/folder doesn't exist.

Doing forensics on the file system, I discovered the location has changed in UbuPP.


[INDENT]Old location:  /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so

New location:  /usr/lib/pkcs11/gnome-keyring-pkcs11.so
[/INDENT]


Fixed the error(s) with a symlink, but this isn't kosher, in the long run, if the location was intentionally changed.

Been Google'ing the situation, but nothing is popping up (for me).

Anybody know what's going on?!?!?  Location change?  Bug?

---

### Post by MAFoElffen on 2011-10-22
> **VinDSL said:**
> Been seeing an error in cli, the past few days, saying the above file/folder doesn't exist.

Doing forensics on the file system, I discovered the location has changed in UbuPP.
[INDENT]Old location:  /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so

New location:  /usr/lib/pkcs11/gnome-keyring-pkcs11.so
[/INDENT]Fixed the error(s) with a symlink, but this isn't kosher, in the long run, if the location was intentionally changed.

Been Google'ing the situation, but nothing is popping up (for me).

Anybody know what's going on?!?!?  Location change?  Bug?
There was a mess of gnome updates last night.  I noticed that error came up during those updates. (One on gnome cert or such)  I figured that I would wait a couple days and see it it cathes up with itself.  It sort of reminded me of the udev error last cycle.

---

### Post by dino99 on 2011-10-23
have had that issue too, and have simply copy/paste to the required path. Might need to report against this error as its not done as i know.

---

### Post by Bowmore on 2011-10-23
I guess this is one of a few multilarch issues.

Bug:
Please convert gnome-keyring to multiarch
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/859600](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/859600)

For some reason this one is one month old and not yet acted upon :(

---

### Post by cariboo on 2011-10-23
> **Bowmore said:**
> I guess this is one of a few multilarch issues.

Bug:
Please convert gnome-keyring to multiarch
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/859600](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/859600)

For some reason this one is one month old and not yet acted upon :(

That bug is pretty sparse on details, if you  are the original reporter, you should at least include what problems this causes, and if you've found a work around, include that too.

---

### Post by Bowmore on 2011-10-24
> **cariboo907 said:**
> That bug is pretty sparse on details, if you  are the original reporter, you should at least include what problems this causes, and if you've found a work around, include that too.Nope, not my bug. 

However, in .xsession-errors I get the message:
> p11-kit: couldn't load module: /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directoryfor my x86_64 install and a corresponding message for the i386 install so there's sort of a multiarch issue here.

---

### Post by ventrical on 2011-10-27
Yep .. just got that..

p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory

---

### Post by effenberg0x0 on 2011-10-27
I have created a soft link at /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so pointing to /usr/lib/pkcs11/gnome-keyring-pkcs11.so too and so far everything is ok. I guess it's ok to leave it that way. Once other software learn to look in the right place, the soft link will just become useless, but won't interfere.

---


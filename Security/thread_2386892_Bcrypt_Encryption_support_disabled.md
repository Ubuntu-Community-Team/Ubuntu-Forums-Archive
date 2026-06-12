---
title: "Bcrypt: Encryption support disabled"
date: 2018-03-12
forum: Security
---

### Post by hrsetrdr on 2018-03-12
Encryption support disabled. See [URL="http://bugs.debian.org/700758"]http://bugs.debian.org/700758
[/URL]
So, according to the Bug report log, bcrypt is fixed in version bcrypt/1.1-8.1.    I have version 1.1-8.1 installed, but still get the "Encryption support disabled" message when attempting to encrypt a file with bcrypt.

Can anyone shed some light on this?

---

### Post by deadflowr on 2018-03-12
The fix *was* to disable the encryption support.

> bcrypt (1.1-8.1) unstable; urgency=low

  * Non-maintainer upload.
  * Disable RC broken encryption support (Closes: #700758). Make this a
    decrypt-only package for already created files.

 -- Agustin Martin Domingo <agmartin@debian.org>  Thu, 08 May 2014 11:46:38 +0200

This is the latest [changelog]("http://changelogs.ubuntu.com/changelogs/pool/universe/b/bcrypt/bcrypt_1.1-8.1/changelog") from Ubuntu's packages.

---

### Post by hrsetrdr on 2018-03-12
> **deadflowr said:**
> The fix *was* to disable the encryption support.

Yes, so I noticed.  ;)

 Well  old habits are hard to break, but I suppose I should move on to a different encryption utility , such as [ccrypt]("http://ccrypt.sourceforge.net/").

---

### Post by hrsetrdr on 2018-04-09
> **hrsetrdr said:**
> Yes, so I noticed.  ;)

 Well  old habits are hard to break, but I suppose I should move on to a different encryption utility , such as [ccrypt]("http://ccrypt.sourceforge.net/").

```
Selecting previously unselected package ccrypt.
(Reading database ... 248672 files and directories currently installed.)
Preparing to unpack .../ccrypt_1.10-4_amd64.deb ...
Unpacking ccrypt (1.10-4) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up ccrypt (1.10-4) ...
ERROR: ccrypt is broken - called emacs-package-install as a new-style add-on, but has no compat file.
Install ccrypt for emacs

```


Bummer.

[s]Anyone have an on-the-fly encryption app they would recommend?[/s]

Disregard, ccrypt does in fact work, not sure why that error was thrown.

---


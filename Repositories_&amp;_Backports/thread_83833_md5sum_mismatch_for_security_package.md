---
title: "md5sum mismatch for security package"
date: 2005-10-29
forum: Repositories &amp; Backports
---

### Post by mfyahya on 2005-10-29
I get the following error messages in synaptic when I reload the package list:

[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) MD5Sum mismatch
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:) MD5Sum mismatch

My source.list includes these two lines:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
The error goes away when I comment them out.
Thanks for any help.

---

### Post by dcstar on 2005-10-30
[QUOTE=mfyahya]I get the following error messages in synaptic when I reload the package list:

[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) MD5Sum mismatch
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:) MD5Sum mismatch

My source.list includes these two lines:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
The error goes away when I comment them out.
Thanks for any help.[/QUOTE]

I have the same deb line (apart from "main restricted **universe multiverse**") and they seem to download fine for me.

---


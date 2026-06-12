---
title: "BAD signature MD5SUMS.gpg at releases.ubuntu.com"
date: 2008-11-03
forum: Security
---

### Post by HandeH on 2008-11-03
Do somebody know why there was a bad MD5SUMS.gpg signature at [http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/) on last Friday at about noon UTC? I was amazed, when I saw different signatures in mirrors (e.g. Finnish). 

The good signature (currently in the servers/mirrors): 

```
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQBJCcVpRhgUM/u3VFERAhdqAKCfzvnFwRO3pd0S8gnJMz/rfPQkrQCdF4fT
eTfsPpyArePssB0idXBIrn4=
=PbZu
-----END PGP SIGNATURE-----
```

and its gpg output: 

```
$ gpg --verify MD5SUMS.gpg MD5SUMS
gpg: Signature made to 30. lokakuuta 2008 16:32:09 EET using DSA key ID FBB75451
gpg: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"

```

The bad one was: 

```
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQBJCa0YRhgUM/u3VFERAiWpAJ0byUwDgGES6RgtdrD4GfYG5cMXNACgjEQ7
Oi8AR0u76sNTQ7NBYcfrMTM=
=t3hg
-----END PGP SIGNATURE-----

```

and its gpg output: 
```
$ gpg --verify MD5SUMS.gpg MD5SUMS
gpg: Signature made to 30. lokakuuta 2008 14:48:24 EET using DSA key ID FBB75451
gpg: BAD signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"

```

I noticed something similar have happened also earlier: 
[http://ubuntuforums.org/showthread.php?t=764898](http://ubuntuforums.org/showthread.php?t=764898)

What do these examples mean? Could these kind of confusing mistakes (?) be prevented.

---


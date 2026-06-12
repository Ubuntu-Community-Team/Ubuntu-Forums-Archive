---
title: "Request: gnupg 1.4.1"
date: 2005-06-10
forum: Ubuntu Backports
---

### Post by Mez on 2005-06-10
I've already done this for my own use, but I think it'd be good to backport

Backported version from deb stable can be found here

[http://mezzle.info/ubuntu/](http://mezzle.info/ubuntu/)

---

### Post by Slo Mo Snail on 2005-06-10
There were problems with signature generating/checking because of changed handling of whitespace or something... if I remember correctly
has this been fixed?

---

### Post by Mez on 2005-06-10
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

Well, it seems to be generating signatures and verifying them ok for me

But, just incase, here's a signature created with my version of it.
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)

iD8DBQFCqhtFUNcmPOEdeBMRAh0LAKCGEkeY7GHMnedDgvgGtb6Bwqj5QACgs1pA
uVTYZzuRwWU2OqMwFPDeXjY=
=lFY4
-----END PGP SIGNATURE-----

If you can verify it, then problems are fixed :D

---

### Post by Mez on 2005-06-11
Update: URL is now: [http://www.sourceguru.net/ubuntu/hoary/](http://www.sourceguru.net/ubuntu/hoary/) (updating at the mo to give the right version number)

---

### Post by Slo Mo Snail on 2005-06-11
The problem was not that simple... it only happened when signing mails by some muas... for example sylpheed / sylpheed-claws had a problem with that

can somebody check if this is resolved?

---

### Post by Mez on 2005-06-11
thats actually a sylpheed problem, not a GPG problem

but

[http://sylpheed.good-day.net/changelog-devel.html.en](http://sylpheed.good-day.net/changelog-devel.html.en)

> The incompatibility of PGP signature between gnupg-1.2 and 1.4 when attached text has trailing spaces was fixed.

it was fixed in sylpheed 1.9.4

---

### Post by jdong on 2005-06-11
Is there a good reason for a gnupg backport? This is such a major part of the system, and I'm sure Ubuntu does security updates for GPG.

---

### Post by Mez on 2005-06-11
The main reason i want it is for direct trust model being implemented, and I'm running it perfectly well on hoary without a single problem

---


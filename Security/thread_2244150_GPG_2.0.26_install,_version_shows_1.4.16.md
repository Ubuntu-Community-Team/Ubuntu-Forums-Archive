---
title: "GPG 2.0.26 install, version shows 1.4.16"
date: 2014-09-14
forum: Security
---

### Post by Botruckle on 2014-09-14
I just downloaded the tarball source for GPG 2.0.26, checked the SHA1 sum, extracted it, did configure, make, had to install the libksba source (1.3.0), went back and made GPG again, then make install. 

All went fine without error other than warnings about unsafe ownership of configuration file gpg.conf

But when I type gpg --version, I see gpg (GnuPG) 1.4.16

Did I miss something somewhere?

---

### Post by bashiergui on 2014-09-14
I believe that's because you didn't uninstall the old version. Try ```
gpg2 --version
```

edit: or it might be called gnupg2.

---

### Post by Botruckle on 2014-09-14
Bingo! Does it come with Ubuntu? I don't recall installing the older version manually.

---

### Post by bashiergui on 2014-09-14
Yes the old version comes pre-installed.

---


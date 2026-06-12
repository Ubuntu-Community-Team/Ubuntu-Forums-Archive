---
title: "How do I hash checksum /boot?"
date: 2011-08-08
forum: Security
---

### Post by nrundy on 2011-08-08
Is it possible to get an md5sum of the contents of /boot? Then user can later take another hash and compare them to see if /boot has been tampered with? Like for sceanrios where everything is encrypted on the drive except for /boot?

---

### Post by Thewhistlingwind on 2011-08-08
[http://linux-howto-guide.blogspot.com/2009/10/directory-checksum.html](http://linux-howto-guide.blogspot.com/2009/10/directory-checksum.html)

Is that what your looking for?

I'm sure it'd be trivial to do something like:

the find + md5 thing > bootsumlast.txt

check that against a new sum stored in bootsum.txt and if they're the same, overwrite bootsumlast.txt

if they're not mail yourself a warning message.

EDIT: and of course you'd automate this.

---


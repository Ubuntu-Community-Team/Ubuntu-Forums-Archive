---
title: "OpenSSL version"
date: 2015-05-05
forum: Security
---

### Post by ichan2 on 2015-05-05
I know that the version of OpenSSL used in Ubuntu 15.04 is supposed to be 1.0.1f-1ubuntu11,
but when I type "openssl version" it says "1.0.1f January 6 2014."

Shouldn't the version reported be 1.0.1f-1ubuntu11?
How can I verify that the version of openssl is indeed the updated, patched version of openssl
if version reports that it is the old version?

Thanks!

---

### Post by deadflowr on 2015-05-09
```
openssl version -a
```
look at the built on date...

The -1ubuntu11 tag is part of Ubuntu's own packaging scheme and shouldn't be reflected in the actual package.

---


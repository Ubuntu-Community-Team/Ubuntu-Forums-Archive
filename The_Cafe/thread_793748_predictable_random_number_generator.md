---
title: "predictable random number generator"
date: 2008-05-14
forum: The Cafe
---

### Post by billgoldberg on 2008-05-14
[URL="http://lists.debian.org/debian-security-announce/2008/msg00152.html"]"This is caused by an incorrect
Debian-specific change to the openssl package (CVE-2008-0166).  As a
result, cryptographic key material may be guessable."

"Affected keys include SSH keys, OpenVPN keys, DNSSEC keys, and key
material for use in X.509 certificates and session keys used in SSL/TLS
connections.  Keys generated with GnuPG or GNUTLS are not affected,
though."
[/URL]
Kind of a big screw-up.

I believe ubuntu is/was also affected.

---

### Post by p_quarles on 2008-05-14
> **billgoldberg said:**
> I believe ubuntu is/was also affected.
[Yup.](http://ubuntuforums.org/showthread.php?t=792879)

---

### Post by schallstrom on 2008-05-14
To me this seems like the biggest screw-up I ever saw in Debian/Ubuntu! Think about it. Each and every SSL key generated on a Debian based system since 2006-09-17 is possibly vulnerable. If crackers new about this vulnerability it is likely that they had pretty much time to make use of it before the good guys got aware of the problem nowadays. To me this means, that I have to assume that all my SSL based communication (SSH, HTTPS, ...) of the last 1 to 2 years was possibly subject to eavesdropping and/or manipulation!

I love Linux and Ubuntu but if something like this had happened to a Microsoft product all of us free softwares users would have cheered and pointed our fingers at Mircosoft. I think, the matter should be taken very very serious.

---


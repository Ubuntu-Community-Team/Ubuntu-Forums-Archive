---
title: "hash link certificates"
date: 2011-11-17
forum: Server Platforms
---

### Post by salemhouda on 2011-11-17
Why apache use hash links to CAs certificates?
```
$  ll /etc/ssl/certs/ |more

lrwxrwxrwx 1 root root     26 2011-10-14 15:57 00673b5b.0 -> thawte_Primary_Root_CA.pem
lrwxrwxrwx 1 root root     29 2011-10-14 15:57 024dc131.0 -> Microsec_e-Szigno_Root_CA.pem

```

---

### Post by t3r0 on 2011-11-17
Hi,

The link hash is the checksum hash of that certificate with .0 in the end. Its used by apache (and others) to find the correct root certificate with out knowing the filename. 

The certs could be named like the hash codes, but with sym links its much easier for the maintainers of the ca-certficates.. And the human readable filename is visible to the admins..


- Tero

---


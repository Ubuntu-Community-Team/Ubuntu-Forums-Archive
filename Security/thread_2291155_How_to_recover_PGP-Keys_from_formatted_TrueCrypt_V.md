---
title: "How to recover PGP-Keys from formatted TrueCrypt Volume"
date: 2015-08-18
forum: Security
---

### Post by Philipp_Schwartz on 2015-08-18
Hello Community,

I somehow managed to quick-format a truecrypt encrypted flash drive with all my important files on it and of course I did not make a backup for a very long time. I uses "resore volume header" in truecrypt to get the volume back but unfortunately it was empty. Filesystem on the encrypted volume is ext3.
With the tool "scalpel" which is foremost-based i did get back most of my office documents.

Now I am trying to recover my pgp-keys including my own personal key. Therefor I changed the /etc/scalpel/scalpel.conf to make it look like this:

```
#---------------------------------------------------------------------    
# PGP (PRETTY GOOD PRIVACY)
#---------------------------------------------------------------------    
#
# PGP Disk Files
#    pgd    y    500000    \x50\x47\x50\x64\x4d\x41\x49\x4e\x60\x01
#
# Public Key Ring
    asc    y    100000    \x99\x00
# Security Ring
    sec    y    100000    \x95\x01
    sec    y    100000    \x95\x00
# Encrypted Data or ASCII armored keys
#    sec    y    100000    \xa6\x00
# (there should be a trailer for this...)
#    txt    y    100000    -----BEGIN\040PGP
```

When I run scalpel with this configuration I get about 150k *.asc and *.sec files. Actually I am looking for 5 public keys and one private key.

Do you guys know how I can get better results with my recovery?

Maybe you know a different recovery-tool I can use for this.

I am thankful for every help.
Thanks in advance

---


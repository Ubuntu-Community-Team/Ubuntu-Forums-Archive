---
title: "FW: How to enable Digital signature for the executable"
date: 2011-12-21
forum: Security
---

### Post by girishlc on 2011-12-21
Hi,

I am trying to add Digital signature for one of our product.
I am using elfsign and elfverify tool for signing and verifying tool.

./elfsign -f /root/ownme -c tester.cert -p tester.privkey 
./elfverify -f /root/ownme -c ca.crt

These are the two commands for signing and verifying;

here I am unable to do the verification; as it has mentioned above that need to use two different certificates for signing and verification.


Can anybody provide me the solution for;

1. How to create 2 certificates for signing and verifying.
2. Is there any other way in ubuntu we can add digital signature.

:confused:
Thanks,
Girish.L.C

---

### Post by lisati on 2011-12-21
Moved to own thread.

---


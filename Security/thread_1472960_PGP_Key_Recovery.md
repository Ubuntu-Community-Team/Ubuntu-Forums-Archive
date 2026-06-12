---
title: "PGP Key Recovery"
date: 2010-05-04
forum: Security
---

### Post by briml3y on 2010-05-04
I updated to 9.10 not to long ago from 8.10 but before I upgraded I backed up my entire home directory. In my previous installation I had created a PGP Encryption Key in the Passwords and Keys application. Is there anyway to recover it from my old home folder? 

Id also like to know where they are stored for future reference, unless they have to be exported.

---

### Post by FuturePilot on 2010-05-04
Go into your backup and find the .gnupg/ directory. Copy that into your new home directory. That also answers your second question.

---

### Post by briml3y on 2010-05-05
Thank you that definently worked! I had to unlock the file using ```
pgp filename
```
I appreciate the help

---


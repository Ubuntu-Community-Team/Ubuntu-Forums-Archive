---
title: "RSA strong auth PAM-module"
date: 2010-10-26
forum: Security
---

### Post by karnamonkster on 2010-10-26
Is it possible to install RSA strong auth PAM-module on UBUNTU 10.04 64bit client.
If yes then please let me know the procedure to do so.

---

### Post by fmfrisch on 2010-10-26
on x64 im not sure however i had pam on a x32 10.04 what ended up happening was that i got locked out of my own computer due to the bug with the unlocking of the keychain. Saw there was a fix out there for it. When it came to setting it up it wasnt that hard. PAM should be in the repos?

---

### Post by karnamonkster on 2010-10-27
Hi,

PAM module is there in the repos but my only concern is to get the RSA strong auth PAM module working on this 64 bit UBUNTU.
in case this requires any modifications to the installation script then please let me know.

---

### Post by fmfrisch on 2010-10-27
no (im absolutely no expert) but if it's from the x64 ubuntu default repo. That would indicate that it's deployable on x64 (?). However the unlocking of the keychain is likely to cause you some trouble. Solving that is above my knowledge

---


---
title: "EasyCrypt"
date: 2011-03-01
forum: Security
---

### Post by AbdRahim on 2011-03-01
I created a crypt file . Easy crypt can open it. I copy it to a new location and it says I have an invalid password, even though the folder containing it was copied to yet another location from which the crypt opens fine with the same password. If I delete the file that doesn't open. and copy it from the location the was just opened and closed. ays invalid password agian. It just does not seem to recognize the password in this location only, which is the main operating folder on this machine. I am using Maverick and Truecrypt 64 bit.

This is critical because it takes several days to upload this file to Dropbox. I would hate to need it one day , downloadit and not be able to open it. I question the usefulness of Dropbox anyhow if it is going to also take several days to down load my file (10GB).

---

### Post by AbdRahim on 2011-03-01
OK. It turns out that EasyCrypt cannot detect or close the open crypt. The drive cannot even be dismounted as root, because trucrypt is tying it up. One has to use truecrypt --dismount /volume name, in order to dismount the drive. This shuts down truecrypt, then it can open another crypt file. Hopefully this bug will get fixed.

---


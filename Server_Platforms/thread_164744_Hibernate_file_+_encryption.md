---
title: "Hibernate file + encryption"
date: 2006-04-23
forum: Server Platforms
---

### Post by Nuld on 2006-04-23
I am about to encrypt some parts of my file system (/tmp, /var, swap, ...) and would like to know where the hibernate file is stored in order to make sure that it's saved encrypted.

At which point during the boot process does the system need access to the hibernate file?

Thanks.

Btw, I am running the current Dapper beta in case that it matters.

---

### Post by LordHunter317 on 2006-04-23
The hibernate file is stored in your swap partition and AFAICT, swsup2 is incompatible with the current encrypted swap patches.

Why do you care?  Unless your encryption setup requires keys on startup, I can still get your data when I still the machine.

---

### Post by Nuld on 2006-04-25
Of course my encryption setup will require a passphrase on startup. Why bother with an encrypted file system if I let the key "lie around"?

The hibernate file is stored in my swap partition? But what if I have more physical memory than swap space? And what happens if the swap partition is already being used for, well, swapped memory?

---


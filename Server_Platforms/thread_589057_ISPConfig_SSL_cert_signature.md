---
title: "ISPConfig SSL cert signature"
date: 2007-10-23
forum: Server Platforms
---

### Post by dbrooke on 2007-10-23
Hello,  I installed ISPConfig successfully.. however, I chose to access it via https and my apache cert seems to be messed up:

error: (paraphrasing)
Could not establish an encrypted connection to [https://10.0.1.200:81/](https://10.0.1.200:81/) because the certificate presented has an invalid signature.

ideas for this noob?

TIA,
Donovan

---

### Post by dbrooke on 2007-10-28
I rebuilt the certificate (with the common name the same as the host name) and now it works well.

Donovan

---


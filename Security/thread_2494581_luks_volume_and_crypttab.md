---
title: "luks volume and crypttab"
date: 2024-01-20
forum: Security
---

### Post by aeronutt on 2024-01-20
I'd like to use a cryptab entry to open a luks container, but the key field in crypttab requires a filename.
I'd prefer the simplicity of pulling the luks key from seahorse. But it seems crypttab wants a file name, not a string.

Anyway to use a string  (eg "$(secret-tool lookup application cryptsetup)") for the key in crypttab?

FYI, this is for a data partition, not /home. I don't have /home encrypted so I can't just store a key file somewhere in /home.

---


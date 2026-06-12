---
title: "Clamd and ExcludePath"
date: 2009-10-22
forum: Security
---

### Post by mohnkern on 2009-10-22
I swear, every time there's an upgrade to clamav the ExcludePath directive changes. 


Right now I'm running .95.2 and if I put:

ExcludePath ^/fs/shared/
or 
ExcludePath ^//fs/shared

in clmad.conf and it doesn't exclude the directory /fs/shared

Has anyone had any success using the ExcludePath directive in clamd.conf?

---


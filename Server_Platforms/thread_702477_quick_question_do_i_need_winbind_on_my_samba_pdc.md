---
title: "quick question: do i need winbind on my samba pdc"
date: 2008-02-20
forum: Server Platforms
---

### Post by beaker15 on 2008-02-20
Hello, 
I Have a Samba PDC (3.0.26) running on an Ubuntu server (7.10) which will serve 8 Windows XP clients.

Q: Do i need winbind? 

or is that used when you have a windows DC.

---

### Post by mrsteveman1 on 2008-02-20
Normally machines on a local network hold a sort of election, and the machine with the newest OS becomes the domain master which then serves requests for machine names.

Winbind shouldn't be necessary but i do find my server sometimes goes invisible unless i force it to become a winbind domain master.

---

### Post by cdenley on 2008-02-20
It is used to join an active directory, or to resolve netbios names as if it was a domain name. It does not sound like you need it.

---


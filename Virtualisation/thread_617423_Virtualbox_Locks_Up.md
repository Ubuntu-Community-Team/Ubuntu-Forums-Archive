---
title: "Virtualbox Locks Up"
date: 2007-11-19
forum: Virtualisation
---

### Post by loupy on 2007-11-19
I saw a thread about a week ago about VirtualBox guest locking up randomly (and frequently) using a winxp guest, that would require the mouse to be moved to unfreeze it - I am unable to locate that thread again.

Does anyone know if this has been fixed or if there is a workaround?

I'm using Ubuntu 7.10 i386 and VirtualBox 1.5.2

---

### Post by loupy on 2007-11-19
seems like the issue may be related to 1.5.2 - I stepped it down to 1.5.0 and everything is working fine now.

---

### Post by Delvien on 2007-11-21
> **loupy said:**
> seems like the issue may be related to 1.5.2 - I stepped it down to 1.5.0 and everything is working fine now.

Disable any type of power management that is in the guest, that should fix it.

---

### Post by loupy on 2007-11-21
That did it - Thank you!!!!

---


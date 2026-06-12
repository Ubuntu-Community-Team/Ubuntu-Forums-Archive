---
title: "Did anyone else's hard drive type magically change?"
date: 2007-04-21
forum: The Cafe
---

### Post by Happy_Man on 2007-04-21
I just noticed this a couple minutes ago.... my hard drive had always been recognized as /dev/hda by Ubuntu 6.06 and 6.10, now it is recognized as /dev/sda by 7.04. Is that normal, and if so, why is it happening?

---

### Post by macogw on 2007-04-21
libata was changed and now all hard drives use sda

---

### Post by Swab on 2007-04-21
> **macogw said:**
> libata was changed and now all hard drives use sda

Except that my PATA drive is still hda!

---

### Post by LookTJ on 2007-04-21
> **Swab said:**
> Except that my PATA drive is still hda!is a PATA a legacy drive?

---

### Post by Swab on 2007-04-21
> **Taylor said:**
> is a PATA a legacy drive?

Well, it's an IDE drive.  Don't know if it's considered legacy quite yet.

---

### Post by prizrak on 2007-04-21
> **macogw said:**
> libata was changed and now all hard drives use sda

What he said :)

---


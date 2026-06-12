---
title: "Hotplug in Dapper 6.06: where is it?"
date: 2006-04-28
forum: The Cafe
---

### Post by uqbar on 2006-04-28
I'm not able to find the "usual" /etc/hotplug directory and cannot find a hotplug package as well.
I'm doing something wrong, but don't know what.
Any hint/help?
TIA.

---

### Post by Annagul on 2006-04-28
Hotplug is in nowhere. Now it's into udev.

---

### Post by uqbar on 2006-04-28
[QUOTE=Annagul]Hotplug is in nowhere. Now it's into udev.[/QUOTE]

Any hint on how to map hotplug based directions to udev?
Many thanks again.

---

### Post by Ptero-4 on 2006-10-25
you need the kernel 2.6.15 to get them automatically mapped (the udev mechanism requires that kernel).

---


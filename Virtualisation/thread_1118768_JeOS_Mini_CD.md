---
title: "JeOS Mini CD ?"
date: 2009-04-07
forum: Virtualisation
---

### Post by Cheesemill on 2009-04-07
Hi there guys,

Does anyone know if the there is a Mini CD iso image available for Ubuntu JeOS 8.04?

I don't want to have to update my VM's when I've finished installing them.

Ta,

Cheesemill

---

### Post by juancarlospaco on 2009-04-07
[B]sudo apt-get install python-vm-builder ; sudo vmbuilder --help

sudo vmbuilder kvm ubuntu --flavour virtual --suite hardy --debug[/B]

---

### Post by Cheesemill on 2009-04-08
> **juancarlospaco said:**
> [B]sudo apt-get install python-vm-builder ; sudo vmbuilder --help

sudo vmbuilder kvm ubuntu --flavour virtual --suite hardy --debug[/B]

Neither apt-get or aptitude can find the python-vm-builder package.

---

### Post by juancarlospaco on 2009-04-08
**sudo apt-get install vm-builder**

This has been re-writed in Python to allow possible non-ubuntu use *(no other distro have this tool at the moment)*.

---


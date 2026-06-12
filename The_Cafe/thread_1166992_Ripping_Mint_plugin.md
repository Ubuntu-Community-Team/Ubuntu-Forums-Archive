---
title: "Ripping Mint plugin"
date: 2009-05-22
forum: The Cafe
---

### Post by elliotn on 2009-05-22
I have a disk of Linux Mint and was wondering if its possible to rip the multimedia plugins and install them on ubuntu as the is no internet

---

### Post by tomcheng76 on 2009-05-22
try to insert your disc,then
```

sudo apt-cdrom add

```

The best is to get a Ubuntu CD via shipit! services as there is package dependency. :-)

---

### Post by elliotn on 2009-05-22
K let me run to me pc n try that out

---

### Post by elliotn on 2009-05-22
E: unable to locate any package files, perhaps this is not a Derbian CD

---

### Post by FuturePilot on 2009-05-22
> **tomcheng76 said:**
> try to insert your disc,then
```

sudo apt-cdrom add

```

That's not going to work for a Live CD as they don't contain any packages.

---

### Post by tomcheng76 on 2009-05-22
can you locate the .deb setup file in the disc?
then just
```

sudo dpkg -i /path/to/your/deb/setup/file.deb

```

---


---
title: "How to install from .iso"
date: 2011-01-22
forum: Wine
---

### Post by Cant on 2011-01-22
I have a game's .iso that I have to use to install it but I can't figure out how. Help?

---

### Post by lisati on 2011-01-22
Sometimes it's easier if you put the ISO file on disk. See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Others might be able to suggest ways of mounting the ISO file as if it were a CD without the need to burn it to CD.

---

### Post by Cant on 2011-01-22
> **lisati said:**
> Others might be able to suggest ways of mounting the ISO file as if it were a CD without the need to burn it to CD.

That's what I need, seeing that I have no CD/DVD big enough.

---

### Post by nitstorm on 2011-01-22
You can mount an iso image with the following command from the terminal. Open up Applications->Accessories->Terminal

```
mkdir somedirectory
sudo mount -o loop /path/to/the/iso/file /path/to/somedirectory
```

now u should be able to browse through the contents of the disc from the *somedirectory* folder itself

---


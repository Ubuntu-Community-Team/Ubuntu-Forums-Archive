---
title: "how to install office 07?"
date: 2009-04-25
forum: Wine
---

### Post by StormRoBoT2 on 2009-04-25
how to install office 07, i have a image file (.iso) file do i need to extract it first?

---

### Post by Dark Aspect on 2009-04-26
> **StormRoBoT2 said:**
> how to install office 07, i have a image file (.iso) file do i need to extract it first?

Type this into the terminal:

```
sudo apt-get install gmountiso
```

Afterwards go to Applications/System Tools/Gmount-iso and select the iso. You may need root privileges, if so try

```
sudo gmount-iso
```

---


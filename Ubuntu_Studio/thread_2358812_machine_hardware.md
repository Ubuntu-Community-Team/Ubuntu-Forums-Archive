---
title: "machine hardware"
date: 2017-04-17
forum: Ubuntu Studio
---

### Post by jwonch on 2017-04-17
I'm trying to install codeweaver software on studio 16.04. Can someone tell the command to print this out?

---

### Post by Autodave on 2017-04-17
I cannot d-l it here without giving my info, so........assuming that you already downloaded it, is it a .deb file? If so, the easiest way (in my opinion) to install it is to go to *synaptic *and get *gdebi *to use to install .deb packages.

I assume that you are familiar with *wine?* The software: not the liquor!)

---

### Post by Autodave on 2017-04-17
*software center *may also have *gdebi *available. If it doesn't, install *synaptic *from there.

---

### Post by howefield on 2017-04-17
> **jwonch said:**
> I'm trying to install codeweaver software on studio 16.04. Can someone tell the command to print this out?

```
sudo apt install ~/Downloads/crossover_16.2.0-1.deb
```

This assumes that the deb package is located in your ~/Downloads folder and that the file name is crossover_16.2.0-1.deb, if either of those two pieces of information is incorrect then amend the command to suit.

---


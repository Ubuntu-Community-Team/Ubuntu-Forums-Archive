---
title: "Better Hardware detection."
date: 2008-10-09
forum: Ubuntu Brainstorm
---

### Post by Slug71 on 2008-10-09
I'd like to see Hardware detection be a little better. A few times i have received Nvidia updates via Update Manager yet i have ATI. 
Just wasted space for me.

---

### Post by cdenley on 2008-10-09
```

sudo apt-get remove nvidia-*

```

---

### Post by mizzouxc on 2008-10-09
If you need to clear more disk space, you can use

     sudo apt-get autoclean

---

### Post by Slug71 on 2008-10-09
I have plenty of space but it just doesn't make sense that i would get nvidia related stuff and vice versa for a person using nvidia getting ATI.

---

### Post by cdenley on 2008-10-10
> **Slug71 said:**
> I have plenty of space but it just doesn't make sense that i would get nvidia related stuff and vice versa for a person using nvidia getting ATI.

Packages are packages. The updater doesn't see which packages are for hardware, or which you actually use, just what you have installed and what there are updates for. The packages should be installed by default so the user can switch video cards without having to install packages.

---

### Post by Slug71 on 2008-10-10
Gotcha, thanks.

---


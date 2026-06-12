---
title: "Deleting gnome shell extensions."
date: 2017-03-26
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2017-03-26
How do I delete the pre-installed gnome shell extensions from the terminal, in ubuntu gnome 17.04

Henry

---

### Post by cariboo on 2017-03-26
Remove the following directory

```
~/.local/share/gnome-shell/extensions/
```

then resart the computer.

---

### Post by Hewjr100 on 2017-03-26
Ok will give it a shot.

Henry

---

### Post by jbicha on 2017-03-27
They are from the gnome-shell-extensions package, but that package also provides GNOME Classic and currently ubuntu-gnome-desktop depends on that.

---


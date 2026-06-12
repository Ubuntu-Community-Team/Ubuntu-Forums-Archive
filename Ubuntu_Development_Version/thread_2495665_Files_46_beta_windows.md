---
title: "Files 46 beta windows"
date: 2024-02-26
forum: Ubuntu Development Version
---

### Post by Claus7 on 2024-02-26
Hello,

Files 46 beta is available under ubuntu noble development. I would like to mention one new(?) feature that reminded some very long days in the distant past, where, while using windows, if I clicked an option of a window that raised a new window on top, I hadn't had the opportunity to see what it was happening in the original window that was placed below.

With new Files 46, if someone opens properties, then if someone tries to remove the properties window, the entire Files will be removed. I think that this is mostly a feature rather than a bug, yet I do not get why this was introduced in the first place. I do not think that is ubuntu specific, yet gnome in general. I do not know if it is intended to stay for other applications as well.

Regards!

---

### Post by corradoventu on 2024-02-27
Try with: ```
gsettings set org.gnome.mutter attach-modal-dialogs false
```

---

### Post by Claus7 on 2024-02-27
Hello,

> **corradoventu said:**
> Try with: ```
gsettings set org.gnome.mutter attach-modal-dialogs false
```

thank you! I tested it both on mantic and noble and it worked like a charm!

Regards!

---


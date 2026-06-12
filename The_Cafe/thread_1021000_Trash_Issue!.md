---
title: "Trash Issue!?"
date: 2008-12-24
forum: The Cafe
---

### Post by kevin11951 on 2008-12-24
I have a file stuck in my trash bin that wont go away, how can i manually delete it?

---

### Post by tuxxy on 2008-12-24
Try this

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by chris4585 on 2008-12-24
I believe this happens when you run nautilus with sudo? use gksu instead

---

### Post by kevin11951 on 2008-12-24
> **tuxxy said:**
> Try this

```
sudo rm -rf ~/.local/share/Trash/files/*
```

thank you, that worked perfectly!

---


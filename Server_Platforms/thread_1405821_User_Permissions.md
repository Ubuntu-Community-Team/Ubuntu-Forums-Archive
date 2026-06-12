---
title: "User Permissions"
date: 2010-02-13
forum: Server Platforms
---

### Post by grouchotron on 2010-02-13
Is it possible to edit a user so that he can only work in his home directory and one or two others? Thanks for any answers.

---

### Post by Bachstelze on 2010-02-13
Yup, just do something like

```
sudo chown -R :jack /some/dir
sudo chmod g+w /some/dir
```

Replace jack with your friend's username (do **not** forget the colon!) and he will have write access to /some/dir and everything under it.

---


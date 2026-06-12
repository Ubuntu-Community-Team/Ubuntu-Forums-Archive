---
title: "Access encrypted home folder from Recover Mode"
date: 2010-11-26
forum: Security
---

### Post by Paddy Landau on 2010-11-26
I logged in to Recover Mode ("Drop to root shell prompt") this morning to do something. Naturally, I wanted access to my encrypted home folder.

The README file says to run ecryptfs-mount-private. However, that command returns an error:
"ERROR: Encrypted private directory is not setup properly."

This cannot be correct, because if I log in normally, I get my home folder without any problem.

How can I access my encrypted home folder when I boot via Recover Mode?

---

### Post by FuturePilot on 2010-11-26
Try su to your user.

---

### Post by Paddy Landau on 2010-11-26
I used the following, which automatically decrypted the folder for me.
```
sudo su paddy
```Thank you.

---


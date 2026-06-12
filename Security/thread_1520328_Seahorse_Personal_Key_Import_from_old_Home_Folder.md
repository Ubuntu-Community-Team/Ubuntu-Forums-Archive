---
title: "Seahorse Personal Key Import from old Home Folder"
date: 2010-06-29
forum: Security
---

### Post by Jabz.biz on 2010-06-29
Hi, 

last week I decided to not just run dist-upgrade, but give the Lynx a completely fresh install. Before that I've only copied my home folder to an external hard-drive.

Now that I'm on Ubuntu 10.04 I have no clue how to import my old personal key and the passwords from the backup (my old home folder).

Does anyone have an idea? 
Thanks for your help!

---

### Post by FuturePilot on 2010-06-29
Copying ~/.gnupg ~/.ssh and ~/.gnome2/keyrings from your backup to your home directory should do the trick.

---

### Post by Jabz.biz on 2010-06-30
This did the trick. Thanks a billion, you made my day!

---

### Post by amarendra on 2011-05-15
> **FuturePilot said:**
> Copying ~/.gnupg ~/.ssh and ~/.gnome2/keyrings from your backup to your home directory should do the trick.
Had not saved my .gnome2/keyrings. Copying .gnupg and .ssh. Hope it works.

---


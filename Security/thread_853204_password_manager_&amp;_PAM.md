---
title: "password manager &amp; PAM"
date: 2008-07-08
forum: Security
---

### Post by mriedel on 2008-07-08
Is there a password manager (like for example revelation) that supports PAM? Specifically, I'd like to use pam_usb to authenticate to my password manager.

---

### Post by mriedel on 2008-07-10
bump

---

### Post by lisati on 2008-07-10
If I have understood the question properly, there is a keyring manager - see System->Administration.. Relevant to this is [http://ubuntuforums.org/showthread.php?t=463621&highlight=keyring](http://ubuntuforums.org/showthread.php?t=463621&highlight=keyring)

---

### Post by mriedel on 2008-07-10
Afaik, gnome-keyring-manager only stores PGP and SSH passwords, along with passwords for programs that support it, like the network manager. Please correct me if I'm wrong.

---

### Post by mriedel on 2008-07-11
In addition, you can't authenticate to gnome-keyring-manager through PAM(_usb)

---


---
title: "encrypted private folder"
date: 2009-01-02
forum: Security
---

### Post by anv on 2009-01-02
this morning tried to use my text files but noticed that Private folder inside was:

=====================================

THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA --  Run mount.ecryptfs_private to mount again

=====================================

anv@pine:~$ mount.ecryptfs_private
keyctl_search: Required key not available

=====================================

öh hmm... HEEEEEEEELP

---

### Post by RansomStark on 2009-01-02
try [http://ubuntuforums.org/archive/index.php/t-947619.html](http://ubuntuforums.org/archive/index.php/t-947619.html)

---

### Post by tubbygweilo on 2009-01-02
A bit more general information on encrypted private folder information and workings [community]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") & [wiki]("https://wiki.ubuntu.com/EncryptedPrivateDirectory") views of this topic.

---

### Post by anv on 2009-01-04
ok I managed to open Private folder. Next, how to get rid of gnome-keyring manager? what other keys it can possibly manage? can I uninstall it safely and have working system even so? I try to use xfce4 as much as possible and I can manage this private folder without it if it is only task where it is used.

---


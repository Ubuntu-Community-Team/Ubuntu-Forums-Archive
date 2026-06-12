---
title: "TIP: If Gigolo only offers &quot;Custom Location&quot;"
date: 2011-10-18
forum: Tutorials
---

### Post by Jose Catre-Vandis on 2011-10-18
If you run Xubuntu, connecting to remote filesystems is supported by using the Gigolo program. For me, on installs up to 11.04, this has worked out of the box, but with a clean install of 11.10 all Gigolo would offer me was a "Custom Location" (not much good if you want SSH / Samba-Windows / FTP / Obex / WebDav shares).

The problem is probably caused by gvfs-backends not being installed, so

```
sudo apt-get install gvfs-backends
```

and Gigolo should work properly. :D

Link to a more detailed page on getting network shares with Gigolo, nice work from user **Kronalias**

[http://ubuntuforums.org/showpost.php?p=11382873&postcount=2](http://ubuntuforums.org/showpost.php?p=11382873&postcount=2)

---

### Post by Sionide on 2011-10-25
Worked for me on Xubuntu 11.10 ( Gigolo 0.4.1 on a default install )

---


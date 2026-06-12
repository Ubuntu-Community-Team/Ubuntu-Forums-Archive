---
title: "Xfce 4.4"
date: 2007-02-27
forum: Repositories &amp; Backports
---

### Post by x1a4 on 2007-02-27
Hi,

Just curious, now that Xfce 4.4 is officially out, when can all of us Xubuntu users expect to see it in the repositories?  

Thank you.

---

### Post by picpak on 2007-02-27
You can put this in your /etc/apt/sources.list:

```
deb http://ubuntu.tolero.org/ edgy xfce-4-4-0
```

and then run

```
sudo apt-get update
sudo apt-get upgrade
```

Then you'll get Xfce 4.4.

---


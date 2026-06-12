---
title: "Ubuntu Mirror"
date: 2005-03-17
forum: Server Platforms
---

### Post by Myles3 on 2005-03-17
Hi I have about 5 Desktop's at my office all installed with Ubuntu. When I have to update them all I have to download and use so much bandwidth. I want to setup a Local Mirror to download all the new updates. Can this be done?

---

### Post by tonym on 2005-03-17
[QUOTE=Myles3]Hi I have about 5 Desktop's at my office all installed with Ubuntu. When I have to update them all I have to download and use so much bandwidth. I want to setup a Local Mirror to download all the new updates. Can this be done?[/QUOTE]
 Yes.  I use the debmirror package to create my own partial mirror.  You can choose which architectures / release / sections you want to copy.  Point it at archive.ubuntu.com

Regards

Tony Middleton

---

### Post by Myles3 on 2005-03-17
What do you use to get all the files? Rsync?

---

### Post by tonym on 2005-03-18
debmirror can use a number of methods - ftp,  http and I think rsync.  When you use ftp/http it first downloads the lists of packages in the repository and works out which packages are new or have new versions and just downloads those.  If you track both warty and hoary its clever enough to only download a package once if the version hasn't changed.

---

### Post by jek on 2005-10-13
What is a good choice of host to use for the sync?

---


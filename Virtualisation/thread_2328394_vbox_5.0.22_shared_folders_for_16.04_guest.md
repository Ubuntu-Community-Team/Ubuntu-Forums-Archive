---
title: "vbox 5.0.22 shared folders for 16.04 guest"
date: 2016-06-20
forum: Virtualisation
---

### Post by JKyleOKC on 2016-06-20
I'm attempting to evaluate and become familiar with the 16.04 LTS release of Xubuntu, in a VBox VM running in VBox 5.0.22. The shared folders appear in /media with a "sf_" prefix to their names, owned by root with group of vboxsf, and no read permissions for "others." I've added myself to the vboxsf group, but still get "access_denied" errors when I try to use the folders. "sudo chown jk:jk" has no effect, suggesting that these folders are immutable.

Previous versions did not have this problem; shared folders set to auto-mount mounted with the uid/gid of the logged-in user and could be accessed like any other. What has changed, and how can I use the 16.05-LTS version?

---

### Post by mehrdadsami on 2016-06-20
hi .... first join the yourself user to vboxsf user and  Once logoff and login ... .

---


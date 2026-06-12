---
title: "Ignore directories in Ubuntu-One"
date: 2010-09-25
forum: Ubuntu One (CLOSED)
---

### Post by martin-probst on 2010-09-25
Hi there,
is there any way to ignore whole directories in Ubuntu-One? I figured out that you can use /etc/xdg/ubuntuone/syncdaemon.conf to ignore files by adding a regex to ignore.default, but I assume this only applies to files. So, how can I avoid the syncing of some subdirectories of my synced folders? I guess I could use symlinks as a workaround, because I read somewhere that Ubuntu-One wouldn't follow them, but I'm hesitating to do so as someone stated that this feature will be added in some upcoming release.

Thanks, Martin

---

### Post by duanedesign on 2010-09-28
You are correct in assuming that only applies to files. Currently there is no way to do this for folders. However it is something that  frequently comes up so I am sure it is being considered.

cheers,
duanedesign

---


---
title: "Dash Downloads + unionfs-fuse"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by 8Kuula on 2012-04-14
H!

Im using unionfs-fuse to overlay two directories to one
```
unionfs-fuse $HOME/.local-Downloads=RW:$HOME/mnt/gatekeeper/Downloads=RW $HOME/Downloads
```

So problem is that downloads in dash do not show up or search files & folders do not find files that are created in $HOME/.local-Downloads or $HOME/mnt/gatekeeper/Downloads until I actualy open (atleast) file.

Dash downloads do not like unionfs-fuse? How to go around that?

---

### Post by cariboo on 2012-04-14
Zeitgeist is what logs your activities, try activity-log-manager to add your non-standard download directory.

---

### Post by 8Kuula on 2012-04-14
How I add from activity-log-manager? Or am I blind? Only can remove directories from there.

---


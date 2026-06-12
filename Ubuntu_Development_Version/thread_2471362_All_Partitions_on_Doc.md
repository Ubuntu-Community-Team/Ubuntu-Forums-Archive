---
title: "All Partitions on Doc"
date: 2022-01-27
forum: Ubuntu Development Version
---

### Post by VMC on 2022-01-27
Since last update, all my linux partitions show up on the Doc. They didn't before. Can't find how to remove them.
They are not mounted from Nautilus. Some conf file has apparently changed this.

The solution: 
```
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts-only-mounted true
```

---


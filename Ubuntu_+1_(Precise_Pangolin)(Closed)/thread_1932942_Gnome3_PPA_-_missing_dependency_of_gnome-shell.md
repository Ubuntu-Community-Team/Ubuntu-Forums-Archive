---
title: "Gnome3 PPA - missing dependency of gnome-shell"
date: 2012-02-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-02-28
Now that gjs_1.31.10 has been uploaded into the Gnome3 PPA, the Gnome-shell desktop environment does not load properly. There are no panels, for instance.

This is because of the new gjs (1.31.10).
You need to install the package gir1.2-gjs-1.0, although no package is set to depend on it.
It should be the dependency of the package gnome-shell.

So, installing gir1.2-gjs-1.0 solves this issue.

---

### Post by jbicha on 2012-02-28
Thanks, I'm uploading a fixed gnome-shell to the PPA now.

---

### Post by Harry33 on 2012-02-28
> **jbicha said:**
> Thanks, I'm uploading a fixed gnome-shell to the PPA now.

Thanks Jeremy.
This is solved then.

---


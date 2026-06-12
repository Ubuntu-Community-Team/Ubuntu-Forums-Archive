---
title: "Gnome3 PPA Nautilus_3.5.92"
date: 2012-09-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-09-21
The Nautilus_3.5.92 package (from Gnome3 PPA) cannot be installed.

The error says the package libnautilus-extension1a_3.5.92 is uninstallable
because it contains the same file
(/usr/lib/nautilus/nautilus-convert-metadata)
than the package nautilus_3.5.92.

---

### Post by xebian on 2012-09-21
> **Harry33 said:**
> The Nautilus_3.5.92 package (from Gnome3 PPA) cannot be installed.

The error says the package libnautilus-extension1a_3.5.92 is uninstallable
because it contains the same file
(/usr/lib/nautilus/nautilus-convert-metadata)
than the package nautilus_3.5.92.

Just force it and everything will be fine.

---

### Post by Harry33 on 2012-09-22
No it won't, I tried it manually with dpkg.
The version I am talking about is 3.5.92-0ubuntu1~ubuntu12.10.1

But now there is a new version in Gnome3 PPA (3.5.92-0ubuntu1~ubuntu12.10.2) which works just fine.

So, this is solved.

---

### Post by mc4man on 2012-09-22
For any future the force generally works in these situations if using 
--force overwrite
So from when the upgrade 1st showed & failed in synaptic, this took care of - 
sudo dpkg -i --force overwrite  /var/cache/apt/archives/libnautilus-extension1a_1%3a3.5.92-0ubuntu1~ubuntu12.10.1_amd64.deb

---


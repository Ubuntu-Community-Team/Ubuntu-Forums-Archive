---
title: "apt-get not working"
date: 2006-06-29
forum: Server Platforms
---

### Post by ExMachina on 2006-06-29
Im getting an error.
i editedotu the CD line and uncommented the universal lines.

E: Could not get lock /var/lib/dpkg/lock - open ( 11 resource temp. unavailavble)
E: Unable to lock the admin directory (/var/lib/dpkg) is another process using it?

someone told me to restart im STILL gettign that erro i cna run apt-get install <<

---

### Post by johnc4510 on 2006-06-29
Usually when it can't get a lock, it is because you have another version of the package manager open. Such as Synaptic or Update Manager. You can only have one open and running at a time. Apt-Get is the other package manager.

---


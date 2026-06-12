---
title: "Backup (Deja dup) broken?"
date: 2012-01-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fallenshadow on 2012-01-18
Hey there,

Im using Ubuntu 12.04 Alpha fully updated. I have a problem as I cannot seem to use the backup tool to restore my backups.

When I try to do it a freeze is caused and the hard disk and processor usage go crazy. I have to power my PC down by the button to cancel the restoration process.

Anyone else experience this?

---

### Post by fallenshadow on 2012-01-23
I think my issue was caused by not having a swap partition as it was accidentally deleted. Therefore it was pointing Ubuntu to a swap space not existing anymore.

Since then I created a swap partition and linked up to it. Backup is restoring my data now.

Consider this solved. :)

---


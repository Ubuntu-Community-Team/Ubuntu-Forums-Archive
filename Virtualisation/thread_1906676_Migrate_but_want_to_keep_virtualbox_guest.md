---
title: "Migrate but want to keep virtualbox guest"
date: 2012-01-09
forum: Virtualisation
---

### Post by leclerc65 on 2012-01-09
I have Win 7 as guest running under Natty Virtualbox.
I plan to migrate to 12.04 (when available) - clean install. I have separate '/' and '/home' partition. Can I keep the virtual Win 7 intact and how ?
Thanks.

---

### Post by wildmanne39 on 2012-01-09
Hi, you have a couple of options since you have a separate home partition.

1. Export windows seven guest to an external device then all you have to do is import it again when the install is done.

2. When you do a clean install do not format your home partition choose it as the home partition for your new installation, however I still recommend exporting windows and making a back up of your other data in the home partition just in case something goes wrong.
Thanks

---

### Post by CharlesA on 2012-01-10
Exporting will merge any snapshots you have into a "flat" image.

You could just copy ~/.VirtualBox and ~/VirtualBox VMs to external media and copy them back after you have reinstalled.

---

### Post by leclerc65 on 2012-01-10
Thanks, I will mark the thread as solved for now.

---


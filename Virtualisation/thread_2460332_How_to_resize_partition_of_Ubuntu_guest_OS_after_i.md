---
title: "How to resize partition of Ubuntu guest OS after increasing virtual disk size"
date: 2021-04-07
forum: Virtualisation
---

### Post by hooby3 on 2021-04-07
I want to increase the size of the virtual disk for an Ubuntu (XUbuntu) guest OS.
I used the VirtualBox media manager to increase the disk size from 200GB to 300GB
When booting the guest OS, dmesg and gparted still show 200GB.  Refreshing disk info with gparted does not change this.

Is there something that I need to do to trigger Ubuntu that the disk size has changed?

Windows10 host OS, FYI.

Thanks!

---

### Post by hooby3 on 2021-04-07
Found my own answer.

Under Virtual Media Manager, I had selected the root .vdi file, and made the change there.  Expanded under this, I guess, are snapshots.  I increased the last snapshot vdi to 300GB, and now I see it under Ubuntu.

---


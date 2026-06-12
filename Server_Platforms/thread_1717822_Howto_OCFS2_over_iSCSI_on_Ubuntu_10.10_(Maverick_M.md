---
title: "Howto: OCFS2 over iSCSI on Ubuntu 10.10 (Maverick Meerkat)"
date: 2011-03-30
forum: Server Platforms
---

### Post by dev.null on 2011-03-30
Hey guys,

I just finished up a OCFS2 install over iSCSI and figured I'd come back and document it step-by-step since I didn't see a howto along the way.

I'd love to hear your feedback - especially if you have some corrections or something I can add that would make the howto more complete.

Thanks!

[http://www.richardpickett.com/ocfs2-over-iscsi-on-ubuntu-10-10-maverick-meerkat](http://www.richardpickett.com/ocfs2-over-iscsi-on-ubuntu-10-10-maverick-meerkat)

---

### Post by trexmaster on 2011-05-18
Hi,

Fine tutorial thanks a lot, just the fs type missing at the end in the line to add to fstab:
/dev/sdc1 /mnt/ocfs2 **ocfs2 **_netdev 0 0

---

### Post by rnldpj on 2011-08-11
Also checkout the following url :D

[http://jackal777.wordpress.com/2011/08/10/ocsf2-iscsi-centralized-storage-in-ubuntu-10-10/](http://jackal777.wordpress.com/2011/08/10/ocsf2-iscsi-centralized-storage-in-ubuntu-10-10/)

---


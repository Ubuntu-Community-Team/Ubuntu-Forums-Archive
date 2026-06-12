---
title: "Encrypted drive after kernel update"
date: 2010-07-05
forum: Security
---

### Post by rpacker on 2010-07-05
Is there a trick to mounting the encrypted drive after a kernel update? It seems like it is just skipping the passphrase screen for all new kernel updates and trying to boot. The original kernel (from install) works but no new ones, it just goes to a black screen with initramfs> and says something about devmapper not finding what it needs. Apparently I need to do whatever devmapper needs, just not sure what that is, there must be a thread or howto on this I missed... anybody got a link?

---

### Post by john stiles on 2013-04-09
Similar/same issue of black screen after restart for a kernel upgrade to 3.5.0-27 upon a fully encrypted Ubuntu 12.10 disk. System will still boot into old kernel. It appears the restart does not update the grub config files completely, so run:

sudo upgrade-grub

Alls well that ends well.

---

### Post by Elfy on 2013-04-09
I suspect it ended nearly 3 years ago when this thread was last posted in.

Closed

---


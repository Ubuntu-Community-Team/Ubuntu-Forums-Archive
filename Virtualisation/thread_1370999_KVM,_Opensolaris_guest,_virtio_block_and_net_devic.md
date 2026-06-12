---
title: "KVM, Opensolaris guest, virtio block and net devices. Anyone succeded?"
date: 2010-01-02
forum: Virtualisation
---

### Post by andliuk on 2010-01-02
Hi guys!

Given the lack of a reliable FS in linux (BTRFS still not available), I set up a working paravirtualized Opensolaris xen guest that runs nearly at native speed on Ubuntu 9.04 dom0.
This solution requires some workarounds, and also xen is not supported anymore on ubuntu. It's better watch out for something else.

I would like to setup an Ubuntu 9.10 with KVM, and run an Opensolaris guest on the top of it. The Opensolaris guest acts mostly as a NAS, so LAN and disk performances MUST be good. It turns out that the only way to paravirtualize IO (disk and net) on KVM is using the virtio device driver, but man it's hard to find good docs about it. Any advice or link?

Has anyone succeded setting up something like that?

Thanks in advance, 

  Andrea

---


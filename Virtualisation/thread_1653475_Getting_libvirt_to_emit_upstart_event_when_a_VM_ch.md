---
title: "Getting libvirt to emit upstart event when a VM changes status"
date: 2010-12-26
forum: Virtualisation
---

### Post by destrius on 2010-12-26
Hi,

I'm wondering if there is currently any way to get libvirt to emit an upstart event (e.g. using the emit program) indicating that a VM has started or stopped. Similar to how events are emitted when network devices go up and down.

I need this feature because I want my host to perform certain actions whenever a VM's status changes, and I figured upstart would be the "right" way to do it.

Does anybody know if there's a way to configure hooks in libvirt which get run when a VM starts or stops? With that I could just add a script to run "emit" in the hook. Alternatively if there's currently no way of doing it, I might try hacking at libvirt to add such a feature.

Thanks!

destrius

---


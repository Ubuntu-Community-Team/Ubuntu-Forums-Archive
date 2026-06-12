---
title: "[SOLVED] KVM - Community Docs Question?"
date: 2008-06-06
forum: Virtualisation
---

### Post by hopelessone on 2008-06-06
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

Under the section:

**How-to edit the attributes of a Virtual Machine (add CPUs, RAM)**

it says To add CPUs to one VM, you need to **edit the '/etc/libvirt/qemu/yourvm.xml' file...**

Well theres nothing there? where else should i look/create?

Thanks you in advance...

---

### Post by hopelessone on 2008-06-06
its there after re-install musta done something wrong the first install...

---

### Post by ktulu73 on 2008-06-07
If you run a VM as normal user, the xml is stored in .libvirt of your home directory.

---


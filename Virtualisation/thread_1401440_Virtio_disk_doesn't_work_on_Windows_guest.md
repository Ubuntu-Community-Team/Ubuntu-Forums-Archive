---
title: "Virtio disk doesn't work on Windows guest"
date: 2010-02-08
forum: Virtualisation
---

### Post by OlegVekhov on 2010-02-08
Hi! I'm using Ubuntu 9.10 as the host os, on AMD 64 X2 6000+ with 6 GB of RAM.

Libvirt+KVM.

Latest Virtio drivers from RedHat (dated 01.2010, digitally signed for all windows systems)

Network virtio devices works perfectly.

Windows drivers for virtio block device installs, but can't initialize with "Code 10. The device can not start".

Tried systems: Windows 2008 R2 x64, Windows 2003 R2 x64, Windows XP x32. Errors are the same.

Fedora or Ubuntu installed on virtio block device works perfectly.

Where should I look?

---

### Post by vadikgo on 2010-04-30
This is bug in qemu. Look here
[http://www.mail-archive.com/kvm@vger.kernel.org/msg23718.html](http://www.mail-archive.com/kvm@vger.kernel.org/msg23718.html)

Upgrade to the Ubuntu "Lucid Lynx" 10.04 LTS, it has new qemu.

---


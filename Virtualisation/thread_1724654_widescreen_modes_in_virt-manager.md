---
title: "widescreen modes in virt-manager"
date: 2011-04-08
forum: Virtualisation
---

### Post by liverpoolfc on 2011-04-08
I've been looking for answers to this, and I've found several leads, but none that actually solve the problem.

The question is: is it possible to get widescreen modes in a VM when you're using virt-manager?

From what I've read, you need to pass the "-vga std" option to QEMU, but I haven't found a way to do that.  I've tried converting my libvirt xml definitions into native QEMU launcher scripts, so that I can pass that option in, but I can't get the networking to work that way be cause the bridge setup that libvirt uses doesn't seem to work when you launch a VM using QEMU.

Does anyone know a solution to this?

Thanks.

---

### Post by liverpoolfc on 2011-04-11
Never mind, I guess I should have done a little less reading and a little more leg-work.  Setting the video to "cirrus" gives me widescreen modes.

---


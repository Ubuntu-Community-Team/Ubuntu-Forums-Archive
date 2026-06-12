---
title: "ubuntu-vm-builder fails to include the ubuntu-desktop package"
date: 2009-12-01
forum: Virtualisation
---

### Post by aleb on 2009-12-01
I used ubuntu-vm-builder to create a virtual machine, and it boots fine, but it is headless (no X). I'm running this command to create a virtual machine containing the "ubuntu-desktop" package, but it does not work:
```
ubuntu-vm-builder kvm karmic --components main,universe --user x --pass x --mem 256 --rootsize 8192 --hostname cv1 --ip 192.168.0.10 --flavour generic --addpkg ubuntu-desktop -d cv1 --libvirt qemu:///system --suite karmic
```

This is the relevant error I think:

```
2009-12-01 16:28:35,742 INFO    : umount: /tmp/vmbuilderFFOGjb/root/proc: device is busy.
2009-12-01 16:28:35,743 INFO    :         (In some cases useful info about processes that use
2009-12-01 16:28:35,743 INFO    :          the device is found by lsof(8) or fuser(1))
2009-12-01 16:28:35,744 INFO    : Cleaning up
2009-12-01 16:28:49,527 INFO    : rm: cannot remove `/tmp/vmbuilderFFOGjb/root/proc/asound/DX': Operation not permitted
[a lot of "rm: cannot remove `/tmp/vmbuilderFFOGjb/root/proc/...': Operation not permitted" messages follow]

```

Any idea how I can make it work?

Edit:
I created a virtual machine with no extra package, then started it, connected to it and "sudo apt-get install ubuntu-desktop". Seems to work.

---


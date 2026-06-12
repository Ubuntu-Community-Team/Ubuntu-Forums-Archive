---
title: "moved libvirt-folder doesn't work"
date: 2016-05-24
forum: Virtualisation
---

### Post by akela68 on 2016-05-24
Hi,

i use Ubuntu 16.04 LTS and use virt-manager to create a vm -> with standard-installation this works fine.
Now i will place the folder /var/lib/libvirt to a subdir on a bigger partition. I create a directory /bigdisk/libvirt and create a symbolic link /var/lib/libvirt to this directory.
The permissions i set with chmod/chown.

With this configuration i cannot create vm's. It will be produce the follow error:

```
Failed to bind socket to /var/lib/libvirt/qemu/domain-hugo/monitor.sock: Permission denied
```

bye Andreas

---

### Post by TheFu on 2016-05-24
What sort of file system is /bigdisk/libvirt?  Also, please post the permissions - ls -al for it and verify the symlink is working.

---


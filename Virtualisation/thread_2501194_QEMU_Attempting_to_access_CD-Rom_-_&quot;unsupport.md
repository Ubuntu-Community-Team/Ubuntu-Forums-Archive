---
title: "QEMU: Attempting to access CD-Rom - &quot;unsupported configuration&quot;"
date: 2024-09-26
forum: Virtualisation
---

### Post by Rick St. George on 2024-09-26
Running QEMU Virtual Machine Mgr. with Windows, and my MS Office program, since upgrade OS / Virtual Box to QEMU, wants my CD-Rom to verify installation. With CD in tray, I see it on Ubuntu v22.04 side, and in Virtual Mgr / IDE CDROM select it, but it shows ....

"Errors were encountered changing permission for the following directories:
/media/Stephen/OFFICE10
Errno 1 Operation not permitted
Errno 30 Read Only File System

It is very likely VM will fail to start up"

Click OK and this pops up;

"Error changing VM configuration:
unsupported configuration:
storage type 'dir' requires use of storage format 'fat' "

Yet it accepts source path: /home/stephen/Downloads/ISO/virtio-win-0.1.100.iso
How do I get around this limitation? Any ideas?
Thanks!

---


---
title: "Qemu/KVM  Windows 10 and 11 booting to black screen"
date: 2024-04-01
forum: Virtualisation
---

### Post by jack frost on 2024-04-01
Thank you in advance.

I have used win10 VM for years with no issues but just a few days ago it stated booting into a black screen after login.

This is also happening to a windows 11 vm. This is using virt manager for both VM's.  

The win10 I have had a very long time with no issues until just a few days ago it boots to login screen, then after login the screen turns black.

The win11 vm was created about a month ago. It was also fine until a few days ago. I am on ubuntu 22.04.4 LTS.

---

### Post by maximge on 2024-05-21
1. Update graphics drivers and Virtio drivers.
2. Check hardware allocation and BIOS settings.
3. Ensure QEMU/KVM and virt-manager are up to date.
4. Experiment with graphics configurations.
5. Review logs for error messages.
6. Recreate VMs if necessary.

---


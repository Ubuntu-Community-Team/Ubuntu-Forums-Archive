---
title: "VMs on Spare SSD"
date: 2019-08-07
forum: Virtualisation
---

### Post by merlot160 on 2019-08-07
I am looking to set up 2 VMs on a spare SSD drive. Do I need the Ubuntu ISO on the same drive or can I just leave in my download folder on my C:\Drive

---

### Post by QIII on 2019-08-07
Hello!

The .iso does not need to be on the target device.

If you are running virtualization software in Windows (or any other host OS), then the .iso can be wherever you want, on any device/partition/directory to which host OS has access.  So you can leave it on your Windows partition in whatever directory you choose.  Virtualization software will generally simply ask you for the location of the installation .iso when you are creating the VM.

(And now for news from the "It really doesn't matter, but FYI department" ...  "C:\" is not technically a "drive".  It is a partition on a physical storage device.  Generally, both "C\:" and "D:\" inhabit the same physical device or "drive" as separate partitions.  We often refer to "C:\" as the "Windows partition".  In Linux parlance, a "folder" is a "directory".  :) )

---

### Post by Dennis N on 2019-08-07
With respect to QEMU/KVM and Virt Manager, there is a default location, but you can choose another location for the virtual machine disks. It's a good idea to do so, because the default location is in /var and the disks will use up your space. The default VM disk is 20 GB. The ISO can be discarded after VM creation.

---

### Post by merlot160 on 2019-08-07
Many thanks for the replies.

---


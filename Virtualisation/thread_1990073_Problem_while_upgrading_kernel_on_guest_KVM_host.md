---
title: "Problem while upgrading kernel on guest KVM host"
date: 2012-05-29
forum: Virtualisation
---

### Post by byo.spoon on 2012-05-29
Hi everyone,

I've got one machine that's a container for small virtualized ubuntu-server instances, everything works on KVM. I'm fighting with one particular issue while upgrading virtual machines and was wondering whether someone have simillar issues :)

The problem  happens everytime the kernel on virtual machine is upgraded. I'm doing the upgrade through ssh, everything goes smooth until I fire the sudo reboot command. When the virtual machine reboots and enters grub, the default kernel option is ignored and the VM ends up in the grub menu eating 100% of the cpu assigned. There's no timeout although it's specified properly in /etc/default/grub. I'm using virt-manager then to connect to the VM and simply press enter which "fixes" the issue.

The problem is even worse when I have virt-manager open while performing the reboot. Virt-manager basically hangs and I have to kill the rebooted virtual machine manually to make virt-manager working again.

The funny thing is that I can issue the reboot without any problem but after the VM boots successfully for the first time after kernel upgrade.

The VM host is running 11.04, kernel version: 2.6.38-13-server
VM guests run ubuntu server 11.04, 11.10 or 12.04, the issue is the same no matter what guest version is used.

Regards
Bartek

---


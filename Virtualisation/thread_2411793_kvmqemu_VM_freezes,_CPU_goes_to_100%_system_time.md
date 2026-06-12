---
title: "kvm/qemu VM freezes, CPU goes to 100% system time"
date: 2019-02-04
forum: Virtualisation
---

### Post by bautsche on 2019-02-04
Hi.

I've got a number of kvm virtual machines running on 18.04. Very regularly (every couple of minutes), the VMs freeze (e.g. they don't respond any more on the network) and the qemu process goes to use 100% of sys time on the CPU it's running on.

The closest I seem to have found to my issue is this:
[https://bugs.launchpad.net/qemu/+bug/1775555](https://bugs.launchpad.net/qemu/+bug/1775555)

However, that suggests that the issue only occurs with migrated VMs, so I tried to install a new VM and got the same issue.

I can unfreeze the VM by opening up its console in virt-manager and hitting return a few times but clearly this isn't a workaround.
Also: the longer the VM was left frozen the longer it takes after the hitting return bit in the console to unfreeze it.

I have a number of VMs running and this doesn't seem to happen to my (only) Windows VM, but to my Solaris VMs only.

This issue only seems to occur since I updated yesterday, but this may be a complete red-herring. Here's what /var/log/apt/history.log has to say:
```
Start-Date: 2019-02-03  16:01:57
Commandline: apt upgrade
Install: libwayland-egl1:amd64 (1.16.0-1ubuntu1.1~18.04.1, automatic), libllvm7:amd64 (1:7-3~ubuntu0.18.04.1, automatic), linux-headers-4.15.0-45:amd64 (4.15.0-45.48, automatic), linux-modules-extra-4.15.0-45-generic:amd64 (4.15.0-45.48, automatic), linux-modules-4.15.0-45-generic:amd64 (4.15.0-45.48, automatic), linux-headers-4.15.0-45-generic:amd64 (4.15.0-45.48, automatic), linux-image-4.15.0-45-generic:amd64 (4.15.0-45.48, automatic)
Upgrade: poppler-utils:amd64 (0.62.0-2ubuntu2.5, 0.62.0-2ubuntu2.6), irqbalance:amd64 (1.3.0-0.1, 1.3.0-0.1ubuntu0.18.04.1), update-manager-core:amd64 (1:18.04.11.8, 1:18.04.11.9), linux-headers-generic:amd64 (4.15.0.43.45, 4.15.0.45.47), libdrm-nouveau2:amd64 (2.4.91-2, 2.4.95-1~18.04.1), linux-libc-dev:amd64 (4.15.0-43.46, 4.15.0-45.48), libapt-inst2.0:amd64 (1.6.6, 1.6.8), libegl-mesa0:amd64 (18.0.5-0ubuntu0~18.04.1, 18.2.2-0ubuntu1~18.04.1), libcairo-gobject2:amd64 (1.15.10-2, 1.15.10-2ubuntu0.1), update-notifier-common:amd64 (3.192.1.4, 3.192.1.5), grub-common:amd64 (2.02-2ubuntu8.9, 2.02-2ubuntu8.10), linux-image-generic:amd64 (4.15.0.43.45, 4.15.0.45.47), apt:amd64 (1.6.6, 1.6.8), libavahi-glib1:amd64 (0.7-3.1ubuntu1.1, 0.7-3.1ubuntu1.2), libgs9:amd64 (9.26~dfsg+0-0ubuntu0.18.04.3, 9.26~dfsg+0-0ubuntu0.18.04.4), libkmod2:amd64 (24-1ubuntu3.1, 24-1ubuntu3.2), libglapi-mesa:amd64 (18.0.5-0ubuntu0~18.04.1, 18.2.2-0ubuntu1~18.04.1), libasound2-data:amd64 (1.1.3-5ubuntu0.1, 1.1.3-5ubuntu0.2), libavahi-common-data:amd64 (0.7-3.1ubuntu1.1, 0.7-3.1ubuntu1.2), libavahi-common3:amd64 (0.7-3.1ubuntu1.1, 0.7-3.1ubuntu1.2), grub2-common:amd64 (2.02-2ubuntu8.9, 2.02-2ubuntu8.10), libspice-server1:amd64 (0.14.0-1ubuntu2.2, 0.14.0-1ubuntu2.4), libapt-pkg5.0:amd64 (1.6.6, 1.6.8), grub-pc:amd64 (2.02-2ubuntu8.9, 2.02-2ubuntu8.10), kmod:amd64 (24-1ubuntu3.1, 24-1ubuntu3.2), libgbm1:amd64 (18.0.5-0ubuntu0~18.04.1, 18.2.2-0ubuntu1~18.04.1), libwayland-client0:amd64 (1.14.0-2, 1.16.0-1ubuntu1.1~18.04.1), grub-pc-bin:amd64 (2.02-2ubuntu8.9, 2.02-2ubuntu8.10), libdrm-amdgpu1:amd64 (2.4.91-2, 2.4.95-1~18.04.1), libtiff5:amd64 (4.0.9-5, 4.0.9-5ubuntu0.1), python3-distupgrade:amd64 (1:18.04.29, 1:18.04.30), python3-update-manager:amd64 (1:18.04.11.8, 1:18.04.11.9), ubuntu-release-upgrader-core:amd64 (1:18.04.29, 1:18.04.30), avahi-daemon:amd64 (0.7-3.1ubuntu1.1, 0.7-3.1ubuntu1.2), tar:amd64 (1.29b-2, 1.29b-2ubuntu0.1), libavahi-core7:amd64 (0.7-3.1ubuntu1.1, 0.7-3.1ubuntu1.2), libwayland-egl1-mesa:amd64 (18.0.5-0ubuntu0~18.04.1, 18.2.2-0ubuntu1~18.04.1), libdrm2:amd64 (2.4.91-2, 2.4.95-1~18.04.1), ghostscript:amd64 (9.26~dfsg+0-0ubuntu0.18.04.3, 9.26~dfsg+0-0ubuntu0.18.04.4), apt-utils:amd64 (1.6.6, 1.6.8), libgl1-mesa-dri:amd64 (18.0.5-0ubuntu0~18.04.1, 18.2.2-0ubuntu1~18.04.1), libmysqlclient20:amd64 (5.7.24-0ubuntu0.18.04.1, 5.7.25-0ubuntu0.18.04.2), libgs9-common:amd64 (9.26~dfsg+0-0ubuntu0.18.04.3, 9.26~dfsg+0-0ubuntu0.18.04.4), libasound2:amd64 (1.1.3-5ubuntu0.1, 1.1.3-5ubuntu0.2), libgl1-mesa-glx:amd64 (18.0.5-0ubuntu0~18.04.1, 18.2.2-0ubuntu1~18.04.1), libdrm-intel1:amd64 (2.4.91-2, 2.4.95-1~18.04.1), firefox:amd64 (64.0+build3-0ubuntu0.18.04.1, 65.0+build2-0ubuntu0.18.04.1), apt-transport-https:amd64 (1.6.6, 1.6.8), libdrm-radeon1:amd64 (2.4.91-2, 2.4.95-1~18.04.1), mesa-vdpau-drivers:amd64 (18.0.5-0ubuntu0~18.04.1, 18.2.2-0ubuntu1~18.04.1), libcairo2:amd64 (1.15.10-2, 1.15.10-2ubuntu0.1), libpoppler73:amd64 (0.62.0-2ubuntu2.5, 0.62.0-2ubuntu2.6), libavahi-client3:amd64 (0.7-3.1ubuntu1.1, 0.7-3.1ubuntu1.2), linux-generic:amd64 (4.15.0.43.45, 4.15.0.45.47), libwayland-server0:amd64 (1.14.0-2, 1.16.0-1ubuntu1.1~18.04.1), mesa-va-drivers:amd64 (18.0.5-0ubuntu0~18.04.1, 18.2.2-0ubuntu1~18.04.1), libglx-mesa0:amd64 (18.0.5-0ubuntu0~18.04.1, 18.2.2-0ubuntu1~18.04.1), libdrm-common:amd64 (2.4.91-2, 2.4.95-1~18.04.1), libwayland-cursor0:amd64 (1.14.0-2, 1.16.0-1ubuntu1.1~18.04.1)
End-Date: 2019-02-03  16:03:35

Start-Date: 2019-02-03  16:03:56
Commandline: apt autoremove
Remove: linux-headers-4.15.0-42:amd64 (4.15.0-42.45), linux-modules-extra-4.15.0-42-generic:amd64 (4.15.0-42.45), libllvm6.0:amd64 (1:6.0-1ubuntu2), linux-modules-4.15.0-42-generic:amd64 (4.15.0-42.45), linux-headers-4.15.0-42-generic:amd64 (4.15.0-42.45), linux-image-4.15.0-42-generic:amd64 (4.15.0-42.45)
End-Date: 2019-02-03  16:04:11
```


Any pointers would be greatly appreciated. As is, this isn't usable.

Thanks.
Eric

---

### Post by maxnasonov on 2019-11-01
Hello Eric. Have you been able to resolve it? We have the issue looking exactly the same.

---

### Post by wildmanne39 on 2019-11-01
Hello and welcome to the forum  maxnasonov, please start your own thread to get the help you need instead of posting in someone else's thread.

Thanks!

Old thread back to sleep, rest in peace.

---


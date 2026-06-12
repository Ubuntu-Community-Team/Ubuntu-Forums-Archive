---
title: "Windows 10 won't boot after Grub update"
date: 2017-10-12
forum: Windows
---

### Post by will76 on 2017-10-12
I've not been able to boot to Windows 10 after an Ubuntu Update that appeared to upgrade Grub. In the past when I had this problem I booted to the Ubuntu live CD and ran boot-repair and this fixed the Windows boot entry in Grub. Now however I've tried boot-repair a number of times trying different options. I have a /boot/EFI partition. In UEFI I disabled CSM and secure boot. I have Refind installed although I can't remember installing it. I think Ubuntu and Windows 10 were installed in UEFI mode. When I select the Windows option in Grub I just goes back to the Grub menu. Ubuntu boots ok. If I select the Windows fall back option in Grub it takes me to the Refind boot loader where there is no option to boot to windows.

Ubuntu and Windows are installed on the same NVME drive on separate partitions. The EFI partition is there also. Here the the result of the last boot-repair.

[https://paste.ubuntu.com/25729033/](https://paste.ubuntu.com/25729033/)

Windows is installed on /dev/nvme0n1p4 and the Ubuntu root partition is on /dev/nvme0n1p5.

Can anyone help with this?

Thanks,

---


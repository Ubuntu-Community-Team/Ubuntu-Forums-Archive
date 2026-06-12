---
title: "Grub menu booting"
date: 2016-06-28
forum: Ubuntu/Debian BASED
---

### Post by carson6 on 2016-06-28
So I dual booted Linux and Windows 10 and then I decided I wanted fedora instead... I deleted the partitions and forgot to change the boot order now when I reboot it brings me to the grub menu and I have no idea how to get back. Ive tried many different videos and none have worked so far, can anyone help me?

---

### Post by oldfred on 2016-06-29
UEFI or BIOS?

If BIOS you can try Boot-Repair, but if you left Windows fast startup on, you probably can only repair with Windows repair flash drive you made before installing any Linux.

If UEFI you should just be able to go into UEFI boot menu and choose Windows. But if you left UEFI fast boot on, you may have to cold boot or do other fixes to get into UEFI or UEFI boot menu.

---


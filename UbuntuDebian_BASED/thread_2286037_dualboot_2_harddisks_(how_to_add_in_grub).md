---
title: "dualboot 2 harddisks (how to add in grub)"
date: 2015-07-09
forum: Ubuntu/Debian BASED
---

### Post by washichi on 2015-07-09
sda: windows (allocated partition, and data partition)
sdb: ElementaryOS (/efi, ext4 / , swap, data)

I have now 2 harddrives in my laptop, So I've formatted them both,
installed win8.1 on sda, and after that installed Elementary OS on sdb.

to install Elementary OS I created 3 partitions:
- /efi (300mb)
- ext4/ (15gb)
- swap (10gb)
- data (441gb)
ElementaryOS is installed on ext4

I can select in my bios which HDD to boot, and if I select SDA windows8.1 will boot, and if I select SDB ElementaryOS will boot.
so far no problem,

[B]How can I add windows in grub? (so I dont have to edit my boot priority in the bios)?

[/B]- Windows diskmanagament: [http://prntscr.com/7qp4ds](http://prntscr.com/7qp4ds)
- boot-repair log: [http://paste2.org/08vfyUBY](http://paste2.org/08vfyUBY)

---

### Post by oldfred on 2015-07-09
Moved to Other OS since not Ubuntu.

You are only showing two Windows partitions. That is then a BIOS install with MBR partitions.
If Elementary is UEFI, you cannot boot Windows from grub, only from UEFI boot menu or one time boot key, often f10 or f12.

UEFI & BIOS are not really compatible. Once you start booting in one mode you cannot change to the other mode. The two systems write data to drive differently for operating system to use. So once system starts in one mode and you have grub menu you cannot switch.

You can reinstall Windows or just use UEFI to boot.

---

### Post by washichi on 2015-07-09
mhh okay, very clear thanks!

by "use UEFI to boot" you mean going in my bios and change boot HDD right?

---

### Post by oldfred on 2015-07-09
Yes.
But you should be able to use one time boot key, often f10 or f12 to choose boot. Quicker than going into UEFI and changing boot order.

How you boot install media for both Windows & Ubuntu is then how it installs. 
 Windows 8 install to blank drive
[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)

---


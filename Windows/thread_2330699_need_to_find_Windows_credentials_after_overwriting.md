---
title: "need to find Windows credentials after overwriting Win 8"
date: 2016-07-13
forum: Windows
---

### Post by Odyssey1942 on 2016-07-13
I am unsure how to proceed. About 3 years ago, I bought a HP Pavilion (AMD Quad-core) desktop from Woot for my wife. She hated Win 8, so we put Ubuntu 12.04 (with Gnome flash-back [fall-back?]) on it and she was/is a happy camper.

It is time to upgrade to 16.04 and I hope I can get that done without posting here, but before that, there is an "opportunity" which expires in a few days (July 31) and that is to upgrade the Win 8 to Win 10 (which I am OK with, but not in preference to Ubuntu). I would like to upgrade her computer to 10 just to have it if needed, but there is no current copy of Win 8 on the machine. I do not see a Win sticker on it either. Have no idea where the documentation (if there was any) is that might have come with the box.

Any ideas on how to credential the computer for the upgrade? Thanks.

---

### Post by yancek on 2016-07-13
You can't upgrade to windows 10 unless you have something to upgrade from. Did you purchase the windows 8 installation DVD with the computer? Do you have a recovery partition for windows 8 and a recovery CD? If not, I doubt there is any way to do it. You might try a windows forum or the microsoft site but if you don't have the sticker on the computer or any documentation, I doubt there is much hope.[SIZE=4][/SIZE]

---

### Post by Bucky Ball on 2016-07-14
And thread moved to **Windows** forum ...

Not related to Ubuntu support.

---

### Post by ubfan1 on 2016-07-14
Actually, the UEFI machines with Windows 8 preinstalled did not have an MS sticker with a product key on the bottom.  The key may be embedded in firmware(?), and also certainly in the registry (usless unless you dumped it before deleting Windows).  Anyway, you can freely download the W10 ISO from Microsoft without a key.  See links like  [http://www.redmondpie.com/download-windows-10-pro-iso-file-without-product-key-from-microsoft/](http://www.redmondpie.com/download-windows-10-pro-iso-file-without-product-key-from-microsoft/)  for instructions.  You can try the straight install to a fresh disk and see if it activates automatically.   Note, even  OEM key numbers work for activation, even ones which were rejected for an earlier Windows ISO download (from another URL, obviously, not the one mentioned above).

From Ubuntu, you may try to find the key with a dump:  od -Ax -tx1z /sys/firmware/acpi/tables/MSDM
Not sure that's the right key, but maybe worth a try.

---

### Post by oldfred on 2016-07-14
Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[URL="http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c"]http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c

      [/URL]
 Repair/backup/restore
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)
Windows 10 ISO
[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO)
Windows 10 repair disk
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 
    

Is Ubuntu installed in UEFI boot mode on gpt partitioned drive. The UEFI product key only works for UEFI install and Windows must have a gpt partitioned drive.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by buzzingrobot on 2016-07-15
I believe it's 8.1 that's upgrade eligible.  If you have 8.0, upgrade to 8.1 first, then to 10.

---


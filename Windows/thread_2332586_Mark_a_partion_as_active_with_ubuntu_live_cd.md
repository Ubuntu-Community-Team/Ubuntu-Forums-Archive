---
title: "Mark a partion as active with ubuntu live cd"
date: 2016-08-01
forum: Windows
---

### Post by blackpower on 2016-08-01
Hi

I had a problem with my Lenovo laptop
It started with a BSOD with error on an intel driver, i then tried to rescure my data with an ubuntu live USB. Since that windows wont even boot into the error message, it just stands on the Lenovo logo without comming further. 
I had checked the drives with the ubuntu usb and can see theres no star with the drive windows should boot from, how can i mark the drive as active so windows will boot from it and what drive should i mark and how do i do it?

Here is a screenshot of the drives
[http://i64.tinypic.com/29kqtlv.jpg](http://i64.tinypic.com/29kqtlv.jpg)

---

### Post by oldfred on 2016-08-01
With UEFI systems the only partition that uses boot flag(active partition in Windows) is the ESP or efi system partition. Your sda2 shows as efi partition so it must be correctly marked.

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Is this a Windows only system?
Often better to use Windows tools and use the Windows repair flash drive you should have made to make repairs to Windows.

       
 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

---

### Post by blackpower on 2016-08-02
It is a windows based system only, the reason why i use ubuntu is i cant get it to boot from a repair disk

Here is the bootinfo
[https://paste2.org/f5Ubyn4Z](https://paste2.org/f5Ubyn4Z)

---

### Post by oldfred on 2016-08-02
Your screen shot from first post showed normal partitions.
Now Boot-Repair is not showing any partitions at all, like you erased drive?

Because your screen shot shows the exact sectors start & end, it may be possible to rebuild partition table. But UEFI with gpt normally has a backup gpt partition table.

Post this:
       sudo gdisk -l /dev/sda

If Windows often better to use Windows tools.
If partitions are missing, testdisk or parted rescue are Linux tools to repair/restore missing partitions.

---

### Post by blackpower on 2016-08-02
I have not erased the drive

Here is sudo gdisk -l /dev/sda
[http://i65.tinypic.com/2j3kwnd.jpg](http://i65.tinypic.com/2j3kwnd.jpg)

---

### Post by oldfred on 2016-08-02
The gdisk output is also normal, and not showing issue that commands run by Boot-Repair to generate report showed.

> Invalid MBR Signature found.

I might just rewrite partition table with gdisk.

       sudo gdisk /dev/sda
Command (? for help):  

 Use gdisk and verify partitions are correct with p, and use w to write the partition table. The v command can give more details on issues if necessary.  If not correct just use q to quit. The w -write should update primary, backup & protective MBR.

---

### Post by blackpower on 2016-08-02
Okay now theres progress, now if i let it stand for about 10 min, it says "Preparing automatic repair" and i get this screen
[URL="http://i67.tinypic.com/2ev41gn.jpg"]http://i67.tinypic.com/2ev41gn.jpg
[/URL]

---

### Post by blackpower on 2016-08-02
If i press F8 i got a screen with the option to boot in safe mode with commandpromt, when i select this it gives me a screen with error on this file windows/system32/drivers/iaStorAV.sys

---

### Post by oldfred on 2016-08-02
Moved to Windows sub-forum.

---


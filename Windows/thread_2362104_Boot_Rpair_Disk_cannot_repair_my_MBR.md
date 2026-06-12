---
title: "Boot Rpair Disk cannot repair my MBR"
date: 2017-05-24
forum: Windows
---

### Post by linuxedwindow on 2017-05-24
Hi

I had a windows 7 ultimate and fedora 21  dual boot. Because of some unknown reasons I was not able to login to  Windows and it showed some LogonUI.exe file error. Till then fedora was  working fine. Then iI used ESET Live rescue disk for full system scan.  It might have deleted or altered some files. After this noting would  start. "Operating system missing" , this is the error being shown.

So i tried boot repair to repair MBR, but it is showing an error. ([http://paste.ubuntu.com/24643100/](http://paste.ubuntu.com/24643100/))

How can this issue be resolved.


Thanks & regards

---

### Post by howefield on 2017-05-24
Thread moved to the "*Windows*" forum.

---

### Post by oldfred on 2017-05-24
It looks like you have new UEFI hardware, but installed in the 35 year old BIOS/MBR configuration.
You must always then boot in BIOS mode and make sure UEFI Secure Boot is off, as then BIOS will not work at all.

You also have EasyBCD, all the /grldr files shown. That uses the very old grub4dos and an edit to BCD to chain to grub4dos which chains to grub2 installed in a partition boot sector (PBR) to boot.
That somewhat worked with grub legacy, but grub2 is a lot larger as it supports all the newer hardware & features.
Grub2 does not want to be installed into a PBR as then it has to convert to block lists which are not reliable.

Grub only boots working Windows, so if now Windows is not working that would be a Windows issues.

I would first go thru all the normal Windows fixes, and often you have to run chkdsk multiple times or until no errors.

       How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/) 
   Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---


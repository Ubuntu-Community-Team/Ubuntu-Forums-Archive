---
title: "Windows 10 Pro 1709 x64 broke boot file"
date: 2017-11-12
forum: Windows
---

### Post by RocknRollTim on 2017-11-12
[LEFT]Hi all,

I was wondering whether you could help. This may or may not be a coincidence but after I upgraded from Windows 10 Pro 1703 to 1709 and powered the PC off and back on, the PC's BIOS says it can't find the disk and instructs you to either press F1 to skip or F2 to enter the PC's BIOS setup, I kept on pressing F1 and kept getting stuck in a continuous loop after the BIOS's splash screen. The PC's disk setup is 4TB Hybrid Hard Disk which is formatted as GPT and is split into 6 partitions, 5 that are bootable and 1 as a storage area. The 5 bootable partitions are 120GB each containing Windows 7 Ultimate SP1 x64, Windows 7 Professional SP1 x64, Windows 8 Pro x64, Windows 8.1 Pro x64 and Windows 10 1709 x64 and all in logical boot order whereas the storage area is using the remaining 3496GB and is non bootable. The BIOS boots the drive using UEFI without secure boot and CSM but in the current situation I am using the drive that came with the PC with making this the master drive and the hybrid drive as the Slave drive. The configuration for this drive is a 250GB MBR with Windows 10 1709 x64 and the PC is currently booting in legacy. I can access the contents of the hybrid drive via the 250GB drive which is an ordinary SATA drive using Windows Explorer. I have performed numerous checks using Seagate Tools for Windows and Check Disk and none of them have picked up any faults? The PC is a Vostro 470. Your help would be very gratefully appreciated.

Regards,

RocknRollTim

P.S. Do think Ubuntu will be able to fix this problem?[/LEFT]

---

### Post by yancek on 2017-11-12
If I understand your post, you have windows on a GPT drive and as far as I know, any windows using GPT must also use UEFI, by design of microsoft.  I'm not sure why that is the case.

I'm not that familiar with UEFI but I would suggest that while you are waiting for a response here, you check with some windows forums or the support.microsoft site as your systems involve only microsoft windows.  I doubt that Ubuntu or any Linux will be able to resolve the problem, I certainly wouldn't expect that.  Boot repair sometimes can repair very simple boot problems with a windows system but with a complex setup such as yours I doubt it would help.

---

### Post by RocknRollTim on 2017-11-12
Hi yancek,

Thank you for responding to my forum thread, I thought I would ask the question just in case someone had a solution to my problem using Ubuntu but if you feel its best for me to continue looking through Microsoft resources, I will continue doing that.

Regards,

RocknRollTim

---

### Post by oldfred on 2017-11-12
I have to agree with yancek that the Windows forums would be best.

But you have an unusual configuration.
A 4TB drive has to be gpt partitioned as MBR(msdos) has a max of 2TiB.
       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

Windows only boots with BIOS using MBR and only with UEFI using gpt.
Some with older Mac and older Windows did use a hybrid MBR/gpt configuration, but that is not now recommended. They also have to be kept in sync.

 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html) 

Even Windows 7 can be installed in UEFI boot mode, but DVD default installer is BIOS only. It has to be copied to a flash drive and some files renamed/moved.
  How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html) 


If you have enabled CSM/Legacy you are booting in BIOS mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

 [http://www.tenforums.com/](http://www.tenforums.com/)
[http://www.eightforums.com/](http://www.eightforums.com/)
[http://superuser.com/](http://superuser.com/)

---

### Post by RocknRollTim on 2017-11-13
Hi oldfred,

Thank you for also responding to my forum thread. I am in the process of obtaining solutions on Microsoft Community as well as other Windows forums. One user from the Microsoft Community forum suggested that I convert the 250GB MBR drive to GPT? I presume this is in order for me to access the 4TB GPT drive and to do some boot edit changes but I do agree with what you are saying with regards to MBR and GPT and will give the instructions ago with regards to creating a bootable Windows UEFI USB stick and to give that route a whirl.

Regards,

RocknRollTim

---

### Post by oldfred on 2017-11-13
I have seen instructions on converting Windows to gpt & UEFI, they were not particularly straightforward. Easier to just reinstall if you have good back ups of your data (which you should have anyway). Windows default installs have a totally different set of partitions.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions) 

 You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)
Convert Windows from BIOS/MBR to UEFI/gpt.
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729](http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx) 


You can use Linux tools to convert from MBR to gpt.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr) 
   Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

---

### Post by RocknRollTim on 2017-11-13
Sounds like a reinstall is a plausible solution oldfred and thank you very much for the information again, it has really helped me to understand the issue in detail.

Regards,

RocknRollTim

P.S. How do PCs which support both BIOS and UEFI function with volumes that are formatted as MBR and GPT?

---

### Post by oldfred on 2017-11-13
PC normally works with MBR, gpt or others like RAID & LVM which may be inside a gpt partition.
Some older systems and many external cases did not work with either gpt or drives over 2TiB and needed updates or replacement.
And some early large drives used some proprietary MBR configuration to allow older Windows to use drives over 2TiB.

It is Windows that only boots with BIOS from MBR and UEFI from gpt.
Ubuntu can boot from gpt with either UEFI or BIOS. I started converting to gpt for my then BIOS only desktop system in 2010. Had one MBR drive for Windows XP, long gone now, and several gpt drives. None of my drives were the new very large drives.

---


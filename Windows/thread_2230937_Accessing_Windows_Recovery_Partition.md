---
title: "Accessing Windows Recovery Partition"
date: 2014-06-22
forum: Windows
---

### Post by kevlimzm on 2014-06-22
Hello! 

I have been trying to get into my windows 7 recovery partition. So far I have tried using a windows installation disk, but for some reason it keeps telling me I'm using the wrong version, eventhough I have tried the 32-bit and 64-bit disk version of win7 home premium as stated as the os on my laptop.

When starting my laptop there is an option called Windows Recovery Enviroment, but by picking it cause it to say: "Uknown command drivemap invalid EFI Filepath". I tried to use the method stated here [http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530), but I' am still unable to access the recovery partition!

I hope someone is able to help me, thank you! :)

This is what I got from Boot-Repair: [http://paste.ubuntu.com/7684742/](http://paste.ubuntu.com/7684742/)

---

### Post by Mark Phelps on 2014-06-22
You don't mention if this is a dual-boot machine in which you have installed a Linux distro, thereby having modified the original partition setup.  IF that is the case, it's likely the Recovery process is NOT going to work because that expects to still have the original partition layout intact.

If this is a Windows-only PC, you might have better luck taking your Windows 7 problem to a Windows 7 forum -- recommend sevenforums.com for one.

---

### Post by kevlimzm on 2014-06-22
Ah I have installed Ubuntu 12.04 on the system, but i have left the recovery partition untouched, while hoping to be able to use Ubuntu to restore Windows 7.

---

### Post by oldfred on 2014-06-22
Recovery partition does not look untouched. It shows mount errors which often can be corrected with chkdsk from your Windows repairCD or flash drive. That cannot be fixed from Linux.
Some third party Windows tools may include a better chkdsk function.
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)
       Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)

    
And as Mark Phelps posts, you probably need to have the original Windows partition structure and maybe even the same partition sizes. The recovery is a image that it restores to the expected partitions.

Typical Windows partitions, but every vendor varies. Best if you know exact structure you had.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by Bucky Ball on 2014-06-22
*Thread moved to **Other OS/Distro Support**.*

---

### Post by kevlimzm on 2014-06-22
oh I see... Then I'll have to try figure it out! Thank you for clearing that up!

---


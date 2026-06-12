---
title: "Installed Zorin OS (based off Ubuntu 14.04) and accidently removed Windows"
date: 2016-08-10
forum: Ubuntu/Debian BASED
---

### Post by chicagotrain on 2016-08-10
I tried to install Zorin OS using a USB Drive, since it didn't detect my operating system considering my Windows 10 system is on UFEI Mode and Zorin is on CSM, I thought it would install alongside, but instead it deleted all the Windows partitions and replaced it with the Zorin/Ubuntu system. I think I got the key from "sudo cat /sys/firmware/acpi/tables/MSDM" but it's a Windows 8 one and I got Windows 10 while the free upgrade so I don't know if it would work. My laptop is a Toshiba Satelite C855D and again, orginially came with Windows 8. I don't think I would be able to recover the data from my former Windows OS so is it possible just to get Windows 10 at least? Like I said I have a key code from the terminal. I don't have a recovery disk but I have a USB flash drive where I installed Zorin. Is it possible to get Windows 10 back?

---

### Post by deadflowr on 2016-08-10
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by kurt18947 on 2016-08-11
You should be able to reinstall Windows 10, I'd think. Once it's been installed on a machine and activated, Microsoft 'remembers' the machine and will reactivate. I think installing one OS in UEFI mode and another in CSM mode is a no-no and possibly why Windows 10 went away. I'm no expert on it though, I have all pre-UEFI machines for a reason ;).

---

### Post by chicagotrain on 2016-08-11
I have been able to install one OS in UEFI and another in CSM in the past sucessfully. I got a Windows 10 .iso converted to a flash drive, if I boot from flash drive on UFEI mode, will it work? The Zorin installation changed the file system of the hard drive to ext4 so will the installation revert it back to NTFS?

---

### Post by kurt18947 on 2016-08-12
> **chicagotrain said:**
> I have been able to install one OS in UEFI and another in CSM in the past sucessfully. I got a Windows 10 .iso converted to a flash drive, if I boot from flash drive on UFEI mode, will it work? The Zorin installation changed the file system of the hard drive to ext4 so will the installation revert it back to NTFS?

This would be a question for Old Fred or someone versed in file systems, boot managers UEFI and related topics, I am not. I am however quite certain that Windows will not install on an EXT4 formatted partition and Zorin will not install on an NTFS formatted partition. I think you can have both but you need to create several partitions first. I have no knowledge beyond what I've read here and elsewhere.

Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I did discover one 'gotcha' though. I had Windows 7 installed as the first partition with an *buntu install immediately after it. I upgraded the Win7 install to Windows 10. The install seems function BUT it created another blank 500 MB. Windows formatted partition right after the existing Windows partition - right over top of the *buntu partition. Gee, thanks Microsoft. How thoughtful of you :frown:. Fortunately there was nothing of consequence in the overwritten partition.

---

### Post by oldfred on 2016-08-12
The most common reason the installer does not see Windows 8 or 10 is the fast start up which is just hibernation.  You must turn off fast start in Windows.

        Product key now in UEFI/BIOS , but do not know if reinstall of upgrade would now be free or not.
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c) 

Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html

      [/URL] How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    [URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]
[/URL]

---


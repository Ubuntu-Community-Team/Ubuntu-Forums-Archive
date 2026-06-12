---
title: "Problem installing Win7"
date: 2014-06-01
forum: Windows
---

### Post by yur2 on 2014-06-01
Hello.

First sorry for my bad english and sorry if this question is missposted.

My computer/HDD (got 1 HDD) have a complete install of Ubuntu 12.10, i mean that everything of Windows was wiped.
Now, because some workproblems, i want to go back fully to Windows 7, and maybe...... an dualboot with Ubuntu (after!).
Thus, first only a complete install of Windows 7.

My DVD drive is broken so i use a 32GB USB stick.
The stick with Windows 7 on it is healthy and has no problems.

So, in the BIOS i set the USB first boot thing. then exit en start up the installation (i was hoping).
But hell no, i get an error. The well known 0xc000000e error.

I have searched for days for an answer but i didn't fine one.
Every discussion on the some same thing is going on the dual-boot, that thing i don't have at the moment and don't want yet!

So, we can help me out???
i want a clean install of Windows7 using USB from a fully installed Ubuntu OS. And the error come up every time.
I think it has to do with the bootloader? But which one? must that for the internal HDD? or for the USB stick?

Who can explain it to me?
Thank you for any help.........

Greets Jeroen J. from Schinnen, the Netherlands.

---

### Post by oldfred on 2014-06-01
Moved to OtherOS.

If a full Windows installer it should boot. But I do see a lot of threads on issues with getting a correct installer with Linux tools. Do not know Windows errors. Last install was Windows XP in 2006. :) And that is not now running.
I was only able to create a Windows 7 repair flash drive by creating the DVD and using its own Windows tools to create the flash drive and copy itself to flash drive.

But Windows has to see unallocated space with available primary partitions or have a NTFS formatted primary partition with the boot flag to install into. It does not see Linux partitions and does not just overwrite them.

And if drive happens to be gpt partitioned Windows will only install in UEFI mode which your hardware may not even support or Windows directly boot into UEFI mode.

---

### Post by yur2 on 2014-06-01
"But Windows has to see unallocated space with available primary  partitions or have a NTFS formatted primary partition with the boot flag  to install into. It does not see Linux partitions and does not just  overwrite them."

Oke, i have this set up right now. 15GB primary ntfs with the bootflag and 5GB unallocated.
With no luck. After boot i get the same error again.
Is there not a possibility to install windows while running Ubuntu?

For some things to understand. I have 1 HDD in the computer and i got 1 usb stick of 32GB.
i got about 8GB of files that must be kept. I want put that on the stick with windows 7 on it too.
But, first i must know that my Windows 7 stick really works before i can delete the GPT partition on the disk.
When deleted i got nothing only the Windows 7 install. When the install not work or i get the same error again (before win7 installation) then i loose my data that must kept. This makes it all harder.

I need to check the win7 installation first (at least only a few steps of the installation).

Help!!!!!!! (lol)

---

### Post by oldfred on 2014-06-01
You do need to be sure something boots before erasing drive. 
And there is no way I know of, to install a full system from another. There is virtual box? Do not know much about it but many suggest it for Windows if not used for gaming and hardware is reasonable new.

But I have multiple flash drives with various Linux installers, or repair ISOs, so I have many ways to boot.

If a Windows 7 installer what tool did you use to create it?
Are you sure it is a full installer and not just a repair or update ISO?

But I think this is only from Windows.
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)

This worked with unetbootin, but I think it does not work now?
 Use unetbootin to copy windows iso to partition and install:
[http://ubuntuforums.org/showthread.php?t=1480974](http://ubuntuforums.org/showthread.php?t=1480974)

Never used this:
[http://www.rmprepusb.com/](http://www.rmprepusb.com/)

---


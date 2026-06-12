---
title: "Installing Windows 7, how do I do it?"
date: 2014-01-16
forum: Windows
---

### Post by thedoctor2016 on 2014-01-16
I have a Windows 7 disc I'm installing and apparently I need to install a pre-installation kit. I read somewhere that I need to format my hard drive since I only have Ubuntu installed and it messes things up. If that's true, can I back up my Ubuntu OS so I don't lose all the data I have? If not, do I need to install the pre-installation kit by CD and then the Windows 7 Service Pack 1 disc? Also if you have any other ideas I would appreciate them.

---

### Post by oldfred on 2014-01-16
Assuming system is older BIOS based with MBR(msdos) partitioning, not new UEFI.
Windows has to boot from a primary (sda1 thru sda4) NTFS formatted partition with the boot flag.
Default installs of Windows use two partitions, a 100MB boot partition and the main install. But it can be installed to one partition. Main reason for separate boot partition was so main partition could be encrypted. Another was so you may be able to run repairs from boot partition on main install. But if you have separate repairCD or flash drive, you can just install to one NTFS partition. 
Some have to use Windows installer to reformat NTFS partition and make active (bot) command as it does not always see NTFS correctly when created from gparted or other Linux tools.

Best not to make Windows primary partition after extended partition on drive. Windows does not correctly see Linux partitions and may rewrite partition table and will install its boot loader to MBR, so you have to plan on reinstalling grub to MBR.

Be sure to have good backups. And document or backup partition table to make it easy to restore if Windows mucks it up like it is prone to do.
       Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---


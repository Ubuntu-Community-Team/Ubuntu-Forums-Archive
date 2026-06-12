---
title: "OS-Uninstaller Broke Grub"
date: 2017-01-16
forum: The Cafe
---

### Post by vdicarlo on 2017-01-16
I see that many people have successfully used OS-Uninstaller, but I was not so lucky. 

I had installed Ubuntu on a an old refurbished Optiplex 960 SFF that I had upgraded to run Windows 10.  The computer uses a bios instead of UEFI, and Grub worked correctly to boot me into either Ubuntu or Windows.  I had a mysterious recurrent problem with my computer freezing up when running Ubuntu, but not Windows, so I used OS-installer to uninstall Ubuntu. Unfortunatetly, after doing so I got an error message from Grub and was unable to boot into Windows, which I then reinstalled using the whole disk.  Didn't lose much data or figure out what went wrong.  

The moral of the story?  Any time you install or uninstall an operating system, realize that you might lose everything on the disk and have to start over from bare metal, unless you are prepared for what may be a long and painful journey through disk backups, and the details of Grub and partitions.

---

### Post by oldfred on 2017-01-16
If you left Windows fast start up or always on hibernation on, then Linux tools do not see Windows NTFS partition.

I would then expect that OS-Uninstaller would not see Windows to let you install a Windows BIOS boot loader.

       Boot live cd/DVD -  knoppix,  Ubuntu or many repair live Linux systems, many have it already installed
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda 

Or use lilo
      
 Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).
[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on/422023#422023](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on/422023#422023)

---


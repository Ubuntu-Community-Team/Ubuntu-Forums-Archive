---
title: "Installing Win 7 inUEFI mode"
date: 2017-08-24
forum: Windows
---

### Post by linuxyogi on 2017-08-24
Hi,

Soon I will be assembling a PC for a friend. The configuration will core i3 with a suppported motherboard (not yet decided). Since all new motherboards come with UEFI I want to know what special steps should I take to install Win 7 on the motherboard.

I have never used a UEFI system. Will it be simple like old system where you press del key on boot and select first boot device and continue with the installation ?

---

### Post by oldfred on 2017-08-24
If you have Windows DVD it is BIOS only install. It will not boot in UEFI mode.
But you can copy DVD to flash drive and move/rename several files to make it UEFI bootable.
UEFI only boots USB flash drives from /EFI/Boot/bootx64.efi. That file name is used by both Windows & Ubuntu, but obviously different files.

        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)
Convert Windows from BIOS/MBR to UEFI/gpt.
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729](http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[https://blogs.technet.microsoft.com/askcore/2011/05/31/installing-windows-7-on-uefi-based-computer/](https://blogs.technet.microsoft.com/askcore/2011/05/31/installing-windows-7-on-uefi-based-computer/)
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition](http://superuser.com/questions/676249/clean-install-of-windows-7-pro-64-bit-on-a-uefi-laptop-with-gpt-partition)

---

### Post by linuxyogi on 2017-08-24
Its too complicated. I will ask him to buy somethng with WIN 10 preloaded. He needs to tun some TAX softwares so Windows is a must.
Thanks for your reply.

---


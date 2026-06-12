---
title: "After attempting to install Debian-based linux, Windows doesn't appear in Grub"
date: 2014-09-13
forum: Ubuntu/Debian BASED
---

### Post by darhinester on 2014-09-13
Pastebin after running boot-repair  --------------- [http://paste.ubuntu.com/8336403/](http://paste.ubuntu.com/8336403/)

After attempting to go to the boot menu, there are still just linux options available.
Please advise on next steps or any further information you may require.

---

### Post by oldfred on 2014-09-13
Moved to other OS.

You deleted the Windows boot partition. 
Windows 7 and later have a separate hidden in Windows 100MB boot partition that has these two files. You now do not show them in your main install, so must have had the separate Boot.

       Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

You cannot fix from any Linux. If you have a Windows repairCD or flash drive it is easy to fix, but you must move boot flag back to your NTFS partition sda3 first. Grub does not use boot flag, Windows has to have boot flag on partition with boot files, normally the 100MB one, but you can boot directly from main install if it has boot files.

If you have a copy of bootmgr copy that into sda3. You may need your Windows repairCD or flash drive or other third party tools to recreate BCD.
      
 Repair BCD
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

      We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $20 or $40  for the download. So make one yourself before you have to pay to get one.
[http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/](http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/)
Make your own Windows recoveryCD/repair: (free)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

     Win7 forum
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---


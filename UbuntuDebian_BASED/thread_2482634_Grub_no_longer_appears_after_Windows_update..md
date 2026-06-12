---
title: "Grub no longer appears after Windows update."
date: 2023-01-06
forum: Ubuntu/Debian BASED
---

### Post by jj.wauters on 2023-01-06
At this moment I can only start Ubuntu by clicking Esc, selecting Ubuntu from Windows Boot Manager and then selecting Ubuntu from his menu. 

HP Envy laptop with Windows10 and Ubuntu 18.04

Bios permits only rank next UEFI boot order: (does not show or permits adding Grub/Ubuntu)
```
USB Diskette on a Key/USB Hard Disk
OS Boot Manager
Internal CD/DVD Rom Drive
USB CD/DVD ROM Drive
! Network Adapte
```r 

While efibootmgr shows:
```
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0002,3002,0000,2001,2002,2003
Boot0000* ubuntu
Boot0002* Windows Boot Manager
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
```
When I change the bootorder to 0000,0002,3002,2001,2002,2003 and reboot the PC it comes back with the previous order (0002,3002,0000,2001,2002,2003)
What I find strange in my opinion is:
- 2003 mentioned in bootorder but not in the detail list
- Boot3000, Boot3001 and Boot3002 while there is only one HD present.

Any help is welcome to get Grub coming up as OS loader.

---

### Post by yancek on 2023-01-06
When you are in the BIOS, do you see a black triangle to the left of OS Boot Manager?  If so, that means multiple entries where you can make a selection.
How did you try to change the order?  Did you use efibootmgr?  I've been using HP with UEFI for several years and have had no luck with efibootmgr.  Try making the change in the BIOS with the F10 option to access BIOS and highlight the Ubuntu entry and use the F6 key to move it up.

I don't think the windows bootloader will boot a Linux system UEFI so you are probably in the BIOS.
Also, support for 18.04 will end in April so you might look at updating to a newer version soon.

---

### Post by jj.wauters on 2023-01-06
There is no black triangle in BIOS. I changed the UEFI order in BIOS with the F keys in order to have a live USB on top. As there is no Ubuntu entry visible in BIOS I cannot move it.
I used efibootmgr -O with the known result.

---

### Post by yancek on 2023-01-07
It seems odd that efibootmgr shows an ubuntu entry but you do not see it in the BIOS.  If you use the down arrow to scroll down to OS Boot Manager then hit the entry key, do you not see an option for ubuntu?  As I indicated previously, I have never had any success trying to make changes with efibootmgr on an HP but can do so in the BIOS.  If you don't see an ubuntu option in the BIOS, I'm not sure what you could do.

---

### Post by jj.wauters on 2023-01-10
Screenshot BIOS: here I can only arrange the order of the available items. 
[IMG][[IMG]https://i.postimg.cc/v4WvZSC0/HP-BIOS.jpg[/IMG]]("https://postimg.cc/v4WvZSC0")[/IMG]
Screenshot BOOT MANAGER: When I press Esc fast enough at PC startup, I can avoid Windows booting and then choose between OS Boot Manager(=Windows), Ubuntu and Boot from efi file(=gives error message). I can't change anything in this screen, only select.
[IMG][[IMG]https://i.postimg.cc/hXFrgqZJ/BOOT-MANAGER.jpg[/IMG]]("https://postimg.cc/hXFrgqZJ")[/IMG]
In fact, I can live with the situation as it is now. I'm just sorry that Grub does no more work.

FYI: content /boot directory
/boot$ ls -d */
efi/  grub/  grub.bak/

/boot/efi$ ls -d */
boot/   EFI/  'System Volume Information/'   Temp/

/boot/efi/EFI$ ls -d */
Boot/  HP/  Microsoft/  ubuntu/

---


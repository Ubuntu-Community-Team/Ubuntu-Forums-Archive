---
title: "Windows 8 UEFI boot broken, not fixed by boot-repair"
date: 2013-10-27
forum: Windows
---

### Post by ihavebeencalled on 2013-10-27
[LIST]
[*]I installed Ubuntu in dual-boot on my Windows 8 laptop. Everything worked fine.
[*]A few days ago I updated to Windows 8.1. Ubuntu stopped booting.
[*]No problem, I ran a live USB version of Ubuntu and ran boot-repair (taking into account that I was using UEFI). Linux booted correctly, but Windows boot got weird.
[LIST]
[*]If I selected Windows Boot Manager at startup, the screen went black then jumped into GRUB. If I selected Windows Boot UEFI loader, I got the GRUB rescue screen.
[*]If I selected Windows UEFI bootmgfw.efi (created by boot-repair, I believe), Windows booted normally.
[/LIST]

[*]This was annoying, so I ran boot-repair a few more times (why I didn't think to save the boot-info, I don't know), now Windows won't boot at all.
[*]Now if I select the previously working option in grub, I get a long and unintelligible error message which I'll share below.
[/LIST]
[INDENT=2]
/EndEntire

file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,c8800,96000,ec9d3a6356fca941,9d,10)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error: premature end of file (hd0,gpt2)/EFI/Microsoft/Boot/bootmgfw.efi

Press any key to continue...
[/INDENT]

[LIST]
[*]Pressing any key returns me to grub
[*]I have no Windows 8 recovery USB (stupid, I know)
[*]A non-Ubuntu recovery live USB disk supposed to fix Windows boot problems didn't notice the disk at all running fdisk -l said "disk doesnt contain a valid partition table"
[*]Did I break it for good?
[*]I'm downloading a free trial of Windows 8 so I can try to run fixboot etc. but I'm a bit worried.
[*]LINUX STILL WORKS! YAY!
[/LIST]

---

### Post by neu5eeCh on 2013-10-29
There seem to have been all kinds of problems updating Windows 8 in a dual boot environment. Here's some advice [I found here]("http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/491339-booting-broken-after-updating-windows-8-1-a.html"):

"As for updating from Windows 8.0 to 8.1, you need to put Windows back in  as the default boot from your PC setup.  Select its uefi partition as  default boot for instance or, if installed on a separate hard disk, make  it the default boot disk in PC setup.  If sharing the same MBR boot  disk, make sure the MBR is generic boot code and use GPARTED to set the  Windows partition as the active booting partition.  Make sure you  created a LiveDVD or thumb drive in order to use GPARTED to put the  openSUSE root partition back as the default boot for that hard disk.

In general do not install Grub into the MBR else Windows 8.1 will not  install or it will remove grub for you, thus making sure you must  reinstall Grub.  You must be online to the internet and logged into  Windows 8.0 with a Microsoft Account.  A local account will not provide  the update option.  You will find the 8.1 option, if all is right, in  the store as the first option you can select."

---

### Post by oldfred on 2013-10-29
Some computers only boot the Windows efi file. Boot-Repair then renames grub2's shim to be the Windows file to get grub to boot. I am sure that confuses Windows on updates and may make the fix a bit more difficult from Boot-Repair as renamed files probably were replaced with new versions and then the backup that Boot-Repair created may be the wrong version. Best to undo any changes Boot-Repair does before upgrading Windows.
But  the real issue is vendors who modify UEFI to only boot Windows.

If you can boot live installer or Ubuntu as installed rerun the Boot-Info report and post link to report.

---


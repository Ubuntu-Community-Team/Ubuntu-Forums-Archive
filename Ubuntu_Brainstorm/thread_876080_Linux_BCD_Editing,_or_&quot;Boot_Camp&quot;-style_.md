---
title: "Linux BCD Editing, or &quot;Boot Camp&quot;-style Rebooting"
date: 2008-07-31
forum: Ubuntu Brainstorm
---

### Post by DizzyTech on 2008-07-31
Dual boot users of Windows Vista will be familiar with NeoSmart Technologies' [EasyBCD]("http://neosmart.net/dl.php?id=1") and [iReboot]("http://neosmart.net/dl.php?id=11").

For the uninitiated, EasyBCD is a tool that allows a user to edit and modify Windows Vista's boot loader.  It features a very wide set of tools and allows for very easy chainloading to GRUB, LILO, NTLDR, OS X's EFI, and a couple of others.  iReboot is a minimalist tray icon that loads a users' list of operating systems from the BCD store and allows a user to set one as the default OS for the next boot, entirely forgetting the selection menu and allowing the selected operating system to start instantly.

The problem is that there is no similar feature for Linux users.  In other words, one can easily boot into Ubuntu from Vista, but Ubuntu will always reboot back into Vista (or vice versa, depending on which you like to be default).

So, I had an idea.  Why not create an OS selection process similar to that of Apple's Boot Camp?  One OS is permanently the default for boot, always.  However, one can select the default OS using a userspace utility.  For OS X users, you'll know this to be the "Startup Disk" utility.  I see no major reason this can't be done for a Windows/Ubuntu setup.


From a more technical aspect, the setup could be done either using Vista's BCD or Linux's GRUB.  A similar utility (and a tutorial) has been made using the command-line tool grub-set-default.  I think the biggest issue for using GRUB, though, would be mounting Ubuntu's filesystem for editing the menu.lst.

That leaves the booting to Vista's BCD.  The major roadblock for this would be editing the BCD to set the default OS and the menu timeout to 0, all from Ubuntu.  Granted, this would be a lot easier because we have write access to the NTFS volume.

The utilities to entirely fulfill this idea would be both a frontend for Windows (resembling NeoSmart's iReboot tray icon and Boot Camp's Startup Disk control panel applet) and a frontend for Ubuntu.

EDIT:  If there is no way to develop a native BCD-editing tool for Linux, Wine could be used to run the bcdedit.exe utility with command switches - but this would require manual configuration to tell the utility which GUID entry is Vista and which is Ubuntu.

Any ideas?

---


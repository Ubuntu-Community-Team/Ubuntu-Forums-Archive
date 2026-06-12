---
title: "Windows 10 User Profile cannot be loaded"
date: 2023-04-06
forum: Windows
---

### Post by tmdntn on 2023-04-06
Windows 10 and Bohdi Ubuntu on IBM ThinkCentre A-52
Dual boot was good for a couple months, now getting error when trying to boot Windows.
[SIZE=3][B]The User Profile Service service failed the sign-in. User Profile cannot be loaded
[/B][/SIZE]Ran boot-repair, report is here:  [https://paste.ubuntu.com/p/fw4ZrYmxHF/](https://paste.ubuntu.com/p/fw4ZrYmxHF/)
Help will be appreciated. Thanks!
tmdntn

---

### Post by coffeecat on 2023-04-06
*Thread moved to **Windows** sub-forum.*

---

### Post by tmdntn on 2023-04-06
As recommended in the above report, I ran boot-repair. Should I next run "[COLOR=#222222][FONT=monospace]unhide-bootmenu-10s win-legacy-basic-fix", as recommended?[/FONT][/COLOR]

---

### Post by oldfred on 2023-04-06
Grub only boots working Windows.
That means it cannot need chkdsk, nor with Windows 8 or later have fast startup/hibernation on. And if UEFI Secure Boot has to be off.
You may need to do Windows repairs using your Windows repair/recovery flash drive.
With UEFI you can boot either install directly from UEFI boot menu.
But with BIOS you only have one MBR, so only one boot loader.
Install Windows BIOS boot loader to MBR, boot & repair Windows & use Boot-Repair or manually reinstall BIOS version of grub to MBR.

---

### Post by coffeecat on 2023-04-07
@tmdntn

Disclaimer - I have little recent experience with Windows, however...

The fact that you are getting a "failed sign in" message, suggests that the boot process is just fine, and that the problem is at the sign in stage. Do you see the Windows sign in page? If so, I would think that trying to fix a probably non-existent boot problem with boot repair is not only unnecessary, but might itself cause further problems. I googled the "The User Profile Service service failed the sign-in. User Profile cannot be loaded" message. (Did you?) There were several seemingly useful hits, including:

[https://4sysops.com/archives/how-to-fix-the-user-profile-service-service-failed-the-sign-in-user-profile-cannot-be-loaded/](https://4sysops.com/archives/how-to-fix-the-user-profile-service-service-failed-the-sign-in-user-profile-cannot-be-loaded/)
[https://theitbros.com/user-profile-service-failed-the-sign-in/](https://theitbros.com/user-profile-service-failed-the-sign-in/)

They both suggest registry problems or filesystem errors as likely causes, not boot process problems. Perhaps those two links, or others you might find in a web search, will give you useful leads. 

Last thought: when I moved your thread from one of the Official Ubuntu Flavours sub-forums yesterday, I thought it odd that someone running a dual-boot of a distro that is not Ubuntu with Windows should seek help with a Windows problem on Ubuntu forums. You are very welcome here for Ubuntu problems, but you might find it more productive to seek help for this particular Windows problem on a Windows forum. Many, perhaps most, members here, like me, have little familiarity with Windows.

---

### Post by yancek on 2023-04-07
At what point do you get this error message?  Is it after you select windows from the Grub boot menu?  Are you booting with Grub?  Does Bodhi still boot?  Do you actually have 2 install of windows 10?

It appears that you tried more than one install as your report shows Grub installed code to the MBR which would not be done with a GPT/UEFI install.  Line 99 of boot repair shows your fstab file has a good EFI and starting at Line 44, it shows a vfat partition which is likely meant to be an EFI partition but contains nothing.  Line 173 shows a good /boot/efi in fstab but again, shows no EFI files.  You can do an EFI install of Ubuntu on an msdos drive but it isn't standard or recommended and if you do, you will not be able to boot windows from Grub if it is a Legacy install (which it is).

Line 87 of boot repair shows the drive is NOT GPT so windows cannot be installed in EFI mode.

The error you report seems to be more of a user log in problem and I doubt that it is a problem with Grub and suggest posting the error message at a windows forum or doing an online search with that exact error message.  Doing that gave a number of links including one to the microsoft site.  Be sure to check back here as it may be possible a member has some knowledge of the problem.

[https://theitbros.com/user-profile-service-failed-the-sign-in/](https://theitbros.com/user-profile-service-failed-the-sign-in/)
[https://answers.microsoft.com/en-us/windows/forum/all/the-user-profile-service-failed-the-sign-in-and/f8c96883-05fb-4094-9dc6-4169d1063ace](https://answers.microsoft.com/en-us/windows/forum/all/the-user-profile-service-failed-the-sign-in-and/f8c96883-05fb-4094-9dc6-4169d1063ace)

---


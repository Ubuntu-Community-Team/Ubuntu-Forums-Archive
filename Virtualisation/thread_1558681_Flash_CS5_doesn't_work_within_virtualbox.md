---
title: "Flash CS5 doesn't work within virtualbox"
date: 2010-08-22
forum: Virtualisation
---

### Post by FattyOwl on 2010-08-22
I'm trying to install Flash CS5 on my Windows 7 64-bit virtual machine. The installation goes trough completely; but at the end I receive an error. The error basically says that my operating system doesn't meet all the requirements.

These are the requirements:
Intel® Pentium® 4 or AMD Athlon® 64 processor
Microsoft® Windows® XP with Service Pack 2 (Service Pack 3 recommended); Windows Vista® Home Premium, Business, Ultimate, or Enterprise with Service Pack 1; or Windows 7
1GB of RAM
3.5GB of available hard-disk space for installation; additional free space required during installation (cannot install on removable flash-based storage devices)
1024x768 display (1280x800 recommended) with 16-bit video card
DVD-ROM drive
QuickTime 7.6.2 software required for multimedia features
Broadband Internet connection required for online services*

I meet all these requirements except for the resolution. The resolution is set to 1360x648. How should I solve this problem?

---

### Post by FattyOwl on 2010-08-22
I tried installing full screen (which met the resolution requirements. I got the same error message:

Exit Code: 7


-------------------------------------- Summary --------------------------------------


 - 0 fatal error(s), 9 error(s), 3 warning(s)


WARNING: OS requirements not met for {694213D7-1E0E-4C8F-B822-E2E3680C0FCE}


WARNING: OS requirements not met for {CFC9F871-7C40-40B6-BE4A-B98A5B309716}


WARNING: CreateAlias:Icon file does not exist at C:\Program Files (x86)\Adobe\Adobe Utilities - CS5\Pixel Bender Toolkit 2\windows\pb_app.icofile:\\\C:\PIXELB~1\source\winwood\Staging    0X1.FEA209P-1022rea\windows\pb_app.ico42178f80493091e8e552c84a2897e9da68fce32_32_f80493091e8e552c84a2897e9da68fce for icon C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Adobe Pixel Bender Toolkit 2.lnk with target C:\Program Files (x86)\Adobe\Adobe Utilities - CS5\Pixel Bender Toolkit 2\Pixel Bender Toolkit.exe


ERROR: 135 Unable to move file at "C:\Program Files (x86)\Common Files\Adobe\Installers\adobeTemp\{14A2CC02-4638-405D-8190-ECD7BFD32D6E}\_128_02f2e862cc942fa3f337fbfbf3734051" to "C:\Program Files (x86)\Adobe\Adobe Flash CS5\en_US\Configuration\Libraries\Sounds.fla" Error 32 The process cannot access the file because it is being used by another process.


ERROR: 135 Command ARKMoveFileCommand failed.


ERROR: 135 Unable to delete file copy at "C:\Program Files (x86)\Adobe\Adobe Flash CS5\en_US\Configuration\Libraries\Sounds.fla" Error 2 The system cannot find the file specified.


ERROR: 135 Error rolling back command ARKMoveFileCommand


ERROR: The following payload errors were found during install:


ERROR:  - Adobe Flash CS5_AdobeFlash11-en_USLanguagePack: Install failed


ERROR:  - Adobe Flash CS5_AdobeMobileExtension_Flash11-en_US: Install failed


ERROR:  - Adobe Flash CS5_AdobeMobileExtension_Flash11-mul: Install failed


ERROR:  - Adobe Flash CS5: Failed due to Language Pack installation failure


-------------------------------------------------------------------------------------

---


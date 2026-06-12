---
title: "Cant Install Remote Desktop Client v6.1"
date: 2010-05-11
forum: Wine
---

### Post by kecher on 2010-05-11
Hey all,

I have been trying to install Remote Desktop Client version 6.1 (and 6.0) in wine but I get an error "path not found" every time and the installation fails. This version of RDP is for winXP x86 which is the OS that I have set in Wine. The version of Wine I have is 1.1.42 and all the other settings are just the default (this is a fresh install from about an hour ago). Here is the terminal output that I get when I try installing...

[HTML]
fixme:clusapi:GetNodeClusterState ((null),0x32ec3c) stub!
fixme:advapi:DecryptFileA "c:\\8996b13ec994154fd644\\" 00000000
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:advapi:RegisterEventSourceA ((null),""): stub
fixme:advapi:RegisterEventSourceW (L"",L""): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0xc00e1115,(nil),0x0003,0x00000000,0x33f360,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0xc00e1115,(nil),0x0003,0x00000000,0x131ec8,(nil)): stub
err:eventlog:ReportEventW L"Windows"
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L"Path not found\r\n"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
[/HTML]Any help or suggestions would be appreciated.

P.S. I have been using Terminal Server Client previously but my boss upgraded the server to only accept connections from computers using RDP 6.0 or above and Terminal Server Client doesn't support that protocol yet. If anyone knows of a linux compatible Terminal Server Client that supports RDP 6.0 I would love to hear about it.

---

### Post by cogadh on 2010-05-12
RDP doesn't really work in WIne:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3108](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3108)

I'm not poositive about this, but I thought rdesktop was already 100% compatible with MS's protocols.

---

### Post by kecher on 2010-05-13
I had checked the wine appdb and saw the one positive report but I didn't read the report. The way they had gotten it to "work" for the one positive report was they installed it in windows and copied all the files over. They didn't actually install it with the installer. I guess my options are to do that (install in Windows and copy the files over), dual boot or install windows on a virtual machine. 

In regards to rdesktop's compatibility with RDP it supports v5 but not v6. As i have been searching I have found this post, [http://www.linuxquestions.org/questions/linux-general-1/remote-desktop-version-6-for-linux-microsoft-rdp-v6-747651/](http://www.linuxquestions.org/questions/linux-general-1/remote-desktop-version-6-for-linux-microsoft-rdp-v6-747651/) apparently I'm not the only person plagued with this problem.

---

### Post by cogadh on 2010-05-13
A Bronze rating on AppDB is not a positive report, its only slightly less "garbagey" than Garbage. Silver is barely a positive report while Gold and Platinum are really the only positive ratings for apps on Wine.

---


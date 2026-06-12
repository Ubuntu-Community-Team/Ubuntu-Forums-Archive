---
title: "DDOnline still won't let me log in"
date: 2010-11-24
forum: Wine
---

### Post by Eldorian on 2010-11-24
Hi all. I still cannot log into DDOnline. I hope someone can help. My system is:

Intel Dual-Core E5300
2GB RAM
700 GB SATA HD
Nvidia GeForce 9500 GT w/ 1GB RAM using driver version 195.36.24
Ubuntu 10.04
Wine 1.3.6

These are the steps I followed to install everything fresh in a new .wine bottle which worked very well until trying to log in:

Download DDO Mod 8 - full version.
Install Wine and Set to Windows 2000.
Create Direct3D.reg on desktop and copy this into it and save it:
____________________________________________________________________________
REGEDIT4 

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="OpenGL"
"Multisampling"="disabled"
"OffscreenRenderingMode"="fbo"
"RenderTargetLockMode"="readdraw"
"UseGLSL"="disabled"
"VideoMemorySize"="1024"
----------------------------------------------------------------------------
Open a terminal and type: regedit /home/user/Desktop/Direct3D.reg then close regedit.
Type: sudo apt-get install cabextract....and let it install then close the terminal.
Install Winetricks.

Create Fake.net11.reg on desktop and copy this into it and save it:
____________________________________________________________________________
REGEDIT4

[HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP\v1.1.4322]
"Install"=dword:00000001
"SP"=dword:00000001

[HKEY_LOCAL_MACHINE\Software\Microsoft\.NETFramework\policy\v1.1]
"4322"="3706-4322"
----------------------------------------------------------------------------
Open a terminal and type: regedit /home/user/Desktop/Fake.net11.reg then close regedit.
Type winetricks and install the following, one at a time from the list:
d3dx9
vcrun2005
vcrun2008

Run the DDO setup.exe using wine and let it install.
If there are .net framework 2.0 errors then install it from winetricks as well then retry DDO install.
Install the following from the repository:
Python
4Suite
pyqt4
pylotro

Download the patchclient.dll file and rename it as lotropatcher.dll and copy it to the DDO folder.

Start pylotro then click Tools, Settings Wizard. Choose wine under application then choose DDOnline under game and click find games. Select the game folder then click apply.
Click Tools then Switch Game and choose DDOnline then OK.
Click Tools, Options and enable Advanced Options and change the patchclient.dll file name to lotropatcher.dll then click Save. Next run Tools, Patch and let the game fully update.

DDO should run now.

Errors and fixes:

*error: bt audio service open connect() failed: Connection refused (111)

*fix: sudo apt-get purge bluez-alsa

*error: DDO tries to start when logging in but stops with ***Finished*** screen

*fix: None yet

---

### Post by Eldorian on 2010-11-25
I am trying everything I can think of while combing through google like a madman and still no joy with pylotro, wine and ddonline. Someone please give me some ideas before I end up breaking wine again. Is there a way to run wine or pylotro through the terminal so I can see if any error shows up? Or maybe some debug program that can trace what is happening behind the scenes when the launcher or ddo crashes? I recently threw out windows and am all in for Linux now but am still a newbie so I'm not sure where to go except here for answers and there is NO WAY I am going back to microsoft. Thanks.

Eldorian

---

### Post by Eldorian on 2010-11-25
After searching more on google I decided to install the winetricks options for d3dx9, vcrun2005 and vcrun2008 again. d3dx9 installed fine but when I tried to install vcrun2005 I got the following:

john@john-desktop:~$ winetricks
Using native,builtin override for following DLLs: msvcr80
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*msvcr80"="native,builtin"
Executing wine vcredist_x86.exe
fixme:advapi:DecryptFileA "C:\\users\\john\\Temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\users\\john\\Temp\\IXP001.TMP\\" 00000000
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:advapi:LookupAccountNameW (null) L"john" (nil) 0x33f150 (nil) 0x33f154 0x33f148 - stub
fixme:advapi:LookupAccountNameW (null) L"john" 0x148b90 0x33f150 0x185d30 0x33f154 0x33f148 - stub
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
err:msi:ITERATE_Actions Execution halted, action L"MsiPublishAssemblies" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627

Any ideas?

---

### Post by Eldorian on 2010-11-25
Update: I got past the login issue by removing the check mark from the Alsa audio driver set in winecfg. Dont ask me why that was stopping it cuz I have no idea, but...I made it to to the character select screen then clicked enter world which took me to the welcome to eberron scree and then it froze with the bar at the bottom saying loading -- please wait never showing any color in the bar. I alt-tabbed to the desktop and found the following error in the wine output screen:

p, li { white-space: pre-wrap; } err:ntdll:RtlpWaitForCriticalSection section 0x68d12c60 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 001f, blocked by 0009, retrying (60 sec)


If anyone has seen this before of has an idea what might cause it please let me know. Thanks :)


Eldorian

---

### Post by Eldorian on 2010-11-25
Well it finally worked. Might have been faster if someone could have responded. I just got lucky removing the Alsa option from wine. Logged in and everything is fine including sound.

---


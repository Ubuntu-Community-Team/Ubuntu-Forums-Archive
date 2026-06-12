---
title: "MS Office 2003 - Wine 1.1.15 - Ubuntu 8.10 can't get it to work"
date: 2009-02-25
forum: Wine
---

### Post by Kiotie on 2009-02-25
I'm trying to get MS office 2003 installed using wine but have yet to find a walk-thru or tutorial that works. So I thought I would post to see if anyone can diagnose the issue to get me over the hump.

I'm close, it brings up the install windows and I enter the key and choose my install options but a second after I click install it crashes with a setup error.  Here is my info:

--------------------

#Wine Version: 1.1.15

#Terminal Output:
user@ubuntu:~$ wine /media/cdrom0/setupstd.exe
fixme:advapi:CheckTokenMembership ((nil) 0x12d790 0x32eaac) stub!
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:LookupAccountNameW (null) L"user" (nil) 0xXXXXX (nil) 0xXXXXX 0xXXXXX - stub
fixme:advapi:LookupAccountNameW (null) L"user" 0xXXXXX 0xXXXXX 0xXXXXX 0xXXXXX 0xXXXXX - stub
fixme:shell:DllCanUnloadNow stub
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:advapi:CheckTokenMembership ((nil) 0xba4d88 0x7dd3f174) stub!
fixme:shell:DllCanUnloadNow stub
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 41 ignored L"Upgrade" table values
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 41 ignored L"Upgrade" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
err:msi:ITERATE_Actions Execution halted, action L"CADpc" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
user@ubuntu:~$ fixme:imm:ImmDisableIME (-1): stub

#Wine configuration:
-OS version - Windows XP
-Library overrides - msxml3 (native), riched20 (native), riched32 (native)
-Sound settings, all options - 
Driver Selection - no Drivers checked
Hardware Acceleration - Basic
Default Sample Rate: 44100
Default Bits Per Sample - 16
Driver Emulation - unchecked
-Graphics settings, all options
Window settings
Allow DirectX apps... - unchecked
Allow the window manager to decorate... - checked
Allow the window manager to control... - checked
Emulate a virtual desktop - unchecked
Direct 3d
Vertex Shader Support - None
Allow Pixel Shader - unchecked
Screen Resolution - 96 dpi
-Registry edits - none

#Hardware Specs/Drivers
Dell XPS M1710 labtop
Intel Core2Duo T7400
GeforceGo 7900GTX 512Mb - Nvidia driver v177
2 Gb Ram
100Gb HD

#Other Wine apps: None

#Error code from MS Office Setup
ProdCode : {90120409-6000-11D3-8CFE-0050048383C9}     
ProdVer : 10.0.2627.01
Action : x     ErrNum : 0     Err0 : x     Err1 : x     Err2 : x

---

### Post by Kiotie on 2009-02-26
bump

---

### Post by NightMKoder on 2009-02-26
From Wine's AppDB: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214)

> 
Current versions of Wine (1.0 and later) do not require any overrides to install Office 2003 Pro.  Install as you would in Windows: insert the cd and run setup.exe. 

Do not report bugs for the installer if you have used any overrides.


Since you have overrides, noone can tell you what's wrong. Furthermore, it seems like you used winetricks which makes it even harder to debug.

Start with a fresh wine install (ie delete/move .wine), and then we may be able to help you. Although it seems like you shouldn't have any problems.

---

### Post by Kiotie on 2009-02-26
Thank you for the input to get me going.  

I removed wine using the Add/Remove tool under applications then deleted the .wine file.  I reinstalled w/o any mods other than configuring drives, folders and audio.

It looks like the same error again.

----------------------

#Wine Version: 1.1.15

#Terminal Output:
user@ubuntu:~$ wine /media/cdrom0/setupstd.exe
fixme:advapi:CheckTokenMembership ((nil) 0x12d790 0x32eaac) stub!
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:LookupAccountNameW (null) L"user" (nil) 0x33f80c (nil) 0x33f810 0x33f804 - stub
fixme:advapi:LookupAccountNameW (null) L"user" 0xXXXXXX 0xXXXXXX 0xXXXXXX 0xXXXXXX 0xXXXXXX - stub
fixme:shell:DllCanUnloadNow stub
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:advapi:CheckTokenMembership ((nil) 0xba4d60 0x7dd3a174) stub!
fixme:shell:DllCanUnloadNow stub
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 41 ignored L"Upgrade" table values
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 41 ignored L"Upgrade" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
err:msi:ITERATE_Actions Execution halted, action L"CADpc" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
user@ubuntu:~$ fixme:imm:ImmDisableIME (-1): stub


#Wine configuration:
-OS version - Windows XP
-Library overrides - none
-Sound settings, all options -
Driver Selection - no Drivers checked
Hardware Acceleration - Basic
Default Sample Rate - 44100
Default Bits Per Sample - 16
Driver Emulation - unchecked
-Graphics settings, all options
Window settings
Allow DirectX apps... - unchecked
Allow the window manager to decorate... - checked
Allow the window manager to control... - checked
Emulate a virtual desktop - unchecked
Direct 3d
Vertex Shader Support - Hardware
Allow Pixel Shader - checked
Screen Resolution - 96 dpi

-Registry edits - none

#Hardware Specs/Drivers
Dell XPS M1710 labtop
Intel Core2Duo T7400
GeforceGo 7900GTX 512Mb - Nvidia driver v177
2 Gb Ram
100Gb HD

#Other Wine apps: None

#Error code from MS Office Setup
ProdCode : {90120409-6000-11D3-8CFE-0050048383C9}     ProdVer : 10.0.2627.01
Action : x     ErrNum : 0     Err0 : x     Err1 : x     Err2 : x

---

### Post by Kiotie on 2009-02-28
.

---

### Post by Kiotie on 2009-03-01
I was able to borrow a copy of Office 2007 from a co-worker for the weekend.  That seems to install using the same configuration as above.  Only Word and Excel actually launch and are usable but it's much further than Office 2003 is getting.

Unfortunately I can't use his copy and I don't want to buy 2007 since 2003 is what we are using at my office.  So I'm still hacking on 2003 without any luck.

---

### Post by Torkiliuz on 2009-03-03
It's "Drive configuration", not "Driver configuration", go to the tab that says "Drive Configuration" in wineconfig, and select "Auto-detect".:)
Now try to insert the install disc, and see what happens.
PS: You can run the setup from the disc, by browsing into it, right-click it and select "open with 'wine'", in case you didn't already know:P.

---

### Post by augoldfinger on 2009-04-01
I have had this issue since Ubuntu 7.1

I have never gotten Office 003 to fully work. I did get everything but Outlook, Word, & Access, but I mainly use Outlook & Word. 

I did successfully install 007, but it was a trail version & like you I did not want to purchase it at the time.

This has been the main issue for me keeping a Windows box. I am not willing to switch my email data base.

I used a program called Crossover in Daper & it worked great for Office 003, but has not worked at all in these newer versions of Ubuntu:(

---

### Post by 24*7 on 2009-04-01
I think that
**if u install wine **
and then 
double-click on **PRO11.MSI** in MS Office 2003 directory, 

ur problem will be resolved.

I'm using MS Office 2003 under Wine in Ubuntu 8.10 and it works perfectly.

**_TIP:_** In case u want Arial/Comic Sans fonts in MS Office 2003 under Wine in Ubuntu 8.10, u need to install msttcorefonts using 
```
$sudo apt-get install msttcorefonts
```

---

### Post by studavis on 2009-04-02
Thanks for the tip, I had 2003 working very well in 8.10 but then had to re-install with 8.04 - long story... I have clean install of Wine 1.1.18 and Office 2003 on my hard drive (dual boot so I keep it on C:). I open PRO11N.MSI (must be different version to yours), the installation screen appears, I can enter serial number and choose the configuration, then it appears to start but the dialog box then disappears.  Any suggestions? I did not run Winetricks or change any libraries. 

thanks

edit:
I've changed to 9.04, fresh Wine 1.0.1 install, I can install 2003 (XL, Word, PP) without problem. No dll changes. When I tried to import my settings file (OPS) XL froze and I could not uninstall. Had to remove Wine and start all over. Lesson: don't import your MS Office settings. Just need to get VBA support running now.

---

### Post by augoldfinger on 2009-04-02
I don't have 8.1 anymore either. I went back the  8.04 as well, but I will try this out on a machine I have. Perhaps later today...I think I used the setup.exe when I installed it the last time.

I'll see if mine has the PRO11.MSI

Thanks

---

### Post by studavis on 2009-04-06
Many thanks Brother, appreciate any help.

---


---
title: "rosetta stone on wine 1.3 and Ubuntu 10.4"
date: 2010-08-21
forum: Wine
---

### Post by zambezi on 2010-08-21
Hi 

I am trying to get Rosetta Stone to run on wine and have tried most things.  Have tried wine 1.0, 1.1, 1,2 & !,3 and have got furtherst with 1.3.  I have managed to install the program and get it to run by removing pulseaudio as suggested but now it crashes at the microphone setup.  Here is the log (if I can paste it without getting smilies all over the place)

fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1066
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1066
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1066
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1066
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1066
fixme:win:EnumDisplayDevicesW ((null),0,0x32f588,0x00000000), stub!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Macrovision Shared\\FLEXnet Publisher\\\\fnp_registrations.xml" 1 4 (nil) (nil) 0x33583f0 (nil)
fixme:psapi:EnumDeviceDrivers ((nil), 0, 0x32c474): stub
fixme:psapi:EnumDeviceDrivers (0x393da68, 0, 0x32c474): stub
fixme:psapi:EnumDeviceDrivers ((nil), 0, 0x32c218): stub
fixme:psapi:EnumDeviceDrivers (0x393b928, 0, 0x32c218): stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:wbemprox:wbem_locator_ConnectServer 0x155268, L"root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0xb53e9a4)
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
fixme:mountmgr:harddisk_ioctl unsupported ioctl 41018
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d0c10
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x154538, L"root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0xb83e974)
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data/FLEXnet" 1 1 0x4ad018 (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data/FLEXnet" 1 4 (nil) (nil) 0x4b0d30 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data/FLEXnet\\rosetta_003da900_event.log" 1 1 0x4b0c78 (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data/FLEXnet\\rosetta_003da900_tsf.data" 1 1 0x4b0c78 (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data/FLEXnet" 1 4 (nil) (nil) 0x4b0d88 (nil)
wine: cannot find L"C:\\windows\\system32\\taskkill.exe"


C:\Program Files\Rosetta Stone\Rosetta Stone Version 3\support\bin\win\\RosettaStoneLtdServices.exe [v072420082200] 

AUDIO ERROR
AUDIO ERROR
wine client error:28: pipe: Too many open files

---

### Post by Mia1990 on 2010-08-21
I have the same problem with wine 1.2 and 1.3 went back and installed 1.1.42 now rosetta stone works great.

---

### Post by zambezi on 2010-08-22
Hi 

Ok tried 1.1.42 (I had to compile it from source as Ubuntu links only to 1,0, 1,2 &1,3) .  Rosetta stone didn't run at all on this.  I have 10 computers to get working for a NGO trying to assist a community with basic literacy so rather frustrating.  I am thinking that I should install Ubuntu 9 or try another distro.

---

### Post by ronnielsen1 on 2010-08-22
It looked like you were trying to run version 3. Here's the winehq page. It might help

> To get the mic working (and showing in preferences -> my settings): 
in wineconfig audio tab: 

1 check alsa 
  UNCHECK oss (and others) 

2 EDIT ~/.asoundrc 
  comment out: 
   pcm.!default { type pulse } 
   ctl.!default { type pulse } 

   or comment out loading settings from ~/.asoundrc.asoundconf 
   if above lines are in there 

IMHO There is no need to kill pulseaudio.


[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10043](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10043)

---

### Post by zambezi on 2010-08-22
I am trying to run rosetta stone 3.4.5 (which is the latest)  but will try the suggestion.  I understand the first instruction clearly but the second & third are not clear where this takes place-  I assume in the terminal -  what directory should I be in ?  home ?

thanks

Paul

---

### Post by khelben1979 on 2010-09-10
Since Mia have told us in this thread that Rosetta Stone is working by using version 1.1.42 of the Wine software, one solution is to spend more time reading what you did wrong in compiling the software.

I've compiled different versions of Wine myself, and before compiling, it needs to go through a configure process where it shows if it lacks libraries which Wine needs. These libraries needs to get installed in your Ubuntu system if they are not already there, so they can be used by this Wine software when you compile it.

Just type ```
./configure
``` in the source directory and keep an eye on what the Wine configure process complains about, if you did not do this in the first place. It would be my recommendation.

---


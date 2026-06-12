---
title: "dotnet 2.0sp2"
date: 2010-08-06
forum: Wine
---

### Post by Yeeha on 2010-08-06
Interestingly theres no information about it at winehq only about 2.0 3.0 4.0 . It can be installed using winetricks but when i try to do it i get:

------------------------------------------------------
Instaling .net 2.0 runtime.  Can take several minutes.  See [http://wiki.winehq.org/MicrosoftDotNet](http://wiki.winehq.org/MicrosoftDotNet) for tips.
------------------------------------------------------
prerequisite gecko already installed, skipping
Executing cp -f /home/oliver/.winetrickscache/dotnet20/l_intl.nls /home/oliver/.wine/dosdevices/c:/windows/system32/
Executing wine /home/oliver/.winetrickscache/dotnet20/NetFx20SP2_x86.exe
fixme:clusapi:GetNodeClusterState ((null),0x32ec24) stub!
fixme:advapi:DecryptFileA "c:\\d7b5f464934722633ff32416428d6345\\" 00000000
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:advapi:LsaOpenPolicy ((null),0x33ef98,0x00000001,0x33efb4) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LsaOpenPolicy ((null),0x33e61c,0x00000001,0x33e644) stub
fixme:advapi:LsaClose (0xcafe) stub
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d0c00
fixme:advapi:LsaOpenPolicy ((null),0x33dd88,0x00000001,0x33ddb0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"oliver" (nil) 0x33a8c0 (nil) 0x33a8c4 0x33a8b8 - stub
fixme:advapi:LookupAccountNameW (null) L"oliver" 0x173828 0x33a8c0 0x1730f8 0x33a8c4 0x33a8b8 - stub
fixme:msi:MsiGetFeatureValidStatesW 1 L"NetFx20_SP1_enu_x86_net_SETUP" 0x33a968 stub returning 8
fixme:urlmon:CoInternetSetFeatureEnabled 8, 0x00000002, 0, stub
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
fixme:mountmgr:harddisk_ioctl unsupported ioctl 70c00
err:msi:remove_tracked_tempfiles failed to delete L"C:\\users\\oliver\\Temp\\msifcd.tmp"
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
err:ole:CoRevokeClassObject called from wrong apartment, should be called from 2200000023
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

If anyone has successfully installed it, i would be grateful for any info how to do it.

---


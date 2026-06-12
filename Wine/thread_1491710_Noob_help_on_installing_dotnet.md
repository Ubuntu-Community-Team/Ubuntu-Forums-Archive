---
title: "Noob help on installing dotnet"
date: 2010-05-23
forum: Wine
---

### Post by littlboz on 2010-05-23
Hey, I am a new user to wine and ubuntu. I want to play a video game called Ultima online and I need to install dotnet30. 

Now I have installed wine and wine tricks succesfully but I get this error:

boswell@boswell-desktop:~$ sh winetricks 
------------------------------------------------------
Instaling .net 3.0 runtime.  Can take 15-30 minutes.  See [http://wiki.winehq.org/MicrosoftDotNet](http://wiki.winehq.org/MicrosoftDotNet) for tips.
------------------------------------------------------
prerequisite dotnet20 already installed, skipping
Executing wine /home/boswell/.winetrickscache/dotnet30/dotnetfx3.exe
fixme:clusapi:GetNodeClusterState ((null),0x32ec9c,0) stub!
------------------------------------------------------
Note: command 'wine /home/boswell/.winetrickscache/dotnet30/dotnetfx3.exe' returned status 8.  Aborting.



Any suggestions?
oh, and before I forget I should say I am using Karmic Koala, as for other information I can't really give because I don't know how to find it out but feel free to tell me to type things into the terminal if need be .

---

### Post by Yeeha on 2010-05-24
When i install dotnet30 through latest winetricks on wine12rc1 into clean .wine dir i get, you do not have sufficient privileges to install... I have installed it fine before though... :S

---

### Post by Yeeha on 2010-05-24
I just tryed installing it from another user, same computer, same wine and there theres no problem?? That other user (where i tryed first) has no sudo rights could that be the problem? But wine doesnt even need to be ran as root?? Otherwise identical clean .wine directoryes same wine, same winetricks, same computer even... Any ideas whats the problem? :D

---

### Post by cogadh on 2010-05-24
@Yeeha
That sounds like a problem with the permissions on the .wine directory in your user's home directory. You should check to see if your user has full read/write permissions on that directory and subdirectories.

@littlboz
Are you sure .NET 3.0 is even required? Looking at the [AppDB entry for Ultima Online]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=228"), there is absolutely no mention of that as a requirement for installing or running the game. As a workaround, it appears some people simply install the game on a Windows machine and then copy the install directory into Wine and it works fine.

---

### Post by littlboz on 2010-05-24
really sorry guys, I am installing Wine on my mac and my ubuntu desktop. :-p I got a little mixed up when I posted this late at night.

I am still having trouble installing this though on Ubuntu. in the installer window it says

"Microsoft .NET Framwork 3.0 x86 has encountered a problem during setup. Setup did not complete correctly."

and then it asks if I want to send report or don't send it.

I will make a second post below that says all the terminal stuff

---

### Post by littlboz on 2010-05-24
boswell@boswell-desktop:~$ sh winetrickster
sh: Can't open winetrickster
boswell@boswell-desktop:~$ sh winetricks
------------------------------------------------------
Instaling .net 3.0 runtime.  Can take 15-30 minutes.  See [http://wiki.winehq.org/MicrosoftDotNet](http://wiki.winehq.org/MicrosoftDotNet) for tips.
------------------------------------------------------
prerequisite dotnet20 already installed, skipping
Executing wine /home/boswell/.winetrickscache/dotnet30/dotnetfx3.exe
fixme:clusapi:GetNodeClusterState ((null),0x32ec9c,0) stub!
fixme:advapi:DecryptFileA "c:\\04416056da5a90cf468307ca6f\\" 00000000
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:advapi:LsaOpenPolicy ((null),0x33f010,0x00000001,0x33f02c) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LsaOpenPolicy ((null),0x33e6b0,0x00000001,0x33e6d8) stub
fixme:advapi:LsaClose (0xcafe) stub
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d0c00
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d0c00 (device=2d access=0 func=300 method=0)
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d0c00
fixme:advapi:LsaOpenPolicy ((null),0x33de20,0x00000001,0x33de48) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"boswell" (nil) 0x33b0ec (nil) 0x33b0f0 0x33b0e4 - stub
fixme:advapi:LookupAccountNameW (null) L"boswell" 0x1fbe90 0x33b0ec 0x1fb398 0x33b0f0 0x33b0e4 - stub
fixme:msi:MsiGetFeatureValidStatesW 1 L"WAP_1.0_Core" 0x33ab8c stub returning 8
fixme:msi:MsiGetFeatureValidStatesW 1 L"Servicing_Key" 0x33ab8c stub returning 8
fixme:urlmon:CoInternetSetFeatureEnabled 8, 0x00000002, 0, stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
fixme:mountmgr:harddisk_ioctl unsupported ioctl 70c00
fixme:ntdll:server_ioctl_file Unsupported ioctl 70c00 (device=7 access=0 func=300 method=0)
fixme:mountmgr:harddisk_ioctl unsupported ioctl 70c00
fixme:clusapi:GetNodeClusterState ((null),0x33ec9c,0) stub!
fixme:advapi:DecryptFileA "c:\\69e95a8e45015f4557b7\\" 00000000
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:setupapi:StringTableAddStringEx 
fixme:setupapi:StringTableAddStringEx 
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
fixme:advapi:LookupAccountNameW (null) L"boswell" (nil) 0x33db94 (nil) 0x33db98 0x33db8c - stub
fixme:advapi:LookupAccountNameW (null) L"boswell" 0x1484900 0x33db94 0x1483e08 0x33db98 0x33db8c - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 5 ignored L"CreateFolder" table values
fixme:advapi:LookupAccountNameW (null) L"boswell" (nil) 0x7dfcfc88 (nil) 0x7dfcfc84 (nil) - stub
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
fixme:imm:ImmDisableIME (-1): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.

---

### Post by littlboz on 2010-05-24
Interestingly enough I am having the same problem on my Mac, using wine that came with the winebottler package.

---

### Post by littlboz on 2010-05-24
Just to note, my original problem is no longer what I need help with. The second one is what I need help with now

---

### Post by littlboz on 2010-05-24
Here is a screen shot to help out

---


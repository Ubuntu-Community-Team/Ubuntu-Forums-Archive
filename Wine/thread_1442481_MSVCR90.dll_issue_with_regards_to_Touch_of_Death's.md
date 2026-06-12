---
title: "MSVCR90.dll issue with regards to Touch of Death's Eclipse Game Engine"
date: 2010-03-30
forum: Wine
---

### Post by Ravenshade on 2010-03-30
Hi, 

I recently downloaded Wine and started to try installing the game engine when I come across a decidedly unusual error. 

```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT"
err:module:import_dll Library MSVCR90.dll (which is needed by L"D:\\Downloads\\Eclipse_Library_Installer_x86.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"D:\\Downloads\\Eclipse_Library_Installer_x86.exe" failed, status c0000135


```



Apparently placing the DLL into the system32 folder won't work. (I've tried, it didn't). 

I have followed the suggestions to have the vb2008 runtime files installed with no joy. 

(Latest Versions as of 30th March)


------------------------------------------------------------------

I've also tried adding in winetricks. Next time I have a bright idea, I'll look up the nearest tall building and forget to take a bungee cord. >_>. I added winetricks on the hope that this little instance would be helpful. Anyone know how to remove it and its effects?

Since I installed winetricks using wget then ran the following

```

sh winetricks vcrun2008

```

I know get the following <EDIT> Turns out this is probably due to the dist already being installed. As when I downloaded it the vc2008 package from microsoft I got a similar error. 

Skip down to see what I got after that. 

[SIZE="1"]```

err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
mkdir: cannot create directory `/home/ravenshade/.wine/dosdevices/c:': File exists
mkdir: cannot create directory `/home/ravenshade/.wine/dosdevices/c:': File exists
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
ln: creating symbolic link `/home/ravenshade/.wine/harddiskvolume0': File exists
Renamed drive_c to harddiskvolume0
Executing wine /home/ravenshade/.winetrickscache/vcrun2008-ms09-035/vcredist_x86.exe
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
fixme:clusapi:GetNodeClusterState ((null),0x32ec9c,0) stub!



```[/SIZE]


Here's what I got next

```
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT"
err:module:import_dll Library MSVCR90.dll (which is needed by L"D:\\Downloads\\Eclipse_Library_Installer_x86.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"D:\\Downloads\\Eclipse_Library_Installer_x86.exe" failed, status c0000135
ravenshade@KidayatoMetaFrame:~/Downloads$
```

...now if I removed winetricks, that'd get rid of those horrible errors just above I hope.

---

### Post by asdfoo on 2010-03-30
> **Ravenshade said:**
> Hi, 

I recently downloaded Wine and started to try installing the game engine when I come across a decidedly unusual error. 

```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT"
err:module:import_dll Library MSVCR90.dll (which is needed by L"D:\\Downloads\\Eclipse_Library_Installer_x86.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"D:\\Downloads\\Eclipse_Library_Installer_x86.exe" failed, status c0000135


```


Apparently placing the DLL into the system32 folder won't work. (I've tried, it didn't). 



No, that won't work - microsoft does not expect it to be in system32.

> 

I have followed the suggestions to have the vb2008 runtime files installed with no joy. 



vb2008?

I presume you mean vcrun2008.

> 
(Latest Versions as of 30th March)


------------------------------------------------------------------

I've also tried adding in winetricks. Next time I have a bright idea, I'll look up the nearest tall building and forget to take a bungee cord. >_>. I added winetricks on the hope that this little instance would be helpful. Anyone know how to remove it and its effects?

Since I installed winetricks using wget then ran the following

```

sh winetricks vcrun2008

```

I know get the following <EDIT> Turns out this is probably due to the dist already being installed. As when I downloaded it the vc2008 package from microsoft I got a similar error. 

Skip down to see what I got after that. 

[SIZE="1"]```

err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
mkdir: cannot create directory `/home/ravenshade/.wine/dosdevices/c:': File exists
mkdir: cannot create directory `/home/ravenshade/.wine/dosdevices/c:': File exists
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
ln: creating symbolic link `/home/ravenshade/.wine/harddiskvolume0': File exists
Renamed drive_c to harddiskvolume0
Executing wine /home/ravenshade/.winetrickscache/vcrun2008-ms09-035/vcredist_x86.exe
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
fixme:clusapi:GetNodeClusterState ((null),0x32ec9c,0) stub!



```[/SIZE]


Here's what I got next

```
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT"
err:module:import_dll Library MSVCR90.dll (which is needed by L"D:\\Downloads\\Eclipse_Library_Installer_x86.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"D:\\Downloads\\Eclipse_Library_Installer_x86.exe" failed, status c0000135
ravenshade@KidayatoMetaFrame:~/Downloads$
```

...now if I removed winetricks, that'd get rid of those horrible errors just above I hope.


Is the dll still in system32?
maybe your wineprefix is broken and you need to start a fresh one


eg, start by first installing vcrun2008 and then your program, it's the next thing to try anyway

---


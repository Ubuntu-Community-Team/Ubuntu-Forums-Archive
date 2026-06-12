---
title: "Need help with Steam+Fallout3"
date: 2010-09-29
forum: Wine
---

### Post by dracken on 2010-09-29
Hello, 

I am running Ubuntu 10.04, with the proprietary hardware drivers that install automatically for an ATI HD5770 card (FGLRX).

I tried installing steam and Fallout 3 GOTY through Playonlinux as well as Wine and while steam works just fine for both after I install fallout I can't start the program.  It simply doesn't load. I tried following the how to on the Wine app page to the letter and nothing...

I wonder if it might be because of the drivers. I have tried installing the drivers from the ATI website but that gave me an error...any words of advice?

Thank you very, very much for any and all suggestions.

---

### Post by P4man on 2010-09-29
try running it from a terminal, so you get some output that may shed light on the issue. Just open a terminal, then change directory to wherever you installed fallout (probably ~/.wine/drive_c/program files/.. ). Then run

```
wine fallout_or_whatever_its_called.exe
```

that will probably start filling your terminal with warnings and errors (it even does that when it works fine). Copy paste it here.

---

### Post by Half-Left on 2010-09-29
> **P4man said:**
> try running it from a terminal, so you get some output that may shed light on the issue. Just open a terminal, then change directory to wherever you installed fallout (probably ~/.wine/drive_c/program files/.. ). Then run

```
wine fallout_or_whatever_its_called.exe
```

that will probably start filling your terminal with warnings and errors (it even does that when it works fine). Copy paste it here.

PlayOnLinux users a different prefix to Wine as I remember and it caused me problems.

---

### Post by dracken on 2010-09-29
Thank you for your help. Here is what the terminal tells me:

```
fixme:actctx:razz:****_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.:cool:
fixme:win:EnumDisplayDevicesW ((null),0,0x32f368,0x00000000), stub!
wine: cannot find L"C:\\windows\\system32\\Fv\00c4{`@\00ec\0002\00f4\00cf\00c9{`\00fd2FalloutLauncher.exe"
fixme:msvcr90:__clean_type_info_names_internal (0x19aa1d4) stub
```

sounds like I need to re-install the windows live client, which unfortunately gives me another error: 

```
fixme:clusapi:GetNodeClusterState ((null),0x32ec24) stub!
fixme:advapi:grin:ecryptFileA "c:\\b853a6f52873718508\\" 00000000
fixme:module:load_library unsupported flag(s) used (flags: 0x00000000)
fixme:shell:MLSetMLHInstance (0x71590000,0x68430000) stub
fixme:shell:MLClearMLHInstance (0x71590000)stub
```Thanks for your help.

---

### Post by Half-Left on 2010-09-29
Try installing vcrun2008. You can use winetricks.

---

### Post by dracken on 2010-09-29
> **Half-Left said:**
> Try installing vcrun2008. You can use winetricks.


I tried that and got this error:

```
Renamed drive_c to harddiskvolume0
Executing wget -O vcredist_x86.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://download.microsoft.com/download/9/7/7/977B481A-7BA6-4E30-AC40-ED51EB2028F2/vcredist_x86.exe
--2010-09-29 21:00:44--  http://download.microsoft.com/download/9/7/7/977B481A-7BA6-4E30-AC40-ED51EB2028F2/vcredist_x86.exe
Resolving download.microsoft.com... 207.46.206.171, 207.46.206.151
Connecting to download.microsoft.com|207.46.206.171|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4485976 (4.3M) [application/octet-stream]
Saving to: `vcredist_x86.exe'

100%[======================================>] 4,485,976   2.43M/s   in 1.8s    

2010-09-29 21:00:45 (2.43 MB/s) - `vcredist_x86.exe' saved [4485976/4485976]

Using native,builtin override for following DLLs: msvcr90
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"*msvcr90"="native,builtin"
Executing wine /home/alex/.winetrickscache/vcrun2008-ms09-035/vcredist_x86.exe
fixme:clusapi:GetNodeClusterState ((null),0x32ec24) stub!
fixme:advapi:DecryptFileA "c:\\913225e1aaf007e8bf4e\\" 00000000
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:LsaOpenPolicy ((null),0x33f324,0x00000001,0x33f34c) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:advapi:LookupAccountNameW (null) L"alex" (nil) 0x7addbc (nil) 0x7addc0 0x7addb4 - stub
fixme:advapi:LookupAccountNameW (null) L"alex" 0x1a9080 0x7addbc 0x199070 0x7addc0 0x7addb4 - stub
fixme:advapi:LookupAccountNameW (null) L"alex" (nil) 0x7add88 (nil) 0x7add8c 0x7add80 - stub
fixme:advapi:LookupAccountNameW (null) L"alex" 0x1cf0b8 0x7add88 0x1cee18 0x7add8c 0x7add80 - stub
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
err:msi:ITERATE_Actions Execution halted, action L"MsiPublishAssemblies" returned 1627
------------------------------------------------------
Note: command 'wine /home/alex/.winetrickscache/vcrun2008-ms09-035/vcredist_x86.exe' returned status 91.  Aborting.
```

Should I maybe uninstall/ delete everything and start from scratch?

---

### Post by Half-Left on 2010-09-30
Go into the directory that it says at the bottom "/home/alex/.winetrickscache/vcrun2008-ms09-035/" and try running the vcredist_x86.exe with Wine.

---


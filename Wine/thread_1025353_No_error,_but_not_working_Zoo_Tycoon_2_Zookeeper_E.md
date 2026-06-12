---
title: "No error, but not working: Zoo Tycoon 2: Zookeeper Edition"
date: 2008-12-30
forum: Wine
---

### Post by moges on 2008-12-30
I am trying to run Zoo Tycoon 2: Zookeeper edition.

In the AppDB, it states that MFC42.dll is needed, (as are a couple of other things). I have done all of that, and got the program to install.

Now I cannot get the program to actually run. Running the program will result in the splash screen showing up, then the screen resolution changing and the screen going black (like it does in Windows when its loading the start), before the program exits and the screen resolution is returned to normal. No actual errors are show to the output, only fixme messages.

I am currently using either version 1.1.11 or 1.0.1-0ubuntu2. The same thing happens in both versions. It won't install in 1.1.11, but I tried installing in 1.0.1 and then upgrading, which has the same problem. Ubuntu is version 8.10, fully updated, and fresh install (I reinstalled it trying to get this working, but it didn't change anything). Sound is using ALSA, and my graphics is NVIDIA, using the 177.80 driver. I have found somewhere that turning GLX off works, but I tried that and no luck. I have tried with and without desktop effects, just in case that was causing a problem.

Here is the output when I run the installed program:
```
bob@serenity:~/.wine/drive_c/Program Files/Microsoft Games/Zoo Tycoon 2$ wine ZT.exe
fixme:atl:AtlAxWinInit semi-stub
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg1: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg2: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 3.
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4d004
fixme:reg:RegOpenUserClassesRoot (0xa0, 0x0, 0x2000000, 0x32eb74) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32eb48
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32eaf4
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32e468
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed74,0x00000000), stub!
fixme:reg:RegOpenUserClassesRoot (0xa0, 0x0, 0x2000000, 0x32f0ec) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {a65b8071-3bfe-4213-9a5b-491da4461ca7} 0x32f0c0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {a65b8071-3bfe-4213-9a5b-491da4461ca7} 0x32f06c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {a65b8071-3bfe-4213-9a5b-491da4461ca7} 0x32e9e0
fixme:reg:RegOpenUserClassesRoot (0xa0, 0x0, 0x2000000, 0x32e9f0) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32e9c4
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32e970
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32e2e4
fixme:reg:RegOpenUserClassesRoot (0xa0, 0x0, 0x2000000, 0x32e844) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32e818
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32e7c4
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32e138
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:reg:RegOpenUserClassesRoot (0xac, 0x0, 0x2000000, 0x32ec58) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32ec2c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32ebd8
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32e54c
fixme:reg:RegOpenUserClassesRoot (0xac, 0x0, 0x2000000, 0x32e2fc) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32e2d0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32e27c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} 0x32dbf0

```

The overrides I have are:
atlu
comcat
mfc42
mfc42u
mscvcirt
msccp60
msvcr80
msvcrt
ole32
oleaut32
olepro32

The important ones here are mfc42, msvcr80, ole32 and oleaut32. Without those, I get a whole bunch of error messages. The rest of the overrides were me overriding all of the dlls that are installed with winetricks when installing the MS Visual C++ 6.0 distributable (vcrun6). I have also tried copying over the dlls (both downloaded from the net and also copied from a windows xp SP2 computer I have available) manually, but that didn't work. I have also tried Cedega and cxgames, both of which were actually worse results then listed above.

---

### Post by cogadh on 2008-12-30
This concerns me:
```
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg1: Permission denied
```
Any idea what device that actually is?

---

### Post by moges on 2008-12-30
> **cogadh said:**
> This concerns me:
```
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg1: Permission denied
```
Any idea what device that actually is?

I was worried about that as well, however if I sudo wine ZT.exe (bad practise I know, but this was before I formatted my computer), then those error messages dissappear and the result is still the same. I'm not sure what they are, but I don't think it matters. I could be wrong though, so let me know if there is more information you need about these devices (and how to get it!).

---

### Post by moges on 2009-01-01
Some more information here, by running **WINEDEBUG=+reg,+loaddll**, it looks like the last thing the program does it look for the internationalization entries.

```
trace:reg:RtlOpenCurrentUser (0x000f003f, 0x32f2f0)
trace:reg:NtCreateKey ((nil),L"\\Registry\\User\\S-1-5-4",<null>,0,f003f,0x32f2f0)
trace:reg:NtCreateKey <- 0x9c
trace:reg:NtCreateKey (0x9c,L"Control Panel\\International",<null>,0,f003f,0x32f2f0)
trace:reg:NtCreateKey <- 0xa8
trace:reg:NtQueryValueKey (0xa8,L"sDecimal",2,0x1340b8,12)
trace:reg:RtlOpenCurrentUser (0x000f003f, 0x32f2d4)
trace:reg:NtCreateKey ((nil),L"\\Registry\\User\\S-1-5-4",<null>,0,f003f,0x32f2d4)
trace:reg:NtCreateKey <- 0x9c
trace:reg:NtCreateKey (0x9c,L"Control Panel\\International",<null>,0,f003f,0x32f2d4)
trace:reg:NtCreateKey <- 0xa8
trace:reg:NtQueryValueKey (0xa8,L"sDecimal",2,0x1340b8,18)
trace:reg:RtlOpenCurrentUser (0x000f003f, 0x32f2dc)
trace:reg:NtCreateKey ((nil),L"\\Registry\\User\\S-1-5-4",<null>,0,f003f,0x32f2dc)
trace:reg:NtCreateKey <- 0x9c
trace:reg:NtCreateKey (0x9c,L"Control Panel\\International",<null>,0,f003f,0x32f2dc)
trace:reg:NtCreateKey <- 0xa8
trace:reg:NtQueryValueKey (0xa8,L"sThousand",2,0x1340b8,12)
trace:reg:RtlOpenCurrentUser (0x000f003f, 0x32f2c4)
trace:reg:NtCreateKey ((nil),L"\\Registry\\User\\S-1-5-4",<null>,0,f003f,0x32f2c4)
trace:reg:NtCreateKey <- 0x9c
trace:reg:NtCreateKey (0x9c,L"Control Panel\\International",<null>,0,f003f,0x32f2c4)
trace:reg:NtCreateKey <- 0xa8
trace:reg:NtQueryValueKey (0xa8,L"sThousand",2,0x1340b8,18)
trace:reg:RtlOpenCurrentUser (0x000f003f, 0x32f2c8)
trace:reg:NtCreateKey ((nil),L"\\Registry\\User\\S-1-5-4",<null>,0,f003f,0x32f2c8)
trace:reg:NtCreateKey <- 0x9c
trace:reg:NtCreateKey (0x9c,L"Control Panel\\International",<null>,0,f003f,0x32f2c8)
trace:reg:NtCreateKey <- 0xa8
trace:reg:NtQueryValueKey (0xa8,L"sGrouping",2,0x1340b8,12)
trace:reg:RtlOpenCurrentUser (0x000f003f, 0x32f2b4)
trace:reg:NtCreateKey ((nil),L"\\Registry\\User\\S-1-5-4",<null>,0,f003f,0x32f2b4)
trace:reg:NtCreateKey <- 0x9c
trace:reg:NtCreateKey (0x9c,L"Control Panel\\International",<null>,0,f003f,0x32f2b4)
trace:reg:NtCreateKey <- 0xa8
trace:reg:NtQueryValueKey (0xa8,L"sGrouping",2,0x1340b8,22)

```

Has anyone come across this problem before? I am Australian, so my international entries will be slightly different from US, but these queries should still pick it up. I should also note that the output ends right there, no more is outputted at all after this. I imagine that this is the last thing the program does before it quits, as I can't see why it would need this information if it has already decided not to run. Also, I changed the locale to US using **LANG=en_US.UTF-8 WINEDEBUG=+reg wine ZT.exe** (which does update the registry at that point), but it didn't help, and error'd in the same place.

---

### Post by moges on 2009-01-04
I have tried the very latest dev build, 1.1.12, but there is still no luck with this. Does anyone have any ideas?

---


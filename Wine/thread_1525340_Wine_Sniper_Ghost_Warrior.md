---
title: "Wine Sniper Ghost Warrior"
date: 2010-07-06
forum: Wine
---

### Post by Uruchima on 2010-07-06
So it crashes before it even opens :S so this is what I got from terminal log:


uruchima@Xepher:~$ wine "c:\program files\city interactive\sniper ghost warrior\sniper_x86.exe"
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0xd4): stub
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
fixme:win:EnumDisplayDevicesW ((null),0,0x32e614,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
wine: Unhandled page fault on read access to 0x00000028 at address 0x103020d6 (thread 0009), starting debugger...

so I have no idea how to fix this, help?

---

### Post by Brebs on 2010-07-06
Check [appdb](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20656) - notice the "winetricks" command that you need to run, etc.

---

### Post by Uruchima on 2010-07-06
> **Brebs said:**
> Check [appdb](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20656) - notice the "winetricks" command that you need to run, etc.

I did that already but still getting this error:

uruchima@Xepher:~$ wine "c:\program files\city interactive\sniper ghost warrior\sniper_x86.exe"
fixme:atl:AtlModuleInit SEMI-STUB (0x10013248 0x10011930 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x10012fb0 0x10012210 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x10026f40 0x10026318 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x1000f750 0x1000f040 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x1001a720 0x10019408 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x1006de68 0x1006c898 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x10045960 0x10044708 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x10010f50 0x10010040 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x10010560 0x10010040 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x1000bc08 0x1000b030 0x10000000)
fixme:atl:AtlModuleInit SEMI-STUB (0x10057070 0x1004c830 0x10000000)
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0xd0): stub
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
fixme:win:EnumDisplayDevicesW ((null),0,0x32e614,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
wine: Unhandled page fault on read access to 0x00000028 at address 0x103020d6 (thread 0009), starting debugger...

---

### Post by Brebs on 2010-07-07
Look at the wine version shown on the appdb - 1.2rc5 - then compare it to your version...

---

### Post by Uruchima on 2010-07-07
> **Brebs said:**
> Look at the wine version shown on the appdb - 1.2rc5 - then compare it to your version...

Mine is 1.2rc6 still getting the same error though

---

### Post by asdfoo on 2010-07-08
> **Uruchima said:**
> Mine is 1.2rc6 still getting the same error though

try starting the program correctly, to do this you need to cd into the install directory and then run it (this is what happens on windows)

---


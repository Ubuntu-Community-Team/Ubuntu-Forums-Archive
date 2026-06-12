---
title: "tried everything, game wont run past startup"
date: 2011-02-23
forum: Wine
---

### Post by u-noob-tu on 2011-02-23
i am about to throw my computer against the wall in frustration. there is no reason why the game should not be running according to wine hq: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9237](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9237). the game is world in conflict, its about three years old, has a gold rating from wine, and my computer can easily handle it. but it just wont run. i get the error described in the guide above (which is supposed to happen) but instead of launching the game, the screen goes black and then shows my desktop. every single time. i have tried everything i could think of, but im all out of ideas. before i forget, heres my setup.

wine 1.2.2 with winetricks
ubuntu 10.10 x32

i just dont get it. ive been dying to play this game for about 2 months now. please help?

---

### Post by cogadh on 2011-02-24
Hardware specs? Did you follow the complete how-to instructions on the AppDB page you linked? What do you get from Wine for error output (run it from the terminal to get that)?

---

### Post by u-noob-tu on 2011-02-24
hardware is an dell studio 17 with 2.1 ghz processor with intel gpu and 3 gb of ram, which is enough to run the game. i followed the steps to the letter at least 5 separate times. the terminal output is attached.

---

### Post by cogadh on 2011-02-24
That's a mostly unreadable mess. Could you simply copy and post the output directly from the terminal into the thread using the forum [code] tags? It will make it much easier to deal with.

As for your hardware, the Intel GPU raises a red flag. Depending on which one it is, it probably can't run the game. Most integrated Intel hardware will be well below what is required for gaming on Windows, let alone gaming on Linux through Wine. Knowing the actual make/model of it should answer that definitively.

---

### Post by u-noob-tu on 2011-02-24
i didnt put the output here cuz i thought it would be unnecessarily long, but here it is: ```
   1.
      fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
   2.
      fixme:ntdll:NtQueryObject Unsupported information class 3
   3.
      err:rpc:I_RpcGetBuffer no binding
   4.
      fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
   5.
      fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
   6.
      fixme:win:EnumDisplayDevicesW ((null),0,0x19e8fb0,0x00000000), stub!
   7.
      fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
   8.
      fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
   9.
      fixme:win:EnumDisplayDevicesW ((null),0,0x19e8b30,0x00000000), stub!
  10.
      fixme:psapi:EnumPageFilesA (0x121b030, 0x19c9ca4) stub
  11.
      fixme:psapi:EnumPageFilesA (0x121b030, 0x19945c0) stub
  12.
      fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
  13.
      fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
  14.
      fixme:win:EnumDisplayDevicesW ((null),0,0x1937e68,0x00000000), stub!
  15.
      fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
  16.
      fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
  17.
      fixme:win:EnumDisplayDevicesW ((null),0,0x19379e8,0x00000000), stub!
  18.
      fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
  19.
      fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
  20.
      fixme:win:EnumDisplayDevicesW ((null),0,0x1937e6c,0x00000000), stub!
  21.
      fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
  22.
      fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
  23.
      fixme:win:EnumDisplayDevicesW ((null),0,0x19379ec,0x00000000), stub!
  24.
      fixme:cdrom:CDROM_GetMediaType : faking success
  25.
      fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
  26.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  27.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  28.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  29.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  30.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  31.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  32.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  33.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  34.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  35.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  36.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  37.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  38.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  39.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  40.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  41.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  42.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  43.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  44.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  45.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  46.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  47.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  48.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  49.
      fixme:ntdll:NtQuerySystemInformation (0x00000007,0x19c1f10,0x00000018,(nil)) stub
  50.
      fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
  51.
      fixme:cursor:SetSystemCursor (0x80214,00007f00),stub!
  52.
      fixme:cursor:SetSystemCursor (0x701fa,00007f00),stub!
  53.
      fixme:cursor:SetSystemCursor (0x701fc,00007f8a),stub!
  54.
      fixme:cursor:SetSystemCursor (0xc01fe,00007f03),stub!
  55.
      fixme:cursor:SetSystemCursor (0xc01dc,00007f01),stub!
  56.
      fixme:cursor:SetSystemCursor (0x150194,00007f88),stub!
  57.
      fixme:cursor:SetSystemCursor (0x1301cc,00007f86),stub!
  58.
      fixme:cursor:SetSystemCursor (0x170192,00007f83),stub!
  59.
      fixme:cursor:SetSystemCursor (0xc01d4,00007f82),stub!
  60.
      fixme:cursor:SetSystemCursor (0x900e6,00007f84),stub!
  61.
      fixme:cursor:SetSystemCursor (0xe01de,00007f04),stub!
  62.
      fixme:cursor:SetSystemCursor (0xc01f4,00007f02),stub!
  63.
      fixme:cursor:SetSystemCursor (0x80214,00007f00),stub!
  64.
      fixme:cursor:SetSystemCursor (0x1401da,00007f8a),stub!
  65.
      fixme:cursor:SetSystemCursor (0x1601ec,00007f00),stub!
  66.
      fixme:cursor:SetSystemCursor (0xa01f2,00007f03),stub!
  67.
      fixme:cursor:SetSystemCursor (0x60208,00007f01),stub!
  68.
      fixme:cursor:SetSystemCursor (0x1301ee,00007f88),stub!
  69.
      fixme:cursor:SetSystemCursor (0xf0178,00007f86),stub!
  70.
      fixme:cursor:SetSystemCursor (0x7020e,00007f83),stub!
  71.
      fixme:cursor:SetSystemCursor (0xa0152,00007f85),stub!
  72.
      fixme:cursor:SetSystemCursor (0x1401c6,00007f82),stub!
  73.
      fixme:cursor:SetSystemCursor (0x60212,00007f84),stub!
  74.
      fixme:cursor:SetSystemCursor (0xc01e0,00007f04),stub!
  75.
      fixme:cursor:SetSystemCursor (0xc01d2,00007f02),stub!
  76.
      fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
  77.
      fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
  78.
      fixme:ntdll:NtQueryObject Unsupported information class 3
  79.
      err:rpc:I_RpcGetBuffer no binding
  80.
      fixme:win:EnumDisplayDevicesW ((null),0,0x19fe138,0x00000000), stub!
  81.
      fixme:win:EnumDisplayDevicesW ((null),1,0x19fe138,0x00000000), stub!
  82.
      fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
  83.
      fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
  84.
      fixme:win:EnumDisplayDevicesW ((null),0,0x19fdbd8,0x00000000), stub!
  85.
      fixme:dxgi:dxgi_device_init Ignoring adapter type.
  86.
      fixme:win:EnumDisplayDevicesW ((null),0,0x19fd454,0x00000000), stub!
  87.
      fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
  88.
      fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
  89.
      fixme:win:EnumDisplayDevicesW ((null),0,0x19fccd8,0x00000000), stub!
  90.
      fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
  91.
      fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
  92.
      fixme:win:EnumDisplayDevicesW ((null),0,0x19fcd88,0x00000000), stub!
  93.
      fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
  94.
      fixme:faultrep:ReportFault 0x19f4844 0x0 stub

```intel has an annoying way of naming their graphics chips. as far as i can remember, mine is the x3100, aka GM45 (i think), and numerous other names. i would think that the chip wouldnt be a problem, as i have a newer pc game (2008 ) which has similar minimum specs and ran almost flawlessly under windows (havent tried on wine yet. dont know if its supported).

---

### Post by ajackson on 2011-02-25
> **u-noob-tu said:**
> i would think that the chip wouldnt be a problem, as i have a newer pc game (2008 ) which has similar minimum specs and ran almost flawlessly under windows (havent tried on wine yet. dont know if its supported).
Wine is not Windows, graphics are accessed through the OS drivers and a lot of Linux drivers are poor compared to their Windows counterparts.

---

### Post by u-noob-tu on 2011-02-25
> **ajackson said:**
> Wine is not Windows, graphics are accessed through the OS drivers and a lot of Linux drivers are poor compared to their Windows counterparts.

yes, thats true. but according to wine hq i shouldnt be getting any issues. i looked all over that guide and the posted comments and nowhere can i find a mention of the game not running because of inadequate hardware. the game complains about hardware on startup probably because (and i may be wrong) since its not running on windows, it probably doesnt know where to look for the right hardware in linux.

---

### Post by ajackson on 2011-02-25
I think, for the benefit of us lesser mortals, you need to re-read the stickies and post all the relevant information, including:

- Video card & driver version
- Wine version (I know you've done this)
- Version of the game (one of the bugs mentions that a patch removes the copy protection - could be an issue, the copy protection that is)
- Terminal output (without line numbers, post exactly what is displayed)
- Try a complete fresh Wine prefix, without any modifications (the stuff on the AppDB is pretty old)
- Try the latest wine (the 1.3 branch, see stickies)

Comments like "tried everything" don't help because if you had tried everything then no one could possible help you, so stick with actuals rather than fanciful overexagurrations (which I can't spell :)).

---

### Post by u-noob-tu on 2011-02-25
i apologize, i guess i didnt read the stickies thoroughly enough. what i meant by "tried everything", i meant "tried everything i could find". video card is called the x3100, but im not sure where to find the firmware version (additional drivers only had me install a wireless driver). the game version is 1.0, and i have a patch for version 1.9, but when i run it it says it cant find the game, even though i run the patch from the games folder. that might be the fix im looking for. heres the terminal output: ```
ryan@ryan-Studio-1737:~/.wine/dosdevices/c:/Program Files/Sierra Entertainment/World in Conflict$ wine wic.exe
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x19e8fb0,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x19e8b30,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x121b030, 0x19c9ca4) stub
fixme:psapi:EnumPageFilesA (0x121b030, 0x19945c0) stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x1937e68,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x19379e8,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x1937e6c,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x19379ec,0x00000000), stub!
fixme:cdrom:CDROM_GetMediaType : faking success
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x19c1f10,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:cursor:SetSystemCursor (0x20022,00007f00),stub!
fixme:cursor:SetSystemCursor (0x10082,00007f00),stub!
fixme:cursor:SetSystemCursor (0x10084,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x10086,00007f03),stub!
fixme:cursor:SetSystemCursor (0x10088,00007f01),stub!
fixme:cursor:SetSystemCursor (0x1008a,00007f88),stub!
fixme:cursor:SetSystemCursor (0x1008c,00007f86),stub!
fixme:cursor:SetSystemCursor (0x1008e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x10090,00007f82),stub!
fixme:cursor:SetSystemCursor (0x10092,00007f84),stub!
fixme:cursor:SetSystemCursor (0x10094,00007f04),stub!
fixme:cursor:SetSystemCursor (0x10096,00007f02),stub!
fixme:cursor:SetSystemCursor (0x20022,00007f00),stub!
fixme:cursor:SetSystemCursor (0x70056,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x70058,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1005e,00007f03),stub!
fixme:cursor:SetSystemCursor (0x10060,00007f01),stub!
fixme:cursor:SetSystemCursor (0x10064,00007f88),stub!
fixme:cursor:SetSystemCursor (0x10068,00007f86),stub!
fixme:cursor:SetSystemCursor (0x1006c,00007f83),stub!
fixme:cursor:SetSystemCursor (0x10070,00007f85),stub!
fixme:cursor:SetSystemCursor (0x10074,00007f82),stub!
fixme:cursor:SetSystemCursor (0x10078,00007f84),stub!
fixme:cursor:SetSystemCursor (0x1007c,00007f04),stub!
fixme:cursor:SetSystemCursor (0x10080,00007f02),stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x19fe138,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x19fe138,0x00000000), stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x4733340, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x4f7362d4)
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:win:EnumDisplayDevicesW ((null),0,0x19f7a28,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x19f76e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x19f7a28,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x19f7d04,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x19f79ec,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x19fcd8c,0x00000000), stub!
fixme:winsock:WSAEnumNameSpaceProvidersA (0x19e8460 0x19e9cd8) Stub!
fixme:imm:ImmReleaseContext (0x1009a, 0x190bc8): stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x19fd66c,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x19fe1d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x19fe1d8,0x00000000), stub!
ryan@ryan-Studio-1737:~/.wine/dosdevices/c:/Program Files/Sierra Entertainment/World in Conflict$ 

```by fresh wine prefix, do you mean a fresh wine install? ill give 1.3 a shot. i think getting the patch to work might be the answer.

---

### Post by cogadh on 2011-02-25
You can ignore all those "fixme" messages as they are really only developer notes, but you do have a couple of real errors in there, only one of which might be fixable (though fixing one might negate the other). Use winetricks to install the dcom98 and ole2 "packages" and it should make the "err:ole:CoGetClassObject" messages go away (note I said "should"). The other "err:rpc:I_RpcGetBuffer" messages refer to what I believe is an unimplemented function in Wine, so it really can't be fixed unless you plan on coding a patch for Wine.

---

### Post by u-noob-tu on 2011-02-25
> **cogadh said:**
> You can ignore all those "fixme" messages as they are really only developer notes, but you do have a couple of real errors in there, only one of which might be fixable (though fixing one might negate the other). Use winetricks to install the dcom98 and ole2 "packages" and it should make the "err:ole:CoGetClassObject" messages go away (note I said "should"). The other "err:rpc:I_RpcGetBuffer" messages refer to what I believe is an unimplemented function in Wine, so it really can't be fixed unless you plan on coding a patch for Wine.

i found "ole2", but dcom98 doesnt seem to be in winetricks (at least in the version i have, which should be the latest). im confused, this game has a gold rating from wine, so how can there be an unimplemented function in wine that this game is trying to use? wouldnt someone have seen that?

---

### Post by cogadh on 2011-02-25
AFAIK, the dcom98 package has been a part of winetricks since the beginning and it is still listed as part of the current version. Get the latest winetricks here: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

A gold rating just means that it is relatively easy to get the application to run, but you might still need to tweak a few things, like installing a few native libraries to cover Wine's shortcomings. Only a platinum rating means the the application will run right out of the box without any tweaking on your part.

---

### Post by u-noob-tu on 2011-02-25
just downloaded winetricks from the link, ran it, and dcom98 still is not there. odd. could you provide the file yourself, please?

---

### Post by cogadh on 2011-02-26
How are you running winetricks? If you are using winetricks' limited GUI, it doesn't really list everything winetricks can do. All you need to do is open a terminal and run "sh winetricks dcom98" and it should install the dcom libraries with no problems.

---

### Post by u-noob-tu on 2011-02-26
tried to install dcom98 but i got a message saying that modern wine doesnt need it.

---

### Post by bobwyajnr on 2011-02-26
> **cogadh said:**
> 
A gold rating just means that it is relatively easy to get the application to run, but you might still need to tweak a few things, like installing a few native libraries to cover Wine's shortcomings. Only a platinum rating means the the application will run right out of the box without any tweaking on your part.

I wrote this rating for WIC:
[World in Conflict - Soviet Assault Addon]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16192"). I was running it under Steam. The game works very well when run through Wine. It is necessary to disable DX10.0 support in Wine (only thing stopping it being platinum really). :popcorn:

Now after that good news. The bad!! If you want a gaming laptop you need to pony up for one!! Intel don't make 'real' GPUs and never have. WIC will be a slide show if you tried to run it on Windows using an Intel integrated 'graphics' card (if it would even run). Under Linux the Intel MESA driver isn't really up to allowing Wine to fully emulate DX9.0c graphics yet. It claims capabilities it doesn't have (that are actually emulated in software or are only partially supported)... 	:-({|=

Give it another 5 years or so and reopen this thread... Or get a laptop with an Nvidia GPU (>310M) in your next refresh... There are Ubuntu forums threads 100's of pages long trying to deal with Intel graphics problems. WIC (basically) just works on Ubuntu+WINE+Nvidia GPU. With an AMD card the game will probably run but may have graphical glitches. ):P

Bob

---

### Post by u-noob-tu on 2011-02-26
ah, that sucks, but thanks for solving the issue. damn you intel!!! i just want to play the game!!!

---

### Post by cogadh on 2011-02-27
> **u-noob-tu said:**
> tried to install dcom98 but i got a message saying that modern wine doesnt need it.
News to me, and really odd, especially considering the error you got specifically references a dcom related problem.

---


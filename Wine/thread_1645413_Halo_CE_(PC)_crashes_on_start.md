---
title: "Halo CE (PC) crashes on start"
date: 2010-12-14
forum: Wine
---

### Post by Ligerzero_942 on 2010-12-14
I've been trying to get Halo CE to work on Wine. The installer worked just fine and so did the update so that I won't need a CD.  However when I try to run the game it just crashes and gives me the "has encountered a problem and needed to close", and this error in the CLI:

> err:ole:CoCreateInstance apartment not initialised
err:devenum:DEVENUM_RegisterQuartz Failed to register Quartz. Error was 0x800401f0)
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfdc
fixme:iphlpapi:NotifyAddrChange (Handle 0x255e8d8, overlapped 0x255e8e0): stub
wine: configuration in '/home/ethan/.wine' has been updated.
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32d1e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32cc84,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32c508,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32c5b8,0x00000000), stub!
fixme:dxdiag:ProcessCommandLine /t unimplemented
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:RegisterEventSourceW ((null),L"Halo"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x00000054,0x5dd83c,0x5dd3f4): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x00000054,0x12d1e8,0x5dd3f4): stub
err:eventlog:ReportEventW L"halo.exe"
err:eventlog:ReportEventW L"1.0.0.564"
err:eventlog:ReportEventW L"quartz.dll"
err:eventlog:ReportEventW L"6.5.1.902"
err:eventlog:ReportEventW L"00001dec"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
I believe I'm using the newest version of Wine.

---

### Post by AllRadioisDead on 2010-12-14
You're using intel graphics, good luck getting anything 3D to run with that.

---

### Post by Ligerzero_942 on 2010-12-15
Really? I have Unreal Tournament '04 running native, and it's just fine.

---

### Post by AllRadioisDead on 2010-12-15
> **Ligerzero_942 said:**
> Really? I have Unreal Tournament '04 running native, and it's just fine.

I'm not sure what kind of framerate you're getting, but native game will generally perform better than Wine applications.

---


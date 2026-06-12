---
title: "Screwed up graphics in StarCraft II"
date: 2011-06-22
forum: Wine
---

### Post by Triblaze on 2011-06-22
I installed StarCraft II and use it in Wine. After a bunch of odds and ends, I got it working. Kinda. Not really. Most of the game runs fine except the most important part, the matches themselves. i can log in, all the menus are fine and run smoothly.

But when I go into a match, I get a garbled mess. The odd thing is, sometimes it works. Sometimes I boot it up and it just works, runs even smoother than on my mom's windows computer.

But around 90% of the time, it just goes nuts. I don't really know what I do to get it to work when it does.

How do I fix this?

Here's the terminal readout:

```
~/.wine/harddiskvolume0/Program Files/StarCraft II$ wine StarCraft\ IIfixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 2000
fixme:win:EnumDisplayDevicesW ((null),0,0x107c10c,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
cd@guitar:~/.wine/harddiskvolume0/Program Files/StarCraft II$ fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x16f138, 0x449f0d4
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x449ed5c,0x449ed60): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:win:EnumDisplayDevicesW ((null),0,0x449e7fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x449e740,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x449f1a0): stub
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
fixme:msctf:ThreadMgrSource_AdviseSink (0x218e70) Unhandled Sink: {71c6e74e-0f28-11d8-a82a-00065b84435c}
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x4496b18,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x4496de8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x4496dd8,0x00000000), stub!
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:imm:ImmReleaseContext (0x4005a, 0x1747c0): stub
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used


I BELIEVE THE PROBLEMS START SOMEWHERE AROUND HERE, EVERYTHING UP TO THIS IS FINE, MAY BE A BIT OFF. I CAN DOUBLE CHECK IF NEED BE.


fixme:process:GetProcessWorkingSetSize (0xffffffff,0x449cd8c,0x449cd90): stub
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x448f674,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x448f924,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x448f914,0x00000000), stub!
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
fixme:win:EnumDisplayDevicesW ((null),0,0x448f674,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x448f924,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x448f914,0x00000000), stub!
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table

```
Running Maverick, Wine 1.2.3, I try both Windows XP and Windows 7, if I recall I've gotten it working on both but I don't think either is more reliable, both usually result in this. Think this is the graphics card, not sure: VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
It says I'm using the proprietary drivers on the card, I believe mmdevapi is disabled in Wine.

Anything else you need to know?

Screencap attached, have to run it as windowed, which I'm fine with. Fullscreen makes the computer go insane.

---

### Post by Tweak42 on 2011-06-25
Try using a newer wine version.  All the working reports on the appdb are using 1.3.x

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

---

### Post by Triblaze on 2011-07-02
> **Tweak42 said:**
> Try using a newer wine version.  All the working reports on the appdb are using 1.3.x

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)
I upgraded, but upon firing it up, I got the same results as before. Do I need to configure some of the settings or something?


Sorry for the week long bump, was gone this week.

---

### Post by Tweak42 on 2011-07-05
> **Triblaze said:**
> I upgraded, but upon firing it up, I got the same results as before. Do I need to configure some of the settings or something?


Sorry for the week long bump, was gone this week.

You can try posting for help on the wine appdb entry for[ Starcraft II]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882").  I had a strange shader issue running my SC2 such that I had to turn some of the grfx details down to low or the rendering once playing the game was all blurred out.  It was playable, but not as pretty looking as in windows. :(  I'm using Nvidia though so your experience maybe completely different.

---

### Post by Triblaze on 2011-07-06
> **Tweak42 said:**
> You can try posting for help on the wine appdb entry for[ Starcraft II]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882").  I had a strange shader issue running my SC2 such that I had to turn some of the grfx details down to low or the rendering once playing the game was all blurred out.  It was playable, but not as pretty looking as in windows. :(  I'm using Nvidia though so your experience maybe completely different.
Thanks, I'll check that.

At first, after posting it wasn't working, I got it working several times in a row and thought it had started working, but today it's all messed up again even after a few restarts. Up grading seems to make it work more often, maybe, but still fail plenty of times. I'll check there.

---


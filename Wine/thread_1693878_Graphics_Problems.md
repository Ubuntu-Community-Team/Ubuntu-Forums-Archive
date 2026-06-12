---
title: "Graphics Problems"
date: 2011-02-23
forum: Wine
---

### Post by Zalib on 2011-02-23
Ok people I'm stumped I have orm=backbuffer and glsl-disabled and this is what I get.

First one is on login.

Second in the main menu.

Third is in single player vs AI

---

### Post by An Sanct on 2011-02-23
Which version of wine is this on and are you using winetricks?

---

### Post by Zalib on 2011-02-23
wine 1.3 I believe it's the beta release. And yes that's how I turned off glsl and set orm=backbuffer

---

### Post by Zalib on 2011-02-23
Shameless bump. I'm tired of this problem and I want to get back to playing Starcraft. :(

---

### Post by Soulcage on 2011-02-24
Did you read this sticky first? [http://ubuntuforums.org/showthread.php?t=885111]("http://ubuntuforums.org/showthread.php?t=885111")
It looks like you're trying to use a intel gpu to play. You would have the best results on a nvidia card.

---

### Post by An Sanct on 2011-02-24
Yes, the sticky states my next question ... the terminal output ...

If that would be included in the first post...

---

### Post by Zalib on 2011-02-24
Alright I installed the proprietary drivers and the launcher said the drivers were out of date and would cause problems. However the video does work. Everything is just slow.

My card is a ATI Readon Mobility 4200

---

### Post by Zalib on 2011-02-24
```
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 2000
fixme:win:EnumDisplayDevicesW ((null),0,0x107c10c,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
zalib@Zalib:~/.wine/drive_c/Program Files/StarCraft II$ fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x16bd60, 0x434efbc
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x434ed50,0x434ed54): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:win:EnumDisplayDevicesW ((null),0,0x434e800,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x434e744,0x00000000), stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16_FLOAT
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32_FLOAT
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16B16A16_FLOAT
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32G32B32A32_FLOAT
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16B16A16_FLOAT
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32G32B32A32_FLOAT
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16_FLOAT
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32G32_FLOAT
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
fixme:win:EnumDisplayDevicesW ((null),0,0x434e4b0,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:win:EnumDisplayDevicesW ((null),0,0x434e488,0x00000000), stub!
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
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x67d5228,0x7029528): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x6e4e3e0,0x6e50aa0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x6e4e3e0,0x2045d0): stub
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
fixme:win:EnumDisplayDevicesW ((null),0,0x4346b1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x4346dec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x4346ddc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x4346b70,0x00000000), stub!
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
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:imm:ImmReleaseContext (0x3005e, 0x171460): stub
fixme:d3d:IWineD3DDeviceImpl_SetRenderTarget Trying to set render target 0 to NULL

```


This is terminal output starting starcraft up to the login screen and then logging out.

---

### Post by Omega420 on 2011-12-21
This is the same exact problem i am having. using the newest version of wine

Fedora 16 64bit
[FONT=monospace]processor AMD Turion(tm) 64 X2 Mobile Technology TL-58 × 2
Graphics Gallium 0.4 on ATI RS690

What else you need to know? cuz this problem is over several 3d games but from the looks of this guys screenshots this is my problem.
[/FONT]

---


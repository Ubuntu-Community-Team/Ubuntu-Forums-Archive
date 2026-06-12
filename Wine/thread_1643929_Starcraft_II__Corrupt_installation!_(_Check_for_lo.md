---
title: "Starcraft II : Corrupt installation?! ( Check for log inside )"
date: 2010-12-12
forum: Wine
---

### Post by SuperXDE on 2010-12-12
Hello~! 

I've had some trouble with Wine for a looong while , till I was so bored and I couldn't play my games , till I found about wine tricks , and started Having fun on it , as well as installing my favourite windows games... However My Starcraft II , which is installed by a digital version seems not to work , saying that Installation is Corrupt , after I installed and patched it , I tried to get a log from the terminal by running wine Starcraft\ II.exe from its location on Drive C inside the .wine folder , and here is what I got.

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 2000
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:win:EnumDisplayDevicesW ((null),0,0x118c10c,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
sharif@ubuntu:~/.wine/drive_c/Program Files/StarCraft II$ fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x138948, 0x466f0e8
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x466ed78,0x466ed7c): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:win:EnumDisplayDevicesW ((null),0,0x466e810,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x466e754,0x00000000), stub!
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
fixme:win:EnumDisplayDevicesW ((null),0,0x466ed08,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x466e5e8,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:win:EnumDisplayDevicesW ((null),0,0x466e5c0,0x00000000), stub!
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
fixme:msctf:ThreadMgrSource_AdviseSink (0x714ed60) Unhandled Sink: {71c6e74e-0f28-11d8-a82a-00065b84435c}
err:module:import_dll Library CRYPT32.dll (which is needed by L"C:\\Program Files\\StarCraft II\\Support\\Battle.net.dll") not found

```

I tried to reinstall Crypt32 using Winetricks , but still the problem persists , and I have no idea what to do about it , also that first part about OpenGL seems to be interesting , so interesting that I didn't understand -_-" 

I've been working on SC2 the whole day , but yet ... no results , and my weekend was spent on it already , I would appreciate if someone could lend me a hand over here , and tell me what to do so I could get it working , also to make me learn more about Linux and Wine , so I could make everyone around me use'em.

Thanks in advance!

---

### Post by 8Kuula on 2010-12-12
have you tried to run SC2 in default wineprefix?

---

### Post by SuperXDE on 2010-12-13
I've read this word , wineprefix , much times ... But ¬¬" I don't know what a Wineprefix is , nor how to , or how is it possible :D , Please more details.

---

### Post by 8Kuula on 2010-12-13
By default wine creates it's working directory to ~/.wine. But it can be changed to create multiple wine "enviroments".

Per command basis:
$ env WINEPREFIX=/home/SuperXDE/.wine-sc2 winecfg
$ env WINEPREFIX=/home/SuperXDE/.wine-sc2 wine ./program.exe

Change prefix until terminal is closed:
$ export WINEPREFIX=/home/SuperXDE/.wine-sc2
$ winecfg
$ wine ./program.exe

When creating new prefix run "winecfg" command, so wine creates new directory and default "enviroment" to that directory. After that it is not needed, except if you change configuration in that enviroment.

---

### Post by SuperXDE on 2010-12-13
I will try it , then tell you the results ( I should create the .wine-sc2 folder manually , shouldn't I? )

---

### Post by 8Kuula on 2010-12-14
> **SuperXDE said:**
> I will try it , then tell you the results ( I should create the .wine-sc2 folder manually , shouldn't I? )
(if you want to)

---

### Post by SuperXDE on 2010-12-15
I've tried a wineprefix , and it launched the game (Thanks , it was very relieving ), however a series of errors appeared showing 
```
sharif@ubuntu:~$ env WINEPREFIX=/home/sharif/.wine-sc2 wine /home/sharif/.wine/drive_c/Program\ Files/StarCraft\ II/StarCraft\ II.exe
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 2000
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:win:EnumDisplayDevicesW ((null),0,0xf7c10c,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
sharif@ubuntu:~$ fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x170e80, 0x440f0e8
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x440ed78,0x440ed7c): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:win:EnumDisplayDevicesW ((null),0,0x440e810,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x440e754,0x00000000), stub!
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
fixme:win:EnumDisplayDevicesW ((null),0,0x440e5e8,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:win:EnumDisplayDevicesW ((null),0,0x440e5c0,0x00000000), stub!
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x772ea38): stub
fixme:msctf:ThreadMgrSource_AdviseSink (0x68ece40) Unhandled Sink: {71c6e74e-0f28-11d8-a82a-00065b84435c}
fixme:d3d:query_init Event query: Unimplemented, but pretending to be supported.
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0xbabea38): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0xbabea38): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0xbabea38): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0xc44ea2c): stub
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
fixme:win:EnumDisplayDevicesW ((null),0,0x44070ac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x4407380,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x4407370,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x4407104,0x00000000), stub!
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x1f06ea38): stub
fixme:mmdevapi:AEV_GetMute stub
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
fixme:d3d:query_init Event query: Unimplemented, but pretending to be supported.
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:imm:ImmReleaseContext (0x4005c, 0x175e68): stub
X Error of failed request:  GLXBadRenderRequest
  Major opcode of failed request:  160 (GLX)
  Minor opcode of failed request:  1 (X_GLXRender)
  Serial number of failed request:  10543
  Current serial number in output stream:  10544
AL lib: ALc.c:1879: exit(): closing 2 Devices
AL lib: ALc.c:1808: alcCloseDevice(): destroying 1 Context(s)
AL lib: ALc.c:1420: alcDestroyContext(): deleting 2 Source(s)
AL lib: ALc.c:1818: alcCloseDevice(): deleting 8 Buffer(s)


```

Summary : I believe it's related to the OpenGL drivers...

So ... what should I do ? Allow direct rendering through the registry?

---

### Post by 8Kuula on 2010-12-15
Hmm, I put my hands up :/

Thou line: "err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly"
So it may be display driver problem.
I have no clue how to fix that thou...

<edit>
If it launches game, and works then just play and ignore errors :P
Those "fixme: blabla" are more for wine coders, I think.
If do not work those "err: something" lines are useful, atleast for someone who knows more about wine than me :]
</edit>

---

### Post by SuperXDE on 2010-12-16
Oh thanks , I've discovered a way to solve it , I just reinstalled my ATI driver , using the one provided on AMD's website instead of the one provided by Ubuntu ( Jockey ) , and edited the xorg.conf to allow Direct Rendering ¬ Whew! , That was a pain!.

It is now working good , Thank you very much , it wouldn't have worked without your assistance! :KS

---


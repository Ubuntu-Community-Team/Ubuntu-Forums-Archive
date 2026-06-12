---
title: "Weird Graphical Error in Starcraft 2 Retail"
date: 2010-07-28
forum: Wine
---

### Post by MeisBarry on 2010-07-28
**My info:**
Ubuntu 10.04 x64
wine version 1.2 with mmdevapi disabled, ALSA
ATI Radeon HD card using proprietary drivers

I've reinstalled the drivers multiple times, using tutorials from at least half a dozen different sources.  They are installed and being used.

Anyway, when I run SC2, everything starts out fine graphically.  The loading screen looks fine, and sometimes the login screen will be visible before the loading screen pops up.  This too, looks fine.

Just before loading finishes and it boots to the login, my screen gets cut into 4 vertical strips, evenly spaced.  The leftmost strip looks normal.  The other three each have a different pattern of garbled boxes, completely destroying any hope of trying to log in, change options, or play.  My uneducated opinion is that something is loaded then (module, texture, something) that causes wine/ATI to go haywire.

I have a feeling it's a problem with the drivers, but I've tried for hours between last night and tonight, and haven't made any progress.

One thing worth noting:  I put a crappy old Nvidia card in last night, and using that the game ran fine (albeit with sub-par graphics). 


Here's the wine puke.  Most of the "err"s pertain to audio, but that seems to be fine.

```
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 2000
fixme:win:EnumDisplayDevicesW ((null),0,0xf7c10c,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
 fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x139878, 0x43cf0e8
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x43ced78,0x43ced7c): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:win:EnumDisplayDevicesW ((null),0,0x43ce810,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x43ce754,0x00000000), stub!
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
fixme:win:EnumDisplayDevicesW ((null),0,0x43ced08,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x43ce128,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:win:EnumDisplayDevicesW ((null),0,0x43ce100,0x00000000), stub!
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
fixme:mixer:ALSA_MixerInit No master control found on C-Media USB Headphone Set  , disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:msctf:ThreadMgrSource_AdviseSink (0x79c0298) Unhandled Sink: {71c6e74e-0f28-11d8-a82a-00065b84435c}
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1be3e0) : pBox=(nil) stub
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
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
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1be3e0) : pBox=(nil) stub
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
fixme:win:EnumDisplayDevicesW ((null),0,0x43cd854,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x43cdb28,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x43cdb18,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x43cd8b0,0x00000000), stub!
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
fixme:d3d:getFormatDescEntry Can't find format unre
```

UPDATE:  The above error is fixable via opening winetricks and setting orm=backbuffer.  This makes the game "playable", but most text is still not displayed in-game.  See post #8.

---

### Post by asdfoo on 2010-07-29
are you using catalyst 10.7 with the ati card?

for the nvidia, people I've talked to who play sc2 on windows say the requirements are quite high, so I don't know which card you have... probably an 8600 or better would be ideal, but again, most recent nvidia drivers would be useful too.

---

### Post by _h_ on 2010-07-29
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)


Saw something about ATI graphical things in the comments, maybe could help.

---

### Post by MeisBarry on 2010-07-29
My Nvidia is a 7600.  It ran but it isn't a permanent solution.

I was using 10.7, (from ATI, not the repo) and the problems persisted.  But with all of the talk in appdb about it, I'm starting to think I must have not fully uninstalled everything properly when I installed them, as hard as I tried :P

I'll try again later today.

---

### Post by MeisBarry on 2010-07-29
Hmm, here's a possible issue...

When I run the 10.7 file I had originally used, I see...

[IMG]http://i134.photobucket.com/albums/q91/meisbarry/Screenshot.png[/IMG]

I have it partially covered, but in the terminal behind it, you can see that the file I'm running is 10.7, but the driver window itself is 8.something.  Normal?

---

### Post by MeisBarry on 2010-07-29
I have exhausted every tutorial, suggestion, and inkling I've had without any luck.  Everything seems to be installed correctly, but the result is the same.

Is there a way to confirm that 10.7 is actually the driver I'm using?  I don't see it listed anywhere in glxinfo or lspci.  Running fglrxinfo does say I'm using ATI drivers, but won't give me the version.

---

### Post by oraqol on 2010-08-01
Same problem here.  ATI vid card, installed Catalyst 10.7 but when I try to run SC2 it crashes right after splash screen.  With default fglrx driver the game runs but I get "scrambled" graphics. Also after installing 10.7 and rebooting the Catalyst Administration option disappears from /System/Preferences.  Tried full uninstall of both fglrx and 10.7 using their uninstall scripts. I'm starting to hate ATI, no love for tux.

HP dv4 laptop
Ubuntu 10.04
Mobility Radeon HD 4200

---

### Post by MeisBarry on 2010-08-10
I fixed this issue by opening winetricks and setting orm=backbuffer.  The original graphical error disappeared.

I don't really want to call it solved, though, since this uncovered a separate issue; missing text.  The main menu is ok, but once I enter a game, most text is missing save a few letters speckled about.  It's annoying enough to force me to play in another OS.

I don't suppose anyone has found a fixed for this other than buying a Nvidia and replacing the ATI card?

---

### Post by urbanus on 2010-08-12
I have the same problem, but found a poor solution:
[http://ubuntuforums.org/showpost.php?p=9710988&postcount=48](http://ubuntuforums.org/showpost.php?p=9710988&postcount=48)

Maybe someone can build upon this solution to get better performance?

---

### Post by MeisBarry on 2010-08-12
It removes the errors with the text (or does not cause them)?  I'll try it out tonight when I'm back at my box.

---

### Post by gloken on 2010-08-12
> **MeisBarry said:**
> I fixed this issue by opening winetricks and setting orm=backbuffer.  The original graphical error disappeared.

I don't really want to call it solved, though, since this uncovered a separate issue; missing text.  The main menu is ok, but once I enter a game, most text is missing save a few letters speckled about.  It's annoying enough to force me to play in another OS.

I don't suppose anyone has found a fixed for this other than buying a Nvidia and replacing the ATI card?

I had this problem with an ATI card, and solved the problem by switching to nvidia. I was on the 2.6.35 kernel, the 10.7 Catalyst and doing everything else that supposedly works. I'm honestly not sure it's worth the fight, but good luck if you choose to press on.

---

### Post by urbanus on 2010-08-12
I have to agree with gloken, things may change and a lot of progress is made on the ati open source drivers etc, but for now one should stick with Nvidia when gaming in Linux.

My laptop with a GeForce 9650m GT plays StarCraft 2 a h#%¤l of a lot faster than my Ati HD4870x2 in Linux. This is the harsh reality :-/

---


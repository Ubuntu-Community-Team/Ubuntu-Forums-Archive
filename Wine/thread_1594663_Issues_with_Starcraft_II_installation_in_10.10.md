---
title: "Issues with Starcraft II installation in 10.10"
date: 2010-10-12
forum: Wine
---

### Post by Tritan on 2010-10-12
Hello,

I have a serious issue with installing Starcraft II on my PC. I get the same result when starting the Installer.exe through Wine, CrossOver games or using PlayOnLinux - all seam to suffer from the same issue;

[IMG]http://img146.imageshack.us/img146/2851/sc2d.gif[/IMG]

I've already tried both the DVD and the digital download, I've mounted the image and DVD in various ways, I've updated my Wine with the tricks mentioned [here]("http://ubuntuforums.org/showthread.php?t=1435314&highlight=starcraft") and on various other sites. 

I've also ran it as root and I've searched through most of the Google hits I get for this problem. The funny part is that I figured out how to mount the ISO correctly so that the installer does not complain about not being able to access the installer information, but right now it just gets stuck after I click install. 

A few details about my system;

Intel i5 750
ATi 5770 ultra
4GB DDR3
OCZ SSD HD

Ubuntu 10.10 _x64_ fully updated
Wine 1.3.4 with winetricks installed
ATi Catalyst proprietary drivers

Even though ATi is pretty tough for gaming, this issue seems to occur far before I even get to launch the game. I'm suspecting that maybe the x64 distribution is causing issues here, but I'm really out of sensible idea's here.

Thanks in advance for your help, I hope I'll be able to erase my dual Windows boot soon!

- M

---

### Post by Tritan on 2010-10-13
Does anyone have suggestions, I'm really out of idea's on this one! :confused:

---

### Post by Tritan on 2010-10-14
Okay, I have narrowed down my problem after solving some issues with the GCC compiler, but I've ran into new issues once I try to run SC2. 

The installation itself goes flawless, but I do have issues once I try to launch the installed version of SC2 (using 'wine Starcraft2.exe'). I do get brief flashes of the SC2 loading screen, but the images are teared up heavily. This stops after approximatively 10 to 15 seconds. 

The following block is the output from Wine I get on my terminal, I'm especially concerned with the fourth entry it shows (OpenGL);

```
root@tritan:~/sc2# wine StarCraft\ II.exe 
fixme:process:GetLogicalProcessorInformation ((nil),0x33c86c): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 2000
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:process:GetLogicalProcessorInformation ((nil),0x117c5c0): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x117c5ac): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation ((nil),0x127e9b8): stub
fixme:win:EnumDisplayDevicesW ((null),0,0xf7c304,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:process:GetLogicalProcessorInformation ((nil),0x127e9b8): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
root@tritan:~/sc2# fixme:process:GetLogicalProcessorInformation (0x33fa5c,0x33fd5c): stub
fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x123590, 0x440f0e8
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x440ed78,0x440ed7c): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:win:EnumDisplayDevicesW ((null),0,0x440ea08,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x440e90c,0x00000000), stub!
fixme:d3d:getColorBits Unsupported format WINED3DFMT_R32_FLOAT.
fixme:d3d:getColorBits Unsupported format WINED3DFMT_R32G32B32A32_FLOAT.
fixme:d3d:getColorBits Unsupported format WINED3DFMT_R32G32B32A32_FLOAT.
fixme:d3d:getColorBits Unsupported format WINED3DFMT_R32G32_FLOAT.
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x4c4c554e (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x4c4c554e) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x4c4c554e (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x4c4c554e) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x440ef00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x440e7e0,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:win:EnumDisplayDevicesW ((null),0,0x440e7b8,0x00000000), stub!
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
fixme:msctf:ThreadMgrSource_AdviseSink (0x75c4090) Unhandled Sink: {71c6e74e-0f28-11d8-a82a-00065b84435c}
fixme:d3d:query_init Event query: Unimplemented, but pretending to be supported.
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
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
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314c41 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314c41) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36315220 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36315220) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x44072a4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x4407578,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x4407568,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x44072fc,0x00000000), stub!
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"mmdevapi.dll"
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
```

Is there anything I can try to fix the OpenGL issue? So far I've tried to install multiple libraries related to OpenGL, and I've tried multiple videodrivers (the builtin ATI one, a beta ATI driver and the MESA one). Searches on Google don't really provide me with an answer either, so I hope you can help! 

By the way, I'm using Wine 1.3.4 with this including wine-tricks and the built-in ATI drivers for the example. 

The full output of my glxinfo can be found [here]("http://pastebin.com/aRc4gf47"). As you can see in the header, direct rendering is supposed to be operational, but it's not.

---

### Post by GmAz on 2010-10-17
I have the same issue.  I get the screens with no text on them, though you can still click where the buttons should be.  But half way though, it errors out.  

I am on 10.10 and have an ATI 4870 video card with ATI's drivers installed.  I have Compiz disabled.  Any help would be great.

---

### Post by TangiX on 2010-10-17
Same issue here, with Ubuntu 10.10, ATI HD 5450 and default fglrx driver.
"nopat" boot option don't change anything

No problem on the same machine with ubuntu 10.04

---

### Post by Halcyon31415 on 2010-10-18
I feel bad not being able to contribute, and ask a new question but hopefully it should be an easy one. 

Is it possible to Play Starcraft 2 on 10.04 using Wine?
I'm not that handy with Ubuntu unfortunately, I got a new computer with Windows 7 on it and to be honest it is ok but it came with a host of HP and Best Buy crap on it that i don't want. I would be happy to just get a Clean OS and play this game. 

So if anyone has a step by step of how to do this i would be very grateful. 
sorry I am not able to help your problem out with 10.10 :(

---

### Post by Halcyon31415 on 2010-10-18
Yikes, Sorry I hate when people do what i just did, i found the link on the FIRST POST on how to Get SC2 to run. Wow I'm sorry for the completely erroneous post.

---

### Post by beastrace91 on 2010-10-19
Crossover Games currently has a 9.2.0 version in open beta that fixes the Starcraft 2 on 10.10 issue. - Give it a try.

~Jeff

---

### Post by Tritan on 2010-10-19
I've reinstalled the standard version of 10.10 x64 yesterday and I've been able to install SC2 with Wine without any issues. 

I've followed [these]("http://jeffhoogland.blogspot.com/2010/07/howto-starcraft-2-on-linux-with-wine.html") steps and included the 'nopat' setting in my grub boot options (you can find instructions for this in the next link). 

I'm using the default fglrx drivers suggested by Ubuntu and I've added the registry options mentioned [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882&iTestingId=56749") to fix my graphics ingame. 

I still need to work out how to boost the FPS, but there seem to be no artifacts and all text is readable. 

So yeah, it actually can be done when using a clean install, I have no explanation why my previous install wouldn't do this, but I'm suspecting that the 'out-of-the-box' ATI support in 10.10 made a difference (there were no tricks involved while I was installing the OS, unlike with previous Ubuntu releases where I had to force vesa drivers i.e.).

---

### Post by mstipanov on 2010-10-20
> **Tritan said:**
> I've reinstalled the standard version of 10.10 x64 yesterday and I've been able to install SC2 with Wine without any issues. 

I've followed [these]("http://jeffhoogland.blogspot.com/2010/07/howto-starcraft-2-on-linux-with-wine.html") steps and included the 'nopat' setting in my grub boot options (you can find instructions for this in the next link). 

I'm using the default fglrx drivers suggested by Ubuntu and I've added the registry options mentioned [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882&iTestingId=56749") to fix my graphics ingame. 

I still need to work out how to boost the FPS, but there seem to be no artifacts and all text is readable. 

So yeah, it actually can be done when using a clean install, I have no explanation why my previous install wouldn't do this, but I'm suspecting that the 'out-of-the-box' ATI support in 10.10 made a difference (there were no tricks involved while I was installing the OS, unlike with previous Ubuntu releases where I had to force vesa drivers i.e.).

I have a 10.10 32 bit version and tried all the mentioned registry options and it doesn't work.

Can anyone help?

Thanks.

---

### Post by beastrace91 on 2010-10-21
> **mstipanov said:**
> I have a 10.10 32 bit version and tried all the mentioned registry options and it doesn't work.

More info please? Wine version(s) tried? Graphics card? Graphics driver version?

Help us, help you,

~Jeff

---


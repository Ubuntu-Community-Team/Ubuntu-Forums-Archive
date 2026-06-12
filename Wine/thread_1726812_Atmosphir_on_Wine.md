---
title: "Atmosphir on Wine"
date: 2011-04-11
forum: Wine
---

### Post by Zbor on 2011-04-11
Hi all,

Ok, I actually read the **Before asking document.
Here is a link to the first Image [http://img140.imageshack.us/i/screenshot1tb.png/](http://img140.imageshack.us/i/screenshot1tb.png/)
My toon is missing his eyes but he has colors. Before I upgraded my video card drivers he was all black and all I could see was his blinking eyes. 
Here is a second link for an item that used to show but now it's black. [http://img848.imageshack.us/i/screenshot2bi.png/](http://img848.imageshack.us/i/screenshot2bi.png/)

I didn't reinstall wine but I did update it. Currently running 1.2.2. I've searched google, wine appdb and ubuntu's forums but haven't found the resolution.

I have tries changing the version of windows to use in the wine config.

Here is the terminal output. 
./Atmosphir.exe -opengl
```
micah@HP-G62-Notebook:~/.wine/drive_c/Program Files/Atmosphir$ ./Atmosphir.exe -opengl
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee14,0x00000000), stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x163160, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x32efdc)
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515406674 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515406674) in the format lookup table
fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x32eba4, cbSize=8) stub!
fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x32ebac, cbSize=8) stub!
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x32ec0c, uiNumDevices=1, cbSize=12) stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1839b8) : pBox=(nil) stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x1eae9f8): stub
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x32f47c, uiNumDevices=1, cbSize=12) stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:winediag:IcmpCreateFile Failed to use ICMP (network ping), this requires special permissions.
fixme:exec:SHELL_execute flags ignored: 0x00004100
fixme:font:RemoveFontMemResourceEx (0x8c5e1289) stub
fixme:font:RemoveFontMemResourceEx (0x8c5c9c31) stub
AL lib: ALc.c:1808: alcCloseDevice(): destroying 1 Context(s)
micah@HP-G62-Notebook:~/.wine/drive_c/Program Files/Atmosphir$ fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33ee14,0x00000000), stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x1324b8, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x33efdc)
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515406674 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515406674) in the format lookup table
fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x33eba4, cbSize=8) stub!
fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x33ebac, cbSize=8) stub!
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x33ec0c, uiNumDevices=1, cbSize=12) stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x183980) : pBox=(nil) stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x216e9f8): stub
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x33f47c, uiNumDevices=1, cbSize=12) stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:winediag:IcmpCreateFile Failed to use ICMP (network ping), this requires special permissions.
err:winediag:IcmpCreateFile Failed to use ICMP (network ping), this requires special permissions.

```./Atmosphir.exe
```
micah@HP-G62-Notebook:~/.wine/drive_c/Program Files/Atmosphir$ ./Atmosphir.exe
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee14,0x00000000), stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x163128, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x32efdc)
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515406674 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515406674) in the format lookup table
fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x32eba4, cbSize=8) stub!
fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x32ebac, cbSize=8) stub!
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x32ec0c, uiNumDevices=1, cbSize=12) stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x183980) : pBox=(nil) stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x1eae9f8): stub
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x32f47c, uiNumDevices=1, cbSize=12) stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:winediag:IcmpCreateFile Failed to use ICMP (network ping), this requires special permissions.
fixme:exec:SHELL_execute flags ignored: 0x00004100
fixme:font:RemoveFontMemResourceEx (0x8c5e1289) stub
fixme:font:RemoveFontMemResourceEx (0x8c5c9c31) stub
AL lib: ALc.c:1808: alcCloseDevice(): destroying 1 Context(s)
micah@HP-G62-Notebook:~/.wine/drive_c/Program Files/Atmosphir$ fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33ee14,0x00000000), stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x1324b8, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x33efdc)
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515406674 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515406674) in the format lookup table
fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x33eba4, cbSize=8) stub!
fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x33ebac, cbSize=8) stub!
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x33ec0c, uiNumDevices=1, cbSize=12) stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x183980) : pBox=(nil) stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x216e9f8): stub
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x33f47c, uiNumDevices=1, cbSize=12) stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
err:winediag:IcmpCreateFile Failed to use ICMP (network ping), this requires special permissions.
err:winediag:IcmpCreateFile Failed to use ICMP (network ping), this requires special permissions.

```I'm currently using Wine 1.2.2 and Ubuntu 10.10 64-bit
```
micah@HP-G62-Notebook:~$ uname -r
2.6.35-28-generic
micah@HP-G62-Notebook:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```On the Graphics tab of my wine config I have A check next to
Allow the window manager to decorate the windows
Allow the window manager to control the windows
Emulate a virtual desktop (I've checked and unchecked this option, no difference)
Currently the desktop size is 1024x768 but I have tried 800x600

Direct3D
-Vertex Shader Support: Hardware (I have changed this to none)
I currently have Allow Pixel Shader checked. (I have unchecked this option)

lspci -vk |grep VGA
```
micah@HP-G62-Notebook:~$ lspci -vk |grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
```glxinfo |grep render
```
micah@HP-G62-Notebook:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile GEM 20100330 DEVELOPMENT 

```I can't find that code in my terminal memory but I have driver version i915.


Any thoughts, ideas, or solutions would be greatly appreciated!


[IMG]http://img140.imageshack.us/i/screenshot1tb.png/[/IMG]

---

### Post by cogadh on 2011-04-11
I think your problem is going to be Unity3D, the game "engine" (for want of a better term) that Atmosphir uses. I don't think it is fully Wine compatible (yet). You might try updating to the more recent 1.3.X Wine version, it may have better support for the engine and game: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Zbor on 2011-04-11
Thanks for your response cogadh!
The good news is the items in the game are back but my character went black again.

See picture [http://img843.imageshack.us/i/screenshot4jf.png/](http://img843.imageshack.us/i/screenshot4jf.png/)
If I move the camera around he'll turn lightish red (inside of grapefruit) or to the color he's supposed to be. I'm hoping I can get this working so I won't have to keep windows around.
I get the same results using ./Atmosphir with or without -opengl

---


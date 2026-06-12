---
title: "WoW video flickers about once a second"
date: 2008-12-26
forum: Wine
---

### Post by doumakes on 2008-12-26
I'm running World of Warcraft Wrath of the Lich King with wine 1.1.10.

For the unable-to-accent-the-EULA problem, I upgraded wine, which worked.

Then WoW would start but everything "behind" the EULA was just flickering colors.  I tried the registry hack, and that worked.

Now I can log in successfully, but there's a flicker about once a second.  A horizontal band of the screen will momentarily show my Ubuntu desktop.  I'd be grateful for a clue!

Terminal output is:
```
      1 fixme:shdocvw:PersistStreamInit_Load (0x135b6b)->(0x32e2d4)
      2 fixme:shdocvw:OleControl_FreezeEvents (0x135b68)->(1)
      3 fixme:shdocvw:OleControl_FreezeEvents (0x135b68)->(0)
      4 fixme:shell:IShellLinkA_fnGetPath (0x1364b0): WIN32_FIND_DATA is not yet filled.
      5 fixme:shell:IShellLinkA_fnGetPath (0x136820): WIN32_FIND_DATA is not yet filled.
      6 fixme:shell:IShellLinkA_fnGetPath (0x136820): WIN32_FIND_DATA is not yet filled.
      7 fixme:shell:IShellLinkA_fnGetPath (0x136490): WIN32_FIND_DATA is not yet filled.
      8 fixme:shell:IShellLinkA_fnGetPath (0x136490): WIN32_FIND_DATA is not yet filled.
      9 fixme:shell:IShellLinkA_fnGetPath (0x136490): WIN32_FIND_DATA is not yet filled.
     10 fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
     11 fixme:iphlpapi:NotifyAddrChange (Handle 0x7d803a08, overlapped 0x7d8039ec): stub
     12 fixme:system:SetProcessDPIAware stub!
     13 fixme:msimtf:ActiveIMMApp_Activate Stub
     14 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10048 24 0 32b654)
     15 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10048 81 0 32b3c8)
     16 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10048 83 0 32b928)
     17 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10048 1 0 32b3c8)
     18 fixme:msimtf:ActiveIMMApp_FilterClientWindows Stub
     19 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 81 0 32bbf0)
     20 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 83 0 32bba0)
     21 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 1 0 32bbf0)
     22 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 5 0 640064)
     23 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 3 0 0)
     24 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 1f 0 0)
     25 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c a 0 0)
     26 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 81 0 32b7b0)
     27 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 83 0 32b760)
     28 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 1 0 32b7b0)
     29 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 5 0 640064)
     30 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 3 0 0)
     31 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 210 1 1004e)
     32 fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x135c04)->((null) 1 0x32bc78 (nil))
     33 fixme:shdocvw:ClOleCommandTarget_Exec (0x135c04)->((null) 25 2 0x32bc8c (nil))
     34 fixme:shdocvw:ClOleCommandTarget_Exec (0x135c04)->((null) 26 2 0x32bc8c (nil))
     35 fixme:shdocvw:ClientSite_GetContainer (0x135c04)->(0x32bcc8)
     36 fixme:shdocvw:ClOleCommandTarget_Exec (0x135c04)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32bd8c (nil))
     37 fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x136490)->(L"" L"" 0 0x32bdc4)
     38 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10048 1c 1 0)
     39 fixme:shdocvw:ClOleCommandTarget_Exec (0x135c04)->((null) 29 2 0x32e9a8 (nil))
     40 fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x135c04)
     41 fixme:shdocvw:ClientSite_GetContainer (0x135c04)->(0x32e7e8)
     42 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 46 0 32d964)
     43 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 83 1 32d880)
     44 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 47 0 32d964)
     45 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 5 0 18e027c)
     46 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 46 0 32d930)
     47 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 83 1 32d84c)
     48 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 46 0 32e5e4)
     49 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 22 0 0)
     50 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 47 0 32e5e4)
     51 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 46 0 32e644)
     52 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 22 0 0)
     53 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 47 0 32e644)
     54 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c a 1 0)
     55 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 7 1003a 0)
     56 fixme:shdocvw:InPlaceFrame_SetStatusText (0x135c04)->(0xf7e8b735)
     57 fixme:shdocvw:ClOleCommandTarget_Exec (0x135c04)->((null) 25 2 0x32e71c (nil))
     58 fixme:shdocvw:ClOleCommandTarget_Exec (0x135c04)->((null) 26 2 0x32e71c (nil))
     59 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 85 1 0)
     60 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 85 1 0)
     61 fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
     62 fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
     63 fixme:shdocvw:ClOleCommandTarget_Exec (0x135c04)->((null) 21 2 (nil) (nil))
     64 fixme:shdocvw:ClOleCommandTarget_Exec (0x135c04)->((null) 28 2 0x32e948 (nil))
     65 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 81 0 32e69c)
     66 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 83 0 32e64c)
     67 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 1 0 32e69c)
     68 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 5 0 18e027c)
     69 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 3 0 0)
     70 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 210 1 10054)
     71 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 81 0 32e7bc)
     72 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 83 0 32e76c)
     73 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 1 0 32e7bc)
     74 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 5 0 0)
     75 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 3 0 0)
     76 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 210 1 10056)
     77 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 46 0 32e7f0)
     78 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 46 0 32e850)
     79 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 22 0 0)
     80 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 47 0 32e850)
     81 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 46 0 32e9a4)
     82 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 83 1 32e8c0)
     83 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 47 0 32e9a4)
     84 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 5 0 18e026c)
     85 fixme:bidi:mirror stub: mirroring of characters not yet implemented
     86 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 80 1 0)
     87 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 80 0 0)
     88 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 210 2 1004e)
     89 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 18 0 0)
     90 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 46 0 32ebd0)
     91 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 47 0 32ebd0)
     92 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 8 1004c 0)
     93 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 7 1004e 0)
     94 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 82 0 0)
     95 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 46 0 32ed14)
     96 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 22 0 0)
     97 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 47 0 32ed14)
     98 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 8 10054 0)
     99 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 7 1004c 0)
    100 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 85 1 0)
    101 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 85 1 0)
    102 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 8 1003a 0)
    103 fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10048 1c 0 0)
    104 fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x135b68)
    105 fixme:msimtf:ActiveIMMApp_Deactivate Stub
    106 fixme:mshtml:HlinkTarget_SetBrowseContext (0x14f430)->((nil))
    107 fixme:shdocvw:OleObject_Close (0x135b68)->(1)
    108 fixme:shell:DllCanUnloadNow stub
    109 fixme:msimtf:DllCanUnloadNow ()
    110 fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
    111 fixme:advapi:SetSecurityInfo stub
    112 fixme:win:EnumDisplayDevicesW ((null),0,0x3aedbc,0x00000000), stub!
    113 fixme:win:EnumDisplayDevicesW ((null),0,0x3aeba8,0x00000000), stub!
    114 fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
    115  @ directx.c / 3810
    116 fixme:win:EnumDisplayDevicesW ((null),0,0x3af2d8,0x00000000), stub!
    117 fixme:win:EnumDisplayDevicesW ((null),0,0x3af434,0x00000000), stub!
    118 fixme:win:EnumDisplayDevicesW ((null),0,0x3af5a0,0x00000000), stub!
    119 fixme:win:EnumDisplayDevicesW ((null),0,0x3af59c,0x00000000), stub!
    120 fixme:win:EnumDisplayDevicesW ((null),0,0x3af530,0x00000000), stub!
    121 fixme:win:EnumDisplayDevicesW ((null),0,0x3af520,0x00000000), stub!
    122 fixme:win:EnumDisplayDevicesW ((null),0,0x3af018,0x00000000), stub!
    123 fixme:win:EnumDisplayDevicesW ((null),0,0x3af150,0x00000000), stub!
    124 fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x140048,0x13ff48): stub
    125 fixme:win:EnumDisplayDevicesW ((null),0,0x3adf1c,0x00000000), stub!
    126 fixme:win:EnumDisplayDevicesW ((null),0,0x3adf44,0x00000000), stub!
    127 fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
    128 fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
    129 fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
    130 fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
    131 fixme:reg:GetNativeSystemInfo (0x374026a4) using GetSystemInfo()
    132 fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
    133 fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
    134 fixme:imm:ImmAssociateContextEx (0x30050, (nil), 16): stub
    135 archive Data\enUS\patch-enUS.MPQ opened^M
    136 archive Data\patch.MPQ opened^M
    137 archive Data\expansion.MPQ opened^M
    138 archive Data\lichking.MPQ opened^M
    139 archive Data\common.MPQ opened^M
    140 archive Data\common-2.MPQ opened^M
    141 archive Data\enUS\locale-enUS.MPQ opened^M
    142 archive Data\enUS\speech-enUS.MPQ opened^M
    143 archive Data\enUS\expansion-locale-enUS.MPQ opened^M
    144 archive Data\enUS\lichking-locale-enUS.MPQ opened^M
    145 archive Data\enUS\expansion-speech-enUS.MPQ opened^M
    146 archive Data\enUS\lichking-speech-enUS.MPQ opened^M
    147 Unable to read extra attributes: "Cache\Survey.mpq"^M

```

```
~$ uname -a
Linux don-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
```

xorg.conf:
```
      1 # xorg.conf (X.Org X Window System server configuration file)
      2 #
      3 # This file was generated by dexconf, the Debian X Configuration tool, using
      4 # values from the debconf database.
      5 #
      6 # Edit this file with caution, and see the xorg.conf manual page.
      7 # (Type "man xorg.conf" at the shell prompt.)
      8 #
      9 # This file is automatically updated on xserver-xorg package upgrades *only*
     10 # if it has not been modified since the last upgrade of the xserver-xorg
     11 # package.
     12 #
     13 # If you have edited this file but would like it to be automatically updated
     14 # again, run the following command:
     15 #   sudo dpkg-reconfigure -phigh xserver-xorg
     16 
     17 Section "InputDevice"
     18     Identifier  "Generic Keyboard"
     19     Driver      "kbd"
     20     Option      "XkbRules"  "xorg"
     21     Option      "XkbModel"  "pc105"
     22     Option      "XkbLayout" "us"
     23 EndSection
     24 
     25 Section "InputDevice"
     26     Identifier  "Configured Mouse"
     27     Driver      "mouse"
     28     Option      "CorePointer"
     29 EndSection
     30 
     31 Section "Device"
     32     Identifier  "Configured Video Device"
     33     Driver      "fglrx"
     34     Option "UseFastTLS" "2"
     35 EndSection
     36 
     37 Section "Monitor"
     38     Identifier  "Configured Monitor"
     39 EndSection
     40 
     41 Section "Screen"
     42     Identifier  "Default Screen"
     43     Monitor     "Configured Monitor"
     44     Device      "Configured Video Device"
     45     Defaultdepth    24
     46 EndSection
     47 
     48 Section "ServerLayout"
     49     Identifier  "Default Layout"
     50   screen "Default Screen"
     51 EndSection
     52 Section "Module"
     53     Load        "glx"
     54 EndSection

```

dmesg | grep ATI produces ```
[   40.276229] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
```"Taints?"  When I look in Synaptic for fglrx I see I've got xorg-driver-fglrx v 1:7.1.0-8-3+2.6.24.14-22.53 and xserver-xorg-video-ati v 1:6.8.0-1 installed.

---


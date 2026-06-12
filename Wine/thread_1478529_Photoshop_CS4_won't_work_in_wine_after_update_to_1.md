---
title: "Photoshop CS4 won't work in wine after update to 10.04..."
date: 2010-05-09
forum: Wine
---

### Post by Laeluu on 2010-05-09
Man, 10.04 just DOES NOT like me so far, hahaha. (: Oh well. Here's the deal:
I got Photoshop CS4 (portable version) working in Wine, but after this latest update it won't seem to run? I tried to run it out of terminal but this message came up:
```
laeluu@laeluu-laptop:~$ wine '/home/laeluu/.gnome2/panel2.d/default/launchers/PhotoshopPortable.exe-1.desktop' 
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfd4
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x1ee05c (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0xa60e8d8, overlapped 0xa60e8e0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x1b0f144 (nil)
wine: configuration in '/home/laeluu/.wine' has been updated.
wine: Bad EXE format for Z:\home\laeluu\.gnome2\panel2.d\default\launchers\PhotoshopPortable.exe-1.desktop
```When I click on my shortcut icon, this appears in a pop-up box:
> The file '/home/laeluu/.wine/dosdevices/c:/Program Files/PhotoshopCS4Portable/PhotoshopPortable.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.EDITEDITEDIT:
Okay, ran the actual file instead of the shortcut (opps)...I have gotten a frightening wall of text, now. This is the part that terminal kept:
```
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf004 0x33d6a4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf034 0x33d6a4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf064 0x33d6a4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf094 0x33d6a4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf0c4 0x33d6a4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf0f4 0x33d6a4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf124 0x33d6a4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf1d4 0x33c95c
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf234 0x33c95c
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf278 0x33c95c
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf2b8 0x33c95c
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf318 0x33c95c
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf358 0x33c95c
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf39c 0x33d6a4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf3dc 0x33d6a4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf41c 0x33d6a4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf4b4 0x33e44c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf4bc 0x33e44c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf4c4 0x33e44c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf4cc 0x33e44c
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf5d0 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf610 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf654 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf694 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf6e8 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf72c 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf76c 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf7b0 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf7f0 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf830 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf874 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf8b4 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf8f8 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf938 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xf978 0x33e7fc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xfa64 0x33ebd4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xfab8 0x33e8dc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xfaf8 0x33e8dc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xfb38 0x33e8dc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xfb78 0x33e8dc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xfbbc 0x33e8dc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xfbfc 0x33e8dc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xfc3c 0x33e8dc
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x1f2c 0x33d2ac
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x1f74 0x33d2ac
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x1fbc 0x33d2ac
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x20e4 0x33d2ac
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x212c 0x33d2ac
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:win:LockWindowUpdate (0x1006a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x2d54 0x33ec54
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x2ff8 0x33e714
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3010 0x33e82c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3020 0x33e7bc
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3030 0x33e72c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3038 0x33e66c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3040 0x33e66c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3048 0x33e66c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3050 0x33e82c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3064 0x33e82c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3074 0x33e7bc
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3084 0x33e72c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x308c 0x33e66c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3094 0x33e66c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x309c 0x33e66c
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x31ac 0x33e3b4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x31b4 0x33e2f4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x31bc 0x33e2f4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x31c4 0x33e2f4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x31dc 0x33e3b4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x31e4 0x33e2f4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x31ec 0x33e2f4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x31f4 0x33e2f4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x320c 0x33e3b4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3214 0x33e2f4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x321c 0x33e2f4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3224 0x33e2f4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3244 0x33e3b4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x324c 0x33e2f4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3254 0x33e2f4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x325c 0x33e2f4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3274 0x33e3b4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x327c 0x33e2f4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3284 0x33e2f4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x328c 0x33e2f4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x341c 0x33e51c
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x3464 0x33e51c
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x34ac 0x33e51c
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:win:LockWindowUpdate (0x1006a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x4388 0x33e86c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x4398 0x33e7fc
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x43a8 0x33e76c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x43b0 0x33e6ac
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x43b8 0x33e6ac
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x43c0 0x33e6ac
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x43cc 0x33e86c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x43dc 0x33e7fc
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x43ec 0x33e76c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x43f4 0x33e6ac
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x43fc 0x33e6ac
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x4404 0x33e6ac
fixme:win:LockWindowUpdate (0x1006a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x456c 0x33e56c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x457c 0x33e4fc
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x458c 0x33e46c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x4594 0x33e3ac
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x459c 0x33e3ac
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x45a4 0x33e3ac
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x45b0 0x33e56c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x45c0 0x33e4fc
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x45d0 0x33e46c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x45d8 0x33e3ac
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x45e0 0x33e3ac
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0x45e8 0x33e3ac
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x4f14 0x5174 0x33ebe4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x4f14 0x51a4 0x33ebe4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x4f14 0x5264 0x33ebe4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x4f14 0x5280 0x33ebe4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x4f14 0x53a8 0x33ebe4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x4f14 0x53d8 0x33ebe4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x6590 0x6758 0x33ebe4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x6590 0x6774 0x33ebe4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x6590 0x6834 0x33ebe4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x6590 0x6850 0x33ebe4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x6d24 0x6ed0 0x33ebe4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x6d24 0x6eec 0x33ebe4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x6d24 0x6fac 0x33ebe4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x6d24 0x6fc8 0x33ebe4
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x6d24 0x7088 0x33ebe4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0x6d24 0x70a4 0x33ebe4
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xb05c 0x33da34
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xaf74 0xb068 0x33da24
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xe97c 0xb080 0x33da34
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf841e24)->0xaf74 0xb08c 0x33da24
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xb438 0x33ed84
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xb414 0xb470 0x33ec9c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xb414 0xb490 0x33ec9c
fixme:win:LockWindowUpdate (0x1006a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xc224 0x33e254
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xc234 0x33e1e4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xc244 0x33e154
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xc24c 0x33e094
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xc254 0x33e094
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xc25c 0x33e094
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xc268 0x33e254
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xc278 0x33e1e4
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xc288 0x33e154
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xc290 0x33e094
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xc298 0x33e094
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xc2a0 0x33e094
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:ole:CoResumeClassObjects stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6d66fc4 0x6d66fd0 0x6d685f8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6d66fc4 0x6d66fd0 0x6d685f8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0xf880f9c 0xf880fa8 0x6d685f8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6d66fc4 0x6d66fd0 0x6d685f8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0xf880f9c 0xf880fa8 0x6d685f8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6d66fc4 0x6d66fd0 0x6d685f8 (nil)
fixme:win:LockWindowUpdate (0x1006a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xf218 0x33dc3c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xf22c 0x33dbcc
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xf23c 0x33db3c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xf244 0x33da7c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xf24c 0x33da7c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xf254 0x33da7c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xf260 0x33dc3c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xf270 0x33dbcc
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xf280 0x33db3c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xf288 0x33da7c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xf290 0x33da7c
fixme:mlang:fnIMLangFontLink2_GetFontCodePages (0xf84561c)->0xfa58 0xf298 0x33da7c
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:imm:ImmReleaseContext (0x1006a, 0x1d0320): stub
```
Also, I can't run it from clicking on the icon...only out of terminal.

---

### Post by cariboo on 2010-05-09
Moved to Wine.

---

### Post by cogadh on 2010-05-09
All that "fixme" stuff is normal and you can (usually) ignore them. Those are just developer notes on what they still need to work on in Wine. As for the execution error you are getting, right click on the Photoshop executable and check the permissions. Make sure that it is set as an executable and you should be able to launch it from the menu like you used to.

---

### Post by moster on 2010-05-10
You got PM, mine version works :)

---

### Post by Laeluu on 2010-05-10
I'm really not sure on how to check the permissions and all that stuff; I'm a newbie to ubuntu/unix/not-windows.

---

### Post by cogadh on 2010-05-10
In the Wine sub-menu of the Applications menu, click on the "Browse C: Drive" shortcut. Find where Photoshop is installed in the Program Files directory, then look for the main executable (I don't have it so I can't provide specifics). Once you have it, simply right-click on it and select Properties. On the Permissions tab there should be a check box to allow the program to be executed.

---


---
title: "Unusual Text issue with Wine 1.1.33"
date: 2009-12-01
forum: Wine
---

### Post by unforeseen123 on 2009-12-01
Hey guys, 

I've attached an image that explains the issue (pictures speak a thousand words and whatnot)

-Wine version 1.1.33 (compiled from source after applying the Steam 'Installation failed (#)' patch)

-The game is still functional (including MP) low FPS because i cant see the graphics options to change them ;)

-I have it running in the wine simulated desktop thing

-Steam is installed and seems to work ok (I can get onto MP games), spotify works fine under wine (using their instructions)

-Added COD4 registry tweaks

-To fix i read somewhere to copy 'd3dx9_34.dll' from a windows installation. made no visible difference.

-Proprietry drivers, installed 'the ubuntu way'

-Ubuntu 9.1, ATI HD 4870 1GB, Intel i7 2.66GHz, 6GB memory

-Console output from as soon as menu becomes responsive:
```
com length=26
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_ERROR_MASK(11): STUB
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=store.steampowered.com length=22
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=cdn.store.steampowered.com length=26
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_ERROR_MASK(11): STUB
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32ceb8,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:file:NtQueryDirectoryFile Unsupported file info class 37
fixme:win:EnumDisplayDevicesW ((null),0,0x33f350,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f714,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
err:d3d:getColorBits Unsupported format: WINED3DFMT_UNKNOWN
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_UNKNOWN
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1e0278) : pBox=(nil) stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x9f072a8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x9f072a8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x9f072a8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x9f072a8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x9f072a8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x9f072a8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x9f072a8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x9f072a8) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x9f072a8) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x33f598,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:file:NtQueryDirectoryFile Unsupported file info class 37
fixme:file:NtQueryDirectoryFile Unsupported file info class 37
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0

```

I'd appriciate any help you could give (I hope I've posted this in the correct place!)

---


---
title: "Battlefield 2 Complete Collection"
date: 2010-01-06
forum: Wine
---

### Post by Final Version on 2010-01-06
I run Battlefield 2 in windowed but after the logo goes away it just flashes black then crashes.

I'm trying to use the install guide from [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438).
[B]
Terminal Output:[/B]
```
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:win:EnumDisplayDevicesW ((null),0,0x33ef40,0x00000000), stub!
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dplayx.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x1707b8,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x33e86c,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x1788f0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788f0, 1, 0x178908)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788f0, 1, 0x178920)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788f0, 1, 0x1790a8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788f0, 1, 0x179498)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788f0, 1, 0x179a80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788f0, 1, 0x179ea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788f0, 1, 0x17a2d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788f0, 1, 0x17a6f8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788f0, 1, 0x17ab20)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788f0, 1, 0x17af78)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788f0, 1, 0x17b348)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x178788)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x178788)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x178788)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x178788, 1, 0x1787a0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"default"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x1788e8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788e8, 1, 0x17c0e0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x17c0f8)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x1788e8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788e8, 1, 0x17c0f8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"default"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     IEnumMoniker_Next(0x1788e8, 1, 0x17c528)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Name:L"DirectSound: default"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer     Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @85! (desktop)
fixme:d3d:debug_d3dformat Unrecognized 1178752590 (as fourcc: NVBF) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1178752590) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1178752590 (as fourcc: NVBF) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1178752590) in the format lookup table
wine: Call from 0x7b845450 to unimplemented function d3dx9_36.dll.D3DXCreateEffectCompiler, aborting
err:seh:raise_exception Unhandled exception code 80000100 flags 1 addr 0x7b845450

```

---

### Post by Final Version on 2010-01-07
Oh and btw, I'm using wine 1.0.1. And trying with just normal battlefield 2, not special forces etc.

---

### Post by alwayshere on 2010-01-07
you will need to delete the intro vids they should be in a file called "movies" 

sudo winfle 

to nav to prog files unless you already have a launcher ??

---

### Post by Final Version on 2010-01-07
Deleted them, same result. After the logo comes up the screen goes black for a second then crashes.

---

### Post by Soulcage on 2010-01-08
Try installing the newest version at the moment its 1.1.35.

---

### Post by Final Version on 2010-01-08
> **Soulcage said:**
> Try installing the newest version at the moment its 1.1.35.
That was the first thing I tried, though I'll give it one more shot.

---

### Post by gyebro on 2010-01-24
You need the native version of d3dx9_36.dll (it is indicated in the console log) and copy into the /windows/system32 directory. You can grab it from [_here_](http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_36).

---


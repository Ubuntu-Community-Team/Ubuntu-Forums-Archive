---
title: "Low fps on mmo 3D ubuntu"
date: 2009-07-31
forum: Wine
---

### Post by nknwn666 on 2009-07-31
im useing ubuntu 8.10, playing a mmorpg named Shaiya, on windows i got 20-40fps in towns and on ubuntu i got 2-7fps in towns, useing wine 1.0.1 beacouse any other new wine version gets my game stuck at login
looked at [winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=10214") and it seems that it should work on wine 1.1.23 but it doesnt work for me and added those extra dll files
wine configuration is the default one
terminal output wine 1.1.26(gets stuck at login):
```
~$ wine /media/sdb1/Shaiya/game.exe
fixme:imm:ImmReleaseContext (0x10030, 0x1466a0): stub
fixme:imm:ImmGetOpenStatus (0x1466a0): semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x3283d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x327db0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x327e40,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x3285d4,0x00000000), stub!
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x215f78,0x215e78): stub
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table

```
terminal output wine 1.1.23(gets stuck at login):
```
~$ wine /media/sdb1/Shaiya/game.exe
fixme:imm:ImmReleaseContext (0x10030, 0x1459a0): stub
fixme:imm:ImmGetOpenStatus (0x1459a0): semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x3283d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x327dd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x327e64,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x3285f8,0x00000000), stub!
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d_surface:surface_load_ds_location (0x170d08) Not supported with fixed up depth stencil
fixme:d3d_surface:surface_load_ds_location (0x170d08) Not supported with fixed up depth stencil
fixme:d3d_surface:surface_load_ds_location (0x170d08) Not supported with fixed up depth stencil
fixme:d3d_surface:surface_load_ds_location (0x170d08) Not supported with fixed up depth stencil
fixme:d3d_surface:surface_load_ds_location (0x170d08) Not supported with fixed up depth stencil
fixme:d3d_surface:surface_load_ds_location (0x170d08) Not supported with fixed up depth stencil
```
terminal output wine 1.0.1(game works but with low fps):
```
:~$ wine /media/sdb1/Shaiya/game.exe
fixme:imm:ImmReleaseContext (0x30026, 0x142fb0): stub
fixme:imm:ImmGetOpenStatus (0x142fb0): semi-stub
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dplayx.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x145f68,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x3288ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3283b0,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x14b7f8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7f8, 1, 0x14b030)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7f8, 1, 0x14b048)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7f8, 1, 0x14b398)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7f8, 1, 0x14ca58)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7f8, 1, 0x14d040)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7f8, 1, 0x14d468)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7f8, 1, 0x14f598)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7f8, 1, 0x14f9c0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7f8, 1, 0x14fde8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7f8, 1, 0x150240)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7f8, 1, 0x150610)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x14b010)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x14b010)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x14b010)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b010, 1, 0x14b800)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x14b7c8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7c8, 1, 0x14b7e0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"C-Media CMI8738"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7c8, 1, 0x1513b0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14b7c8, 1, 0x1517e8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"OPL3 FM synth"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x151c18)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x151c18)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x151c18, 1, 0x152048)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x151c18, 1, 0x152060)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:imm:NotifyIME IMC_SETCONVERSIONMODE
fixme:imm:ImmGetOpenStatus (0x142fb0): semi-stub
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
```
at the wine 1.0.1 terminal output is all the output until after caracter select,after this time, it only spams ```
fixme:d3d:tex_coordindex Unhandled WINED3DTSS_TEXCOORDINDEX 40000
``` in terminal

---

### Post by nknwn666 on 2009-08-01
bump :(

---


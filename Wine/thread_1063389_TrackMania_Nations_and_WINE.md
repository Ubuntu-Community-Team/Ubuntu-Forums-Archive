---
title: "TrackMania Nations and WINE"
date: 2009-02-07
forum: Wine
---

### Post by nkri on 2009-02-07
Hey everyone...
     I tried to install [_TrackMania Nations_]("http://www.trackmania.com/en/index.php?lang=en&rub=nations") under WINE last night, and everything seemed to be going okay until I tried to actually play the game--that is, it installed fine, and brought me to a start up screen where I could choose between "Play," "Configure," "Help," etc.  I could configure it and everything, but when I clicked "Play," a window popped up for a fraction of a second and then disappeared.  Nothing seems to be working, and I'd really like to get this up and running, so does anyone know if it needs dependencies or something?  By the way, I have compiz turned off.
Thanks!
-nkri

---

### Post by Murrquan on 2009-02-07
Try running it from the terminal (type "wine (program's name)" inside that program's directory). The output might help someone technically-inclined to give you a useful answer.

Also -- have you tried running any other programs with 3d graphics? I've had a lot of trouble on computers where Wine didn't understand my graphics card or something like that, which made a lot of neat games unplayable.

---

### Post by nkri on 2009-02-08
Here's the output from Terminal:
```
nkri@nkri-laptop:~/.wine/drive_c/Program Files/TmNationsForever$ wine TmForever.exe
err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileW' used by L"C:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'd3dx9_36.D3DXGetImageInfoFromFileW' used by L"C:\\windows\\system32\\d3dx9_30.dll". If you are using builtin L"d3dx9_30.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'd3dx9_36.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_30.dll". If you are using builtin L"d3dx9_30.dll", try using the native one instead.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f208,0x00000000), stub!
fixme:dinput:IDirectInputDevice2WImpl_EnumEffects (this=0x142730,0x8aa9b0,0x1359700,0x00000003): stub!
fixme:dinput:IDirectInputDevice2WImpl_EnumEffects (this=0x143e38,0x8aa9b0,0x13597c8,0x00000003): stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetSoftwareVertexProcessing (0x147fe8) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 4
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Event query: Unimplemented, but pretending to be supported
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 10
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 11
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 12
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 13
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 14
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 15
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 16
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 17
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 18
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 843666497 (as fourcc: ATI2) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 843666497 (as fourcc: ATI2) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(843666497) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 843666497 (as fourcc: ATI2) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 843666497 (as fourcc: ATI2) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 843666497 (as fourcc: ATI2) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 843666497 (as fourcc: ATI2) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(843666497) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled nkri@nkri-laptop:~/.wine/drive_c/Program Files/TmNationsForever$ wine TmForever.exe
err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileW' used by L"C:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'd3dx9_36.D3DXGetImageInfoFromFileW' used by L"C:\\windows\\system32\\d3dx9_30.dll". If you are using builtin L"d3dx9_30.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'd3dx9_36.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_30.dll". If you are using builtin L"d3dx9_30.dll", try using the native one instead.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f208,0x00000000), stub!
fixme:dinput:IDirectInputDevice2WImpl_EnumEffects (this=0x142730,0x8aa9b0,0x1359700,0x00000003): stub!
fixme:dinput:IDirectInputDevice2WImpl_EnumEffects (this=0x143e38,0x8aa9b0,0x13597c8,0x00000003): stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetSoftwareVertexProcessing (0x147fe8) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 4
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Event query: Unimplemented, but pretending to be supported
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 10
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 11
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 12
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 13
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 14
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 15
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 16
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 17
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x147fe8) Unhandled query type 18
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x162a90) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 843666497 (as fourcc: ATI2) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 843666497 (as fourcc: ATI2) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(843666497) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 843666497 (as fourcc: ATI2) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 843666497 (as fourcc: ATI2) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 843666497 (as fourcc: ATI2) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 843666497 (as fourcc: ATI2) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(843666497) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
wine: Call from 0x7b845450 to unimplemented function d3dx9_36.dll.D3DXAssembleShader, aborting
nkri@nkri-laptop:~/.wine/drive_c/Program Files/TmNationsForever$ format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
wine: Call from 0x7b845450 to unimplemented function d3dx9_36.dll.D3DXAssembleShader, aborting
nkri@nkri-laptop:~/.wine/drive_c/Program Files/TmNationsForever$ 
```

Yes, I have run 3D graphics, but not under WINE...I've only used games native to Linux so far...
-nkri

---

### Post by hikaricore on 2009-02-08
You should check the [WINE Application Database]("http://appdb.winehq.org") there are several TrackMania games listed there and almost none of them work under WINE.

---

### Post by nkri on 2009-02-08
ok, just got it working...it just needed the d3dx9_36 library, and now it runs fine:)
-nkri

---


---
title: "Problem Running NFS MOST WANTED ON WINE (11.04)"
date: 2011-06-19
forum: Wine
---

### Post by linuxyogi on 2011-06-19
Hi,

11.04 (32 Bit)
Wine 1.3.22
Nvidia 9500 GT || Driver ver. 270.41.06

:```
~/Need for Speed Most Wanted$ wine speed.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x32f88c,0x00000000), stub!
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0x9c83e0, 49980, (nil), (nil), (nil), 0, 0x16dc18, 0xa7a2d0, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000018
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000053
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x16de68, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x16de68, parameter 0x16e4c0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x16de68, parameter 0x16e548, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x16de68, parameter 0x16e7c0, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x16de68, parameter 0x16e858, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x16de68, parameter 0x16e8f0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x16de68, parameter 0x16e988, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x16de68, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x16fa40, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x16fa40, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16de48)->(0x16fa40): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x16ffa8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x16ffa8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16de48)->(0x16ffa8): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x170580, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x170580, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16de48)->(0x170580): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x170bb8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x170bb8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16de48)->(0x170bb8): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x1711f0, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x1711f0, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16de48)->(0x1711f0): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x171828, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x171828, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16de48)->(0x171828): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x171e60, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x171e60, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16de48)->(0x171e60): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x172498, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x16de68, object 0x172498, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16de48)->(0x172498): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0x9dbf08, 57784, (nil), (nil), (nil), 0, 0x16dc18, 0xfec458, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000001b
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000061
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1735e8, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1735e8, parameter 0x173cb8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1735e8, parameter 0x173d40, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1735e8, parameter 0x173fb8, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1735e8, parameter 0x174050, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1735e8, parameter 0x1740e8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1735e8, parameter 0x174180, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1735e8, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x175e98, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x175e98, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16dfb0)->(0x175e98): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x1763a8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x1763a8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16dfb0)->(0x1763a8): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x176928, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x176928, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16dfb0)->(0x176928): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x176ea0, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x176ea0, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16dfb0)->(0x176ea0): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x177418, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x177418, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16dfb0)->(0x177418): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x177998, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x177998, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16dfb0)->(0x177998): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x177f18, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x177f18, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16dfb0)->(0x177f18): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x178488, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1735e8, object 0x178488, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x16dfb0)->(0x178488): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0x9ea0c0, 10972, (nil), (nil), (nil), 0, 0x16dc18, 0xfec4d8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000004
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000000d
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1795f8, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1795f8, parameter 0x1797a8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1795f8, parameter 0x179830, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1795f8, parameter 0x179aa8, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1795f8, parameter 0x179b40, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1795f8, parameter 0x179bd8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1795f8, parameter 0x179c70, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1795f8, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1795f8, object 0x17b438, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1795f8, object 0x17b438, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1795d8)->(0x17b438): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0x9ecba0, 55128, (nil), (nil), (nil), 0, 0x16dc18, 0xfec558, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000001a
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000005d
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x17baf0, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x17baf0, parameter 0x17c1b0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x17baf0, parameter 0x17c238, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x17baf0, parameter 0x17c4b0, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x17baf0, parameter 0x17c548, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x17baf0, parameter 0x17c5e0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x17baf0, parameter 0x17c678, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x17baf0, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17df58, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17df58, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x179620)->(0x17df58): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17e460, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17e460, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x179620)->(0x17e460): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17e9d8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17e9d8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x179620)->(0x17e9d8): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17ef50, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17ef50, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x179620)->(0x17ef50): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17f4c8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17f4c8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x179620)->(0x17f4c8): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17fa40, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17fa40, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x179620)->(0x17fa40): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17ffb8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x17ffb8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x179620)->(0x17ffb8): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x1804c0, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17baf0, object 0x1804c0, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x179620)->(0x1804c0): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0x9fa2f8, 49748, (nil), (nil), (nil), 0, 0x16dc18, 0xfec5d8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000018
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000004f
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x17bcd0, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x17bcd0, parameter 0x181800, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x17bcd0, parameter 0x181888, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x17bcd0, parameter 0x181b00, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x17bcd0, parameter 0x181b98, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x17bcd0, parameter 0x181c30, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x17bcd0, parameter 0x181cc8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x17bcd0, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x183600, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x183600, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x17bcb0)->(0x183600): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x183b68, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x183b68, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x17bcb0)->(0x183b68): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x184140, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x184140, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x17bcb0)->(0x184140): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x184718, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x184718, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x17bcb0)->(0x184718): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x184cf0, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x184cf0, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x17bcb0)->(0x184cf0): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x1852c8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x1852c8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x17bcb0)->(0x1852c8): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x1858a0, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x1858a0, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x17bcb0)->(0x1858a0): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x186960, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x17bcd0, object 0x186960, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x17bcb0)->(0x186960): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa06550, 38140, (nil), (nil), (nil), 0, 0x16dc18, 0xfec658, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000015
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000003b
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x187790, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x187790, parameter 0x187dc0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x187790, parameter 0x187e48, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x187790, parameter 0x1880c0, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x187790, parameter 0x188158, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x187790, parameter 0x1881f0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x187790, parameter 0x188288, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x187790, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x187790, object 0x1896d8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x187790, object 0x1896d8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x187770)->(0x1896d8): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x187790, object 0x189c40, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x187790, object 0x189c40, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x187770)->(0x189c40): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x187790, object 0x18a218, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x187790, object 0x18a218, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x187770)->(0x18a218): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x187790, object 0x18a7f0, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x187790, object 0x18a7f0, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x187770)->(0x18a7f0): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x187790, object 0x18adc8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x187790, object 0x18adc8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x187770)->(0x18adc8): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x187790, object 0x18b3a0, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x187790, object 0x18b3a0, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x187770)->(0x18b3a0): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa29f80, 11712, (nil), (nil), (nil), 0, 0x16dc18, 0xfec6d8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000006
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000015
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x18b998, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x18b998, parameter 0x18bf88, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x18b998, parameter 0x18c010, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x18b998, parameter 0x18c288, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x18b998, parameter 0x18c320, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x18b998, parameter 0x18c3b8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x18b998, parameter 0x18c450, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x18b998, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x18b998, object 0x18d3a8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x18b998, object 0x18d3a8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x18b978)->(0x18d3a8): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0x9d4720, 708, (nil), (nil), (nil), 0, 0x16dc18, 0xfec758, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000001
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000000
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x18e1e0, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x18e1e0, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x18e1e0, object 0x18e238, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x18e1e0, object 0x18e238, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x18e0c8)->(0x18e238): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0x9d49e8, 10068, (nil), (nil), (nil), 0, 0x16dc18, 0xfec7d8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000005
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000015
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x18e828, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x18e828, parameter 0x18e9a8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x18e828, parameter 0x18ea18, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x18e828, parameter 0x18ec90, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x18e828, parameter 0x18ed28, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x18e828, parameter 0x18edc0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x18e828, parameter 0x18ee58, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x18e828, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x18e828, object 0x18f550, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x18e828, object 0x18f550, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x18e808)->(0x18f550): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0x9d7140, 10192, (nil), (nil), (nil), 0, 0x16dc18, 0xfec858, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000005
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000016
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1908a8, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1908a8, parameter 0x190a28, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1908a8, parameter 0x190ab0, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1908a8, parameter 0x190d28, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1908a8, parameter 0x190dc0, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1908a8, parameter 0x190e58, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1908a8, parameter 0x190ef0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1908a8, parameter 0x191488, n 15 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1908a8, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1908a8, object 0x1915f8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1908a8, object 0x1915f8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x18e948)->(0x1915f8): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0x9d9910, 9716, (nil), (nil), (nil), 0, 0x16dc18, 0xfec8d8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000006
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000015
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x192a50, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x192a50, parameter 0x192be0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x192a50, parameter 0x192c68, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x192a50, parameter 0x192ee0, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x192a50, parameter 0x192f78, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x192a50, parameter 0x193010, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x192a50, parameter 0x1930a8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x192a50, parameter 0x1935b0, n 15 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x192a50, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x192a50, object 0x1939b8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x192a50, object 0x1939b8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x192a30)->(0x1939b8): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa0fa50, 21096, (nil), (nil), (nil), 0, 0x16dc18, 0xfec958, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000016
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000034
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x195038, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x195038, parameter 0x195250, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x195038, parameter 0x195728, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x195038, parameter 0x195918, n 15 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x195038, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x195038, object 0x1964f8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x195038, object 0x1964f8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x195018)->(0x1964f8): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa14cb8, 5620, (nil), (nil), (nil), 0, 0x16dc18, 0xfec9d8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000007
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000000b
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x198378, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x198378, parameter 0x198558, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x198378, parameter 0x198a48, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x198378, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x198378, object 0x199948, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x198378, object 0x199948, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1951d8)->(0x199948): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa162b0, 15864, (nil), (nil), (nil), 0, 0x16dc18, 0xfeca58, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000012
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000026
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x19a0f0, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x19a0f0, parameter 0x19a1a8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x19a0f0, parameter 0x19a5d8, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x19a0f0, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x19a0f0, object 0x19b0d8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x19a0f0, object 0x19b0d8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x199fd8)->(0x19b0d8): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa1a0a8, 2676, (nil), (nil), (nil), 0, 0x16dc18, 0xfecad8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000005
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000004
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x19cc28, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x19cc28, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x19cc28, object 0x19d500, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x19cc28, object 0x19d500, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x19cb38)->(0x19d500): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa1ab20, 11480, (nil), (nil), (nil), 0, 0x16dc18, 0xfecb58, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000005
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000001a
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x19dca8, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x19dca8, parameter 0x19dd30, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x19dca8, parameter 0x19ddb8, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x19dca8, parameter 0x19e030, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x19dca8, parameter 0x19e0c8, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x19dca8, parameter 0x19e160, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x19dca8, parameter 0x19e1f8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x19dca8, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x19dca8, object 0x19e868, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x19dca8, object 0x19e868, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x19db90)->(0x19e868): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa1d7f8, 7068, (nil), (nil), (nil), 0, 0x16dc18, 0xfecbd8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000000d
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000000a
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1a0040, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a0040, parameter 0x1a0118, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1a0040, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a0040, object 0x1a1588, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a0040, object 0x1a1588, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x19ff58)->(0x1a1588): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa1f398, 8272, (nil), (nil), (nil), 0, 0x16dc18, 0xfecc58, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000005
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000013
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1a2038, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a2038, parameter 0x1a21a0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1a2038, parameter 0x1a2228, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a2038, parameter 0x1a24a0, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a2038, parameter 0x1a2538, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a2038, parameter 0x1a25d0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a2038, parameter 0x1a2668, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1a2038, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a2038, object 0x1a2b88, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a2038, object 0x1a2b88, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1a0090)->(0x1a2b88): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa213e8, 15524, (nil), (nil), (nil), 0, 0x16dc18, 0xfeccd8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000000c
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000023
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1a3bf8, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a3bf8, parameter 0x1a3d88, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1a3bf8, parameter 0x1a3e10, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a3bf8, parameter 0x1a4088, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a3bf8, parameter 0x1a4120, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a3bf8, parameter 0x1a41b8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a3bf8, parameter 0x1a4250, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1a3bf8, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a3bf8, object 0x1a4c08, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a3bf8, object 0x1a4c08, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1a2150)->(0x1a4c08): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a3bf8, object 0x1a5170, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a3bf8, object 0x1a5170, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1a2150)->(0x1a5170): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a3bf8, object 0x1a5748, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a3bf8, object 0x1a5748, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1a2150)->(0x1a5748): stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a3bf8, object 0x1a5d20, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a3bf8, object 0x1a5d20, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1a2150)->(0x1a5d20): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa25090, 14724, (nil), (nil), (nil), 0, 0x16dc18, 0xfedd78, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000000d
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000001d
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1a6820, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a6820, parameter 0x1a6eb0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1a6820, parameter 0x1a6f38, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a6820, parameter 0x1a71b0, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a6820, parameter 0x1a7248, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a6820, parameter 0x1a72e0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a6820, parameter 0x1a7378, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1a6820, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a6820, object 0x1a8db8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a6820, object 0x1a8db8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1a6800)->(0x1a8db8): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa2cd40, 1468, (nil), (nil), (nil), 0, 0x16dc18, 0xfeee18, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000003
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000003
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1a9960, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1a9960, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a9960, object 0x1a9b18, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a9960, object 0x1a9b18, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1a6998)->(0x1a9b18): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa2d300, 7980, (nil), (nil), (nil), 0, 0x16dc18, 0xfefeb8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000002
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000000e
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1a9f98, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a9f98, parameter 0x1aa118, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1a9f98, parameter 0x1aa1a0, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a9f98, parameter 0x1aa418, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a9f98, parameter 0x1aa4b0, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a9f98, parameter 0x1aa548, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1a9f98, parameter 0x1aa5e0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1a9f98, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a9f98, object 0x1ab1e0, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1a9f98, object 0x1ab1e0, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1a9f78)->(0x1ab1e0): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa2f230, 9508, (nil), (nil), (nil), 0, 0x16dc18, 0xff0f58, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000005
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000016
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1abe60, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1abe60, parameter 0x1abfe0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1abe60, parameter 0x1ac050, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1abe60, parameter 0x1ac2c8, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1abe60, parameter 0x1ac360, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1abe60, parameter 0x1ac3f8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1abe60, parameter 0x1ac490, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1abe60, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1abe60, object 0x1acb50, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1abe60, object 0x1acb50, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1abe40)->(0x1acb50): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa31758, 5656, (nil), (nil), (nil), 0, 0x16dc18, 0xff1ff8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000004
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000000e
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1adc88, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1adc88, parameter 0x1ade00, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1adc88, parameter 0x1ade88, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1adc88, parameter 0x1ae100, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1adc88, parameter 0x1ae198, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1adc88, parameter 0x1ae230, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1adc88, parameter 0x1ae2c8, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1adc88, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1adc88, object 0x1ae870, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1adc88, object 0x1ae870, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1abf80)->(0x1ae870): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa32d70, 3528, (nil), (nil), (nil), 0, 0x16dc18, 0xff3098, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000004
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000007
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1aee00, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1aee00, parameter 0x1aef70, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1aee00, parameter 0x1aeff8, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1aee00, parameter 0x1af270, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1aee00, parameter 0x1af308, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1aee00, parameter 0x1af3a0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1aee00, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1aee00, object 0x1af930, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1aee00, object 0x1af930, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1adcb0)->(0x1af930): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa33b38, 3332, (nil), (nil), (nil), 0, 0x16dc18, 0xff4138, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000004
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000007
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1afd38, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1afd38, parameter 0x1aff00, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1afd38, parameter 0x1aff70, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1afd38, parameter 0x1b01e8, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1afd38, parameter 0x1b0280, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1afd38, parameter 0x1b0318, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1afd38, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1afd38, object 0x1b08a8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1afd38, object 0x1b08a8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1aee28)->(0x1b08a8): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa34840, 3344, (nil), (nil), (nil), 0, 0x16dc18, 0xff51d8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000004
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000007
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1b0cb0, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b0cb0, parameter 0x1b0e20, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1b0cb0, parameter 0x1b0ea8, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b0cb0, parameter 0x1b1120, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b0cb0, parameter 0x1b11b8, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b0cb0, parameter 0x1b1250, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1b0cb0, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1b0cb0, object 0x1b17e0, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1b0cb0, object 0x1b17e0, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1afd60)->(0x1b17e0): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa35550, 3332, (nil), (nil), (nil), 0, 0x16dc18, 0xff6278, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000004
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000007
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1b1be8, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b1be8, parameter 0x1b1d58, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1b1be8, parameter 0x1b1de0, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b1be8, parameter 0x1b2058, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b1be8, parameter 0x1b20f0, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b1be8, parameter 0x1b2188, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1b1be8, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1b1be8, object 0x1b2718, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1b1be8, object 0x1b2718, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1b0cd8)->(0x1b2718): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa36258, 3528, (nil), (nil), (nil), 0, 0x16dc18, 0xff7318, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000004
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000007
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1b2b20, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b2b20, parameter 0x1b2c90, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1b2b20, parameter 0x1b2d18, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b2b20, parameter 0x1b2f90, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b2b20, parameter 0x1b3028, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b2b20, parameter 0x1b30c0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1b2b20, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1b2b20, object 0x1b3650, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1b2b20, object 0x1b3650, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1b1c10)->(0x1b3650): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa37020, 1512, (nil), (nil), (nil), 0, 0x16dc18, 0xff83b8, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000003
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000003
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1b3b00, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1b3b00, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1b3b00, object 0x1b3cb8, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1b3b00, object 0x1b3cb8, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1b2b48)->(0x1b3cb8): stub
fixme:d3dx:D3DXCreateEffectEx (0x139c60, 0xa28a18, 5480, (nil), (nil), (nil), 0, 0x16dc18, 0xff9458, 0x32fc34): semi-stub
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x00000002
fixme:d3dx:skip_dword_unknown Skipping 1 unknown DWORDs:
fixme:d3dx:skip_dword_unknown     0x0000000c
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1b40e0, desc 0x32fbec partial stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b40e0, parameter 0x1b4288, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetIntArray iface 0x1b40e0, parameter 0x1b42f8, n 0x93de20, count 5 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b40e0, parameter 0x1b4570, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b40e0, parameter 0x1b4608, n 2 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b40e0, parameter 0x1b46a0, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_SetInt iface 0x1b40e0, parameter 0x1b4738, n 1 stub
fixme:d3dx:ID3DXBaseEffectImpl_GetDesc iface 0x1b40e0, desc 0x32fc68 partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1b40e0, object 0x1b4c20, name "shader" partial stub
fixme:d3dx:ID3DXBaseEffectImpl_GetAnnotationByName iface 0x1b40e0, object 0x1b4c20, name "shadowLevel" partial stub
fixme:d3dx:ID3DXEffectImpl_ValidateTechnique (0x1b40c0)->(0x1b4c20): stub
fixme:d3dx:ID3DXEffectImpl_OnLostDevice (0x16de48)->(): stub
wine: Unhandled page fault on read access to 0x00000002 at address 0x685d51bd (thread 0009), starting debugger...
```The game wont start. This is the first time I am trying to install a game using Wine. Do I need to install something else to make it work ?

---

### Post by bobwyajnr on 2011-06-19
Not getting much from that debugging output - sorry!

I presume you are installing "Need for Speed : Most Wanted" retail DVD v1.3 - right?

Have you checked out the [AppDB page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8714") for the game?

You'll need the MS Visual C++ libraries 2008 (SP1) according to the most recent test result. The **winetrick**s script only does the base VC++ 2008 library install by the looks of it...

None of the testers mention any other .dll overrides recently...

Might be copy protection since the DVD uses Safedisc v4.60.00. Most copy protection mechanisms cause problems for Wine. Might need to use a no CD/DVD patch - I'm not sure on that one...

If I was you (and in the absence of a AppDB maintainer) I would pm some of the other recent testers on AppDB. Since they have got the game running OK they should be able to get you started on the right road! :popcorn:

Bob

---

### Post by linuxyogi on 2011-06-19
> **bobwyajnr said:**
> Not getting much from that debugging output - sorry!

I presume you are installing "Need for Speed : Most Wanted" retail DVD v1.3 - right?

Have you checked out the [AppDB page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8714") for the game?

You'll need the MS Visual C++ libraries 2008 (SP1) according to the most recent test result. The **winetrick**s script only does the base VC++ 2008 library install by the looks of it...

None of the testers mention any other .dll overrides recently...

Might be copy protection since the DVD uses Safedisc v4.60.00. Most copy protection mechanisms cause problems for Wine. Might need to use a no CD/DVD patch - I'm not sure on that one...

If I was you (and in the absence of a AppDB maintainer) I would pm some of the other recent testers on AppDB. Since they have got the game running OK they should be able to get you started on the right road! :popcorn:

Bob

I just installed MS Visual C++ libraries 2008 (SP1) from [[COLOR=Blue]here[/COLOR]  ]("http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=5582")but same thing, it crashes on startup.

At the wine appdb page a user says
> [SIZE=2]
[IMG]http://appdb.winehq.org/images/blank.gif[/IMG] [/SIZE]                [SIZE=1]  **Confirmation of startup crash**
 by  Nicolas Krzywinski on Monday June 21st 2010, 11:48
[/SIZE] [SIZE=1] I can confirm the startup crash with current versions: 
Lucid 10.04 with kernel 2.6.32-23 
Wine 1.1.43 

1. Installation works (from original CD with game version 1.2) [/SIZE] [SIZE=1]
2. Update to v1.3 works 
3. Startup intro and video and welcome blabla works 
4. Creation of game profile at startup works 
5. Crash after loading game profile 

Overriding d3dx9_36 makes no difference - no single output line is altered. [/SIZE] [SIZE=1]
The output tells something with eventlog. 

The exact crash and output is reproducible and immediately after clicking on "proceed" button after game profile load. [/SIZE] [SIZE=2]
[/SIZE]I guess it just doesn't work with the newer kernels anymore or perhaps some specific workaround is needed to make it work.

Since this game is quite old now. Tough to find people interested in solving the issue.

I mean we will hardly find the 11.04 & NFS MW combination, may be most them are playing SHIFT now.

Thanks for trying.

---

### Post by bobwyajnr on 2011-06-19
> **linuxyogi said:**
> I just installed MS Visual C++ libraries 2008 (SP1) from [[COLOR=Blue]here[/COLOR]  ]("http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=5582")but same thing, it crashes on startup.

At the wine appdb page a user says
I guess it just doesn't work with the newer kernels anymore or perhaps some specific workaround is needed to make it work.

Since this game is quite old now. Tough to find people interested in solving the issue.

I mean we will hardly find the 11.04 & NFS MW combination, may be most them are playing SHIFT now.

Thanks for trying.

RE NFS:MW I haven't actually tried anything at all **yet**!! I'll test out my copy on Wine 1.3.22. It's a bit late now - so I'll do it later on... I can't believe it's that hard to get working.

Your main hindrance won't be your kernel or Wine version but may in fact be your alpha-release Window Manager!! :D

Bob



[SIZE="2"]PS Hey, really, don't believe any of those old AppDB reports. Wine 1.1.43 - that's months old and tests with that mean nothing... Wine development aims to pull all things forwards uniformly - rather than take one step forwards and two back...

There are always lots of regressions but a lot of stuff is really moving forwards big-time. Look at the Steam client (that I maintain on AppDB): buy games with SSL (tick), store flash video trailers (tick), and even the in-game chat overlay is partially supported...

Even the Steam client system information menu entry gives native looking entries (e.g. ATI HD4600 series for graphics card, proper CPU info and supported extended instruction sets, etc.) The Steam client used to be decidedly flaky when I initially tried to run it in Wine a couple of years ago...
[/SIZE]

---

### Post by bobwyajnr on 2011-06-21
Hi **linuxyogi**

Need for Speed : Most Wanted (Black Edition) appears to work OK. Dang reminds me why I haven't played it for ages (no support for widescreen resolutions, etc.) :popcorn:

Sadly it appears to need a no-CD/DVD patch (which I expected really). I didn't specify any other .dll overrides (or install any Windows libraries). Not sure how different the non-Black version is ???

Bob

---

### Post by linuxyogi on 2011-06-21
> **bobwyajnr said:**
> Hi **linuxyogi**

Need for Speed : Most Wanted (Black Edition) appears to work OK. Dang reminds me why I haven't played it for ages (no support for widescreen resolutions, etc.) :popcorn:

Sadly it appears to need a no-CD/DVD patch (which I expected really). I didn't specify any other .dll overrides (or install any Windows libraries). Not sure how different the non-Black version is ???

Bob

I have a no cd/dvd patch & I have tested this game on my friend's XP box. It played fine.

This is a 2 CD pack. I afaik this is not the black edition. ](*,)

I guess I will try a new racer.

---

### Post by linuxyogi on 2011-06-22
@ Bob

I replaced the CD/DVD pactch with new one & its working now.  :guitar:

---

### Post by bobwyajnr on 2011-06-22
> **linuxyogi said:**
> @ Bob

I replaced the CD/DVD pactch with new one & its working now.  :guitar:

Sweet! Thought it might be something like that... :popcorn:

Just in case anyone else reads this thread - did you use a .dll override (or two) in the end?

Perhaps you could mark the thread as [SOLVED] as well?

Bob

---

### Post by linuxyogi on 2011-06-22
> **bobwyajnr said:**
> 

Just in case anyone else reads this thread - did you use a .dll override (or two) in the end?



No. Just replacing the patch did it.

---

### Post by linuxyogi on 2011-06-25
Hi, ):P

After setting up NFSMW I didn't really played it coz I was busy setting up some of the other 
games.

Latest: NFSMW starts fine. But at the end of every race it crashes. 

At least I can play it. One race per start =P~ I guess something is going wrong while the game is trying to save the profile.


*I am playing Tom Clancy's Hawx & Easports Cricket 2007 with negligible issues.*

---

### Post by bobwyajnr on 2011-06-26
> **linuxyogi said:**
> Hi, ):P
...
Latest: NFSMW starts fine. But at the end of every race it crashes. 

At least I can play it. One race per start =P~ I guess something is going wrong while the game is trying to save the profile.
...

That is the sort of bug report that helps push Wine forwards... I presume it's not a side-effect of the no-CD/DVD patch though? :popcorn:

Bob

---

### Post by linuxyogi on 2011-06-26
> **bobwyajnr said:**
>  I presume it's not a side-effect of the no-CD/DVD patch though? 


No idea.

[I]
NFS Carbon is having no such issues with its own no CD/DVD patch.[/I]

---


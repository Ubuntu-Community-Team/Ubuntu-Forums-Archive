---
title: "Autodesk Inventor 2008"
date: 2009-02-26
forum: Wine
---

### Post by Odd_sam on 2009-02-26
After I installed Autodesk Inventor 2008 and ran it I came up with the following error:

Microsoft Visual C++ Runtime Library

Runtime Error!
Program: C:\Program Files\Inventor 2008\Bin\Inventor.exe
abnormal program termination

and then it closes out the program. Here is what the terminal puts out.

```
err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileW' used by L"C:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'd3dx9_36.D3DXGetImageInfoFromFileW' used by L"C:\\windows\\system32\\d3dx9_31.dll". If you are using builtin L"d3dx9_31.dll", try using the native one instead.
fixme:storage:StgCreateStorageEx Stub: calling StgCreateDocfile, but ignoring pStgOptions and grfAttrs
fixme:msxml:xmlnode_get_ownerDocument 
fixme:msxml:xmlnode_get_ownerDocument 
fixme:msxml:xmlnode_get_ownerDocument 
fixme:msxml:xmlnode_get_ownerDocument 
fixme:msxml:xmlnode_get_ownerDocument 
fixme:msxml:xmlnode_get_ownerDocument 
fixme:msxml:xmlnode_get_ownerDocument 
fixme:msxml:xmlnode_get_ownerDocument 
fixme:msxml:xmlnode_get_ownerDocument 
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
fixme:heap:HeapSetInformation 0x540000 0 0x33f97c 4
fixme:reg:GetNativeSystemInfo (0x32f140) using GetSystemInfo()
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Inventor 2008\\Compatibility\\Bin\\2dTranslator.Dll" failed with error 0
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Inventor 2008\\Compatibility\\Bin\\2dTranslator.tlb" failed with error 2
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
fixme:heap:HeapSetInformation 0x7c0000 0 0x32ccd8 4

```
My wine installation is default I have not changed anything. If someone could help me find the solution to the problem it would be much appreciated, using a free alternative is not an option. This software is required for school and I'd like to get rid of my XP Partition.
WINE version: 1.0.1

---

### Post by Odd_sam on 2009-02-28
can anyone help me?

---


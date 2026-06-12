---
title: "Patching"
date: 2010-10-25
forum: Wine
---

### Post by shawnic on 2010-10-25
I know this question gets asked all the time but i'm still unclear as to how exactly I get this working.

I got the Wine source from sourceforge. (wine-1.2.1-1mdv2010.1.i586.rpm)
and the patch to apply (FONV.patch)```
diff --git a/dlls/d3d9/directx.c b/dlls/d3d9/directx.c
index 1fcc8c4..93bb381 100644
--- a/dlls/d3d9/directx.c
+++ b/dlls/d3d9/directx.c
@@ -474,9 +474,7 @@ static HRESULT WINAPI DECLSPEC_HOTPATCH IDirect3D9ExImpl_CreateDeviceEx(IDirect3
             iface, adapter, device_type, focus_window, flags,
             parameters, mode, device);
 
-    *device = NULL;
-
-    return D3DERR_DRIVERINTERNALERROR;
+    return IDirect3D9Ex_CreateDevice(iface, adapter, device_type, focus_window, flags, parameters, (void *)device);
 }
 
 static HRESULT WINAPI IDirect3D9ExImpl_GetAdapterLUID(IDirect3D9Ex *iface, UINT adapter, LUID *luid)

```

I go to the terminal and type
```
patch -p1 < FONV.patch
```
but I get this output
```
patching file dlls/d3d9/directx.c
Hunk #1 FAILED at 474.
1 out of 1 hunk FAILED -- saving rejects to file dlls/d3d9/directx.c.rej
```
what am I doing wrong?

---


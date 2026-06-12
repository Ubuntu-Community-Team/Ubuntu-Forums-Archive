---
title: "Morrowind Crash on start?"
date: 2010-11-13
forum: Wine
---

### Post by Kn1v3s37 on 2010-11-13
EDIT: The November 12th Wine update fixed it.

Like the title says, after I launch Morrowind, it begins to load the game files, but then it suddenly crashes. I've tried googling around and checked the AppDB, but I couldn't find anything to help. Here's what the terminal spits out when it crashes. 

```
ryan@ryan-G60VX:~/.wine/drive_c/Program Files/Bethesda Softworks/Morrowind$ wine Morrowind.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32f068,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1f5528,0x1f5498): stub
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,24)-(1024,768)
fixme:d3d8:IDirect3DDevice8Impl_ResourceManagerDiscardBytes Byte count ignored.
fixme:gstreamer:GST_Connect Could not make source filter, are gstreamer-plugins-* installed?

(wine:2434): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(wine:2434): GStreamer-CRITICAL **: gst_pad_unlink: assertion `GST_IS_PAD (srcpad)' failed

(wine:2434): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed
wine: Unhandled page fault on read access to 0x00000001 at address 0x30086b8 (thread 0009), starting debugger...
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 45 requests (45 known processed) with 54 events remaining.

``` 

And yes, gstreamer-plugins-* is installed.

Thanks for any help in advance.
-Ryan


EDIT: Here's some specs. Geforce GTX 260m, 2.1ghz Core 2 Duo. Wine is the newest beta version. I'm using proprietary video card drivers. 64bit Ubuntu.

---

### Post by Kn1v3s37 on 2010-11-14
Bump?

---


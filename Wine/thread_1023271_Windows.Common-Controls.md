---
title: "Windows.Common-Controls?"
date: 2008-12-27
forum: Wine
---

### Post by jdpearson on 2008-12-27
I have some apps written in, essentially, Visual Basic.  I've used winetricks to install the VB runtimes, common controls, etc.  

At this point, my application actually displays (nothing happened before) but it does not calculate properly.  Any ideas?  Here is the output I get when run from Terminal:

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:ole:OleLoadPictureEx (0xa9e55c,774,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f8ec), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x12fc38)->(0x1444e0, 0, (nil)), hacked stub.
fixme:ole:OLEPictureImpl_SaveAsFile (0x12fc38)->(0x14fd48, 0, (nil)), hacked stub.
fixme:ole:OLEPictureImpl_get_hPal unimplemented for type 3. Returning 0 palette.
fixme:ole:OLEPictureImpl_SaveAsFile (0x12fc38)->(0x14ff40, 0, (nil)), hacked stub.
^X^X^Xfixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}

```

---


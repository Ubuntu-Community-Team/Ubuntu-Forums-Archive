---
title: "MS-Word 2003 not printing images"
date: 2011-03-04
forum: Wine
---

### Post by Shdwdrgn on 2011-03-04
Running an x64 install of Lucid, wine 1.3.14-0ubuntu1~lucidppa1.

I cannot seem to get inserted images to print in Word.  For testing, I started a new document, and inserted a .gif and .jpg image.  This printed a blank page.  Next I put a border around each image, and the borders printed (but still no images).

Under Tools/Options/Print, I have verified that 'Drawing objects' and 'Background colors and images' are both checked.  I've tried printing to two different printers, both controlled under cups.  Winecfg is set for WindowsXP.

Any suggestions?

---

### Post by Shdwdrgn on 2011-03-04
Running from the console, I pasted a .jpg image and captured this when I printed the document...
```
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:winspool:SetJobW Ignoring everything other than document title
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:psdrv:PSDRV_ExtEscape QUERYESCSUPPORT(25) - not supported.
fixme:ole:snapshot_QueryGetData (0x19cbeb8, 0x32ecdc {cf c00a ptd (nil) aspect 1 lindex -1 tymed 4})
fixme:ole:snapshot_QueryGetData (0x19cbeb8, 0x32ea9c {cf c05d ptd (nil) aspect 1 lindex -1 tymed 1})
fixme:msi:MsiUseFeatureExW mark product L"{90110409-6000-11D3-8CFE-0150048383C9}" feature L"CAGFiles" as used
fixme:wincodecs:JpegDecoder_Frame_GetResolution (0x19dc834,0x8fb75c,0x8fb754): stub

```

---


---
title: "PSXfin/pSX emulator window resizing issues"
date: 2010-07-23
forum: Wine
---

### Post by turgidtoupee on 2010-07-23
I'm using PSXfin 1.13 via wine, and every time I resize the window or fullscreen it the video stops and the audio continues. Everything else works as long as I don't resize anything.

I'd use the linux version but the site seems to have been replaced by "It works!" which means I can't get to the download.

Using wine 1.2 on nvidia 8800gt with the 180(I think) driver.

Terminal gave:```
fixme:win:EnumDisplayDevicesW ((null),0,0x32f6ec,0x00000000), stub!
fixme:d3d:swapchain_init The application requested more than one back buffer, this is not properly supported.
Please configure the application to use double buffering (1 back buffer) if possible.
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
```

As it said in the apphq, I installed directx 9 using winetricks. This didn't help either.

---

### Post by cogadh on 2010-07-23
Is there a reason you have to use PSXFin? There are other emulators available like ePSXe and PCSX that also have Linux native versions.

---


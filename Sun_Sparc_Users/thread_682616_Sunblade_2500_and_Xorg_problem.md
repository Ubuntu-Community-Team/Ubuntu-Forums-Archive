---
title: "Sunblade 2500 and Xorg problem"
date: 2008-01-30
forum: Sun Sparc Users
---

### Post by Gmarco on 2008-01-30
Hi to all,
I installed the last version of ubuntu server sun on a sunblade 2500.
I have some problem with the xorg video driver.
lspci output is:
0003:00:02.0 Display controller: 3DLabs Sun XVR-500 Graphics Accelerator (rev 01)

xorg.conf section device:
Section "Device"
        Identifier      "Scheda video generica"
        Driver          "glint"
        BusID           "PCI:3:0:2"
        Option          "UseFBDev"              "true"
        Option          "ReferenceClock"        "29.500MHz"
EndSection

I tried glint, sunffeb, vesa and vga ... no one worked

Anyone have any ideas?

Tnx

ps is it possible to use a standard pci video card (for example an old s3) if the XVR-500 wasn't support ?

---

### Post by inubasket on 2008-02-03
For starters, yes it is possible. No worries there.

Secondly, vga and vesa both DO work, you just need to have them installed and running properly, which can be tricky if you have a slow CPU drive or an older version of vga/vesa.

---

### Post by Gmarco on 2008-02-03
thank you very much for the reply.
I tried to use the pci S3 video card:
1) if there is ONLY the S3 the sunblade doesn't boot :(
2) using both the video cards the sun boots, but the monitor connected to the s3 remains black.

Can you help me please?

---


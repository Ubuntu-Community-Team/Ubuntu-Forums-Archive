---
title: "Torchlight help :("
date: 2009-11-01
forum: Wine
---

### Post by feedmeh8 on 2009-11-01
Been playing torchlight in wine for 3 days now working perfectly. Played a little this morning, moved the laptop downstairs and started it back up ... to find that the screen is all glichy.. cant make out anything at all. No idea why this happened, as i changed nothing. 

Using ubuntu 9.10 with the latest wine with all the necessary winetricks installed. there was a power outage earlier but i played after fine. Its not till i shutdown, restarted and opened it up again that the glich was there. Any help appreciated.

ty

screen shot of glichy screen:
[IMG]http://img11.imageshack.us/img11/3157/screenshotru.png[/IMG]

---

### Post by beastrace91 on 2009-11-01
Can I inquire as to how you have torchlight installed? I can't even it to load via Wine with Steam :/

~Jeff

---

### Post by feedmeh8 on 2009-11-01
did not use steam i dont think... just copied the program file from a friends windows insall and pasted it in wine c drive..was working flawlessly up to this morning. Im at a total loss. 

EDIT: just got it opening in opengl for the first time instead of crashing ... but getting the same horrible screen glitches as i did with direct3d. If anyone has any suggestions i would appreciate it :D 
ty

---

### Post by myromance123 on 2009-11-02
What graphics card are you using?

 What drivers might you be using?

These matter when it comes to Wine games as they really need a solid good driver to work.

It sounds like the power outage might have damaged something (software wise).

If anything maybe just a complete reinstall of your graphics driver might solve it.
 Anymore little information you might think would contribute to the problem?

---

### Post by feedmeh8 on 2009-11-02
thanks for helping :)

have reinstalled wine and all the winetricks, tried it in both opengl and direct3d .. same horrible result!

lspci results:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
```

I have no idea where i would find drivers for my t61 ubuntu9.10. 

When i go to System-Administration-Hardware Drivers it says "no proprietary drivers are in use on this system". After the power went i could play .. then pluged out laptop, and moved it. Turned it back on, and tried to play again and the screen was a mess :/ ... i have a post in i think every thread in existence to do with wine and torchlight lol. trying to figure this out.

---

### Post by feedmeh8 on 2009-11-02
/thread

fixed problem thanks to post on [http://forums.runicgames.com/viewtopic.php?f=5&t=1272&p=38937#p38937](http://forums.runicgames.com/viewtopic.php?f=5&t=1272&p=38937#p38937)

disabled vertex shader in winecfg. Game is running fine now. thanks to all that helped :D i am a happy destroyer now

---

### Post by myromance123 on 2009-11-04
Glad you fixed it and thanks for posting how you fixed it!

 Happy gaming :D

---

### Post by Cclips on 2009-11-07
Maybe you guys can help me out, I've tried the vertex shaders trick with no luck, also installed all types of winetricks plug-ins with no result. The game loads and plays, but the display stays a very light blue (see screenshot). Any ideas?


LSPCI output
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

---

### Post by Cclips on 2009-11-07
Here is what Wine spits out at me in the terminal, and a inplay screenshot.

```
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized

```

---

### Post by Gaberman on 2009-11-07
I have almost the same problem as Cclips: I also have those two errors repeating in the terminal as the game runs, but in my case, not everything is blue, but the images blur endlessly... Well, see the pictures if you can't imagine it :P

The two errors are:

fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!

and

fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!

The first picture is right when the game strarts. The second is after loading the character. The third is when I try to move (the sky blurs into the other shapes).

---

### Post by Cclips on 2009-11-08
Well I got it to work, I ended up uninstalling and upgrading Wine to the newest version, why it wasn't already I don't know. But that got it working. Had to disable vertex shaders and the other options in wineCFG. It runs, and has a decent framerate but is still a bit sluggish. 

Update: I did manage to get it working in fullscreen, however I'm on a laptop with a resolution of 1400x900. In game, it looked fine, but the resolution was listed as 800x600. So when I tried to change it, it crashed. I'm now going back and figuring out what all works to make it fullscreen.

On how to get it, for one I disabled compiz with:

```
metacity --replace
```

Then loaded it up

I tried it doing this, run Torchlight.exe in safe mode, and check the options fullscreen and netbook mode. That has gotten it to fullscreen for me.

While It does work sporadically, it isn't a consistent method. I'm still working out a method to get it stable...=\

---

### Post by lux_coepi on 2009-11-26
I had originally had much of the same lag and various problems as other users, but after completely wiping my .wine directory and removing and reinstalling the wine and winetricks debs, I managed to get TL running on my box. 
 
I used winetricks to grab Directx9 and vc2008, and the game runs wonderfully, probably better than my brothers newer laptop using Vista. 
 
Even with all graphics options on maximum (except AA and HW skinning which I leave off) I'm still running 40fps average *woot* 
 
Now however, the game will randomly freeze, and I get a
--- "Torchlight.exe is borked and needs to close" ---
pop-up in WineGui. It does not matter whether I use fullscreen or not. I am currently running it in windowed no decoration desktop emulation mode at 1280x800. I am using direct3d, as in OpenGL the game freezes immediately at main menu. 
 
 
My box 
________________________ 
 
I am using Ubuntu 9.04.

some of my sources are 8.10 sources (xserver, jockey,canberra,libdrm2...) so I can use proprietary drivers for my legacy radeon x700, as the new fglrx drivers do not support it, but the new version of xserver does not support the old (working) driver from 8.10. 

The open source drivers refuse to work at all, so I have no option but to use these unless a work-around is found for 9.10. 
 
Turion x64 (original single-core) 2.4 
Ati Radeon mobility x700 with proprietary drivers. 
Wine  1.1.33 
2 gigs DDR crucial (No problems with them) 
Audigy 2 ZS Notebook PCMCIA with ALSA drivers (sound works fine in wine) 
 
All of Wine's dependent packages I reinstalled (mesa, gcc, libc, xlib, etc.), and Wine directory is clean.  TL is bought and downloaded from GamersGate. 



Here is a link to the terminal dump:
[http://paste.ubuntu.com/328979/](http://paste.ubuntu.com/328979/)

I can run wine debug mode, and dump that as a file if needed.

Any suggestions would be appreciated.

---

### Post by AllRadioisDead on 2010-04-13
Eugh, I'd love to play this game but It's still sluggish on my netbook. It's almost there, I'd estimate I'm getting around 10-15 fps with the usual registry tweaks and shaders disabled, and running it in netbook mode. Is there anything else I can do? I have my 256mb of shared ram specified in the wine registry, if I upgrade to 2gb of ram, is there a chance my framerates will increase? I only really need a 5-10 fps boost to get the game playable...

---

### Post by greylion on 2010-07-03
> **ihermit said:**
> Is there anything else I can do? I have my 256mb of shared ram specified in the wine registry, if I upgrade to 2gb of ram, is there a chance my framerates will increase? I only really need a 5-10 fps boost to get the game playable...
(I know, maybe a bit late to reply).

A RAM-upgrade probably won't make any difference.
Try a kernel with preempt.

---


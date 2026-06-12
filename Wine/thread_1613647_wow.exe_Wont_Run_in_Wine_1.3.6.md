---
title: "wow.exe Wont Run in Wine 1.3.6"
date: 2010-11-04
forum: Wine
---

### Post by the rent is too damn high on 2010-11-04
Many months ago, my machine ran WoW 3.x  flawlessly. Now however, with Linux, it wont run at all. I am using Wine  1.3.6 and WoW 4.0.1 installed fine with the downloader, and the  launcher runs without a hitch (although the "play" button won't appear  once in a while). But once the Launcher program attempts to run the  wow.exe, I get nothing. No game, no error message. 
 
Here's my Config.wtf file by the way: 
 
SET locale "enUS" 
SET patchlist "enUS.patch.battle.net:1119/patch" 
SET hwDetect "0" 
SET gxApi "OpenGL" 
SET gxRefresh "60" 
SET gxMultisampleQuality "0.000000" 
SET gxFixLag "0" 
SET gxApi "opengl" 
SET ffxDeath "0" 
SET ffxGlow "0" 
SET gxWindow "1" 
 
 
And when I attempt to run wow.exe through the terminal with *~$ wine "c:/program files/world of warcraft/wow.exe"* here's what it spits back at me: 
 
       
```
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting 
err:module:LdrInitializeThunk Main exe initialization for L"C:\\program  files\\world of warcraft\\wow.exe" failed, status c0000005
```Thinking this message might have meant a corrupted .dll, I went ahead  and downloaded a new opengl32.dll and threw it in the WoW directory, but  no change; opengl32.dll is already in System32 as well!  I'm still thinking this error is somehow graphics-related.
 
And here's some more specs if they help any: 
 
Dell Latitude D610 
Ubuntu 10.10 
 
       
```
lspci -v : 
 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
Subsystem: Dell Dell Latidude C610 
Flags: bus master, fast devsel, latency 0 
Capabilities: <access denied> 
Kernel modules: intel-agp 
 
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode]) 
Flags: bus master, fast devsel, latency 0 
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
I/O behind bridge: 0000d000-0000dfff 
Memory behind bridge: dfd00000-dfefffff 
Prefetchable memory behind bridge: d0000000-d7ffffff 
Capabilities: <access denied> 
Kernel driver in use: pcieport 
Kernel modules: shpchp 
 
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode]) 
Flags: bus master, fast devsel, latency 0 
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0 
I/O behind bridge: 00002000-00002fff 
Memory behind bridge: dfc00000-dfcfffff 
Prefetchable memory behind bridge: 0000000084000000-00000000841fffff 
Capabilities: <access denied> 
Kernel driver in use: pcieport 
Kernel modules: shpchp 
 
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI]) 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 0, IRQ 16 
I/O ports at bf80 [size=32] 
Kernel driver in use: uhci_hcd 
 
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI]) 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 0, IRQ 17 
I/O ports at bf60 [size=32] 
Kernel driver in use: uhci_hcd 
 
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI]) 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 0, IRQ 18 
I/O ports at bf40 [size=32] 
Kernel driver in use: uhci_hcd 
 
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI]) 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 0, IRQ 19 
I/O ports at bf20 [size=32] 
Kernel driver in use: uhci_hcd 
 
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI]) 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 0, IRQ 16 
Memory at ffa80800 (32-bit, non-prefetchable) [size=1K] 
Capabilities: <access denied> 
Kernel driver in use: ehci_hcd 
 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode]) 
Flags: bus master, fast devsel, latency 0 
Bus: primary=00, secondary=03, subordinate=07, sec-latency=32 
I/O behind bridge: 00003000-00003fff 
Memory behind bridge: dfb00000-dfbfffff 
Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff 
Capabilities: <access denied> 
 
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03) 
Subsystem: Dell Latitude D610 Laptop 
Flags: bus master, medium devsel, latency 0, IRQ 16 
I/O ports at ed00 [size=256] 
I/O ports at ec40 [size=64] 
Memory at dffffe00 (32-bit, non-prefetchable) [size=512] 
Memory at dffffd00 (32-bit, non-prefetchable) [size=256] 
Capabilities: <access denied> 
Kernel driver in use: Intel ICH 
Kernel modules: snd-intel8x0 
 
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic]) 
Subsystem: Conexant Systems, Inc. Device 5423 
Flags: medium devsel, IRQ 17 
I/O ports at ee00 [size=256] 
I/O ports at ec80 [size=128] 
Capabilities: <access denied> 
Kernel modules: snd-intel8x0m 
 
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03) 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 0 
Kernel modules: iTCO_wdt, intel-rng 
 
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master]) 
Subsystem: Dell Device 0182 
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17 
I/O ports at 01f0 [size=8] 
I/O ports at 03f4 [size=1] 
I/O ports at 0170 [size=8] 
I/O ports at 0374 [size=1] 
I/O ports at bfa0 [size=16] 
Capabilities: <access denied> 
Kernel driver in use: ata_piix 
Kernel modules: ahci 
 
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300] (prog-if 00 [VGA controller]) 
Subsystem: Dell Device 2006 
Flags: bus master, fast devsel, latency 0, IRQ 42 
Memory at d0000000 (32-bit, prefetchable) [size=128M] 
I/O ports at de00 [size=256] 
Memory at dfdf0000 (32-bit, non-prefetchable) [size=64K] 
[virtual] Expansion ROM at dfd00000 [disabled] [size=128K] 
Capabilities: <access denied> 
Kernel driver in use: radeon 
Kernel modules: radeon, radeonfb 
 
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01) 
Subsystem: Dell Latitude D610 
Flags: bus master, fast devsel, latency 0, IRQ 16 
Memory at dfcf0000 (64-bit, non-prefetchable) [size=64K] 
Expansion ROM at <ignored> [disabled] 
Capabilities: <access denied> 
Kernel driver in use: tg3 
Kernel modules: tg3 
 
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 168, IRQ 19 
Memory at dfb00000 (32-bit, non-prefetchable) [size=4K] 
Bus: primary=03, secondary=04, subordinate=07, sec-latency=176 
Memory window 0: 80000000-83fff000 (prefetchable) 
Memory window 1: 88000000-8bfff000 
I/O window 0: 00003000-000030ff 
I/O window 1: 00003400-000034ff 
16-bit legacy interface ports at 0001 
Kernel driver in use: yenta_cardbus 
Kernel modules: yenta_socket 
 
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller 
Subsystem: Dell Device 0182 
Flags: medium devsel, IRQ 5 
Memory at dfbfd000 (32-bit, non-prefetchable) [size=4K] 
Memory at dfbfe000 (32-bit, non-prefetchable) [size=4K] 
Capabilities: <access denied> 
 
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05) 
Subsystem: Intel Corporation Device 1020 
Flags: bus master, medium devsel, latency 64, IRQ 17 
Memory at dfbff000 (32-bit, non-prefetchable) [size=4K] 
Capabilities: <access denied> 
Kernel driver in use: ipw2200 
Kernel modules: ipw2200 
     
```What am I doing wrong here?

---

### Post by marl30 on 2010-11-04
You're using the development (beta) version of Wine. Often the case these version will cause previous programs that once worked under wine to stop working. I've tried it out and had to go back to the sable version of 1.2.1, which runs my programs ok.

---

### Post by the rent is too damn high on 2010-11-04
I tried it already in 1.2.1, and vitamin from the WineHQ forums told me to upgrade because Ubuntu 10.10 has a patched kernel that breaks Wine.  Why the error message about trying to get opengl32.dll?  The issue apparently is not related to which version of Wine I'm using, otherwise I should see some change.  The error stays identical.

---

### Post by the rent is too damn high on 2010-11-05
Bump.

---

### Post by lkjoel on 2010-11-05
> **the rent is too damn high said:**
> Bump.
Have you tried PlayOnLinux?
```
sudo wget http://deb.playonlinux.com/playonlinux_UBUNTUCODENAME.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux
```
Where UBUNTUCODENAME can be hardy-karmic.
If you have lucid or later, use karmic.

---

### Post by cwwilson721 on 2010-11-05
No reason to get POL if he doesn't need it. POL adds no functionality to the wine binaries, just a pretty interface.

A question that has not been asked:

Have you installed the ATi drivers from Additional Hardware?
If so, try to uninstall (deactivate) them, then reboot, and reactivate.

The issue you are having is with drivers, not wine. (opengl is what wine uses to run WoW. If, for whatever reason, it got borked, a deactivate/reactivate will usually set matters straight.)

Of course, I have NO clue if the current ATi drivers support your videochip (Ati likes to 'legacy' stuff too quick. One of the reasons I don't run ATi on my machines)

---

### Post by lkjoel on 2010-11-05
> **cwwilson721 said:**
> No reason to get POL if he doesn't need it. POL adds no functionality to the wine binaries, just a pretty interface.

A question that has not been asked:

Have you installed the ATi drivers from Additional Hardware?
If so, try to uninstall (deactivate) them, then reboot, and reactivate.

The issue you are having is with drivers, not wine. (opengl is what wine uses to run WoW. If, for whatever reason, it got borked, a deactivate/reactivate will usually set matters straight.)

Of course, I have NO clue if the current ATi drivers support your videochip (Ati likes to 'legacy' stuff too quick. One of the reasons I don't run ATi on my machines)
It actually does help a lot.
It creates a Prefix, you can simulate a reboot, and there are many scripts.
WoW works perfectly with PlayOnLinux.

---

### Post by the rent is too damn high on 2010-11-05
I went ahead and installed POL, and if anything, it's a wonderful diagnostics tool.  Upon starting up it gave me the message:

"You don't seem to have 3D acceleration !  We advise you install and enable it."

I'm convinced this is in fact a driver issue.  I'm removing my fglrx stuff now, and I'm going to re-install it after a reboot.  Let's see how this goes.

---

### Post by cwwilson721 on 2010-11-05
> **lkjoel said:**
> It actually does help a lot.
It creates a Prefix, you can simulate a reboot, and there are many scripts.
WoW works perfectly with PlayOnLinux.As I said, it doesn't improve on the WINE BINARIES.

It's just a shell and scripts.

All it does, I already do, just not automated and pretty.

And DON'T get me started on Cedega....lol

---

### Post by the rent is too damn high on 2010-11-06
I tried reinstalling the ATI drivers, but nothing is showing up under System>Administration>Additional Drivers.  And the error is staying the same when I try to run wow.exe.  :confused:

---

### Post by khelben1979 on 2010-12-10
Wine 1.3.6 works with World of Warcraft. I've tried it myself not long ago. 

Technical specifications which was used: nVidia Geforce 470 GTX with 1280 MB of graphics memory and the processor an Intel Quad at 2.4 ghz + 4 GB RAM. OS: Debian Squeeze "testing". Ubuntu is based on Debian so it would not change too much from your system.

I would recommend that you dig into how to compile it from source code and follow all the instructions. It's not difficult. There are many packages which needs to get installed in the system (if they are not there) to be able to compile up Wine.

---

### Post by Tweak42 on 2010-12-10
> **the rent is too damn high said:**
> I tried reinstalling the ATI drivers, but nothing is showing up under System>Administration>Additional Drivers.  And the error is staying the same when I try to run wow.exe.  :confused:   


It sounds like your problem is still the opengl 3D system.  A simple test I use to verify that opengl is installed and working, is to launch glxgears from a command terminal.  If it's not installed, search "mesa-utils" in the software center.

I once had a simular opengl error after a kernel upgrade, it turned out to be a file permissions problem.  However I only have experience with nvidia chips.  You may want to ask for help in the Hardware & Laptops or Multimedia & Video forums.

---

### Post by vanquishedangel on 2011-02-20
> **the rent is too damn high said:**
> Many months ago, my machine ran WoW 3.x  flawlessly. Now however, with Linux, it wont run at all. I am using Wine  1.3.6 and WoW 4.0.1 installed fine with the downloader, and the  launcher runs without a hitch (although the "play" button won't appear  once in a while). But once the Launcher program attempts to run the  wow.exe, I get nothing. No game, no error message. 
 
Here's my Config.wtf file by the way: 
 
SET locale "enUS" 
SET patchlist "enUS.patch.battle.net:1119/patch" 
SET hwDetect "0" 
SET gxApi "OpenGL" 
SET gxRefresh "60" 
SET gxMultisampleQuality "0.000000" 
SET gxFixLag "0" 
SET gxApi "opengl" 
SET ffxDeath "0" 
SET ffxGlow "0" 
SET gxWindow "1" 
 
 
And when I attempt to run wow.exe through the terminal with *~$ wine "c:/program files/world of warcraft/wow.exe"* here's what it spits back at me: 
 
       
```
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting 
err:module:LdrInitializeThunk Main exe initialization for L"C:\\program  files\\world of warcraft\\wow.exe" failed, status c0000005
```Thinking this message might have meant a corrupted .dll, I went ahead  and downloaded a new opengl32.dll and threw it in the WoW directory, but  no change; opengl32.dll is already in System32 as well!  I'm still thinking this error is somehow graphics-related.
 
And here's some more specs if they help any: 
 
Dell Latitude D610 
Ubuntu 10.10 
 
       
```
lspci -v : 
 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
Subsystem: Dell Dell Latidude C610 
Flags: bus master, fast devsel, latency 0 
Capabilities: <access denied> 
Kernel modules: intel-agp 
 
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode]) 
Flags: bus master, fast devsel, latency 0 
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
I/O behind bridge: 0000d000-0000dfff 
Memory behind bridge: dfd00000-dfefffff 
Prefetchable memory behind bridge: d0000000-d7ffffff 
Capabilities: <access denied> 
Kernel driver in use: pcieport 
Kernel modules: shpchp 
 
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode]) 
Flags: bus master, fast devsel, latency 0 
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0 
I/O behind bridge: 00002000-00002fff 
Memory behind bridge: dfc00000-dfcfffff 
Prefetchable memory behind bridge: 0000000084000000-00000000841fffff 
Capabilities: <access denied> 
Kernel driver in use: pcieport 
Kernel modules: shpchp 
 
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI]) 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 0, IRQ 16 
I/O ports at bf80 [size=32] 
Kernel driver in use: uhci_hcd 
 
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI]) 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 0, IRQ 17 
I/O ports at bf60 [size=32] 
Kernel driver in use: uhci_hcd 
 
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI]) 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 0, IRQ 18 
I/O ports at bf40 [size=32] 
Kernel driver in use: uhci_hcd 
 
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI]) 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 0, IRQ 19 
I/O ports at bf20 [size=32] 
Kernel driver in use: uhci_hcd 
 
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI]) 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 0, IRQ 16 
Memory at ffa80800 (32-bit, non-prefetchable) [size=1K] 
Capabilities: <access denied> 
Kernel driver in use: ehci_hcd 
 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode]) 
Flags: bus master, fast devsel, latency 0 
Bus: primary=00, secondary=03, subordinate=07, sec-latency=32 
I/O behind bridge: 00003000-00003fff 
Memory behind bridge: dfb00000-dfbfffff 
Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff 
Capabilities: <access denied> 
 
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03) 
Subsystem: Dell Latitude D610 Laptop 
Flags: bus master, medium devsel, latency 0, IRQ 16 
I/O ports at ed00 [size=256] 
I/O ports at ec40 [size=64] 
Memory at dffffe00 (32-bit, non-prefetchable) [size=512] 
Memory at dffffd00 (32-bit, non-prefetchable) [size=256] 
Capabilities: <access denied> 
Kernel driver in use: Intel ICH 
Kernel modules: snd-intel8x0 
 
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic]) 
Subsystem: Conexant Systems, Inc. Device 5423 
Flags: medium devsel, IRQ 17 
I/O ports at ee00 [size=256] 
I/O ports at ec80 [size=128] 
Capabilities: <access denied> 
Kernel modules: snd-intel8x0m 
 
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03) 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 0 
Kernel modules: iTCO_wdt, intel-rng 
 
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master]) 
Subsystem: Dell Device 0182 
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17 
I/O ports at 01f0 [size=8] 
I/O ports at 03f4 [size=1] 
I/O ports at 0170 [size=8] 
I/O ports at 0374 [size=1] 
I/O ports at bfa0 [size=16] 
Capabilities: <access denied> 
Kernel driver in use: ata_piix 
Kernel modules: ahci 
 
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300] (prog-if 00 [VGA controller]) 
Subsystem: Dell Device 2006 
Flags: bus master, fast devsel, latency 0, IRQ 42 
Memory at d0000000 (32-bit, prefetchable) [size=128M] 
I/O ports at de00 [size=256] 
Memory at dfdf0000 (32-bit, non-prefetchable) [size=64K] 
[virtual] Expansion ROM at dfd00000 [disabled] [size=128K] 
Capabilities: <access denied> 
Kernel driver in use: radeon 
Kernel modules: radeon, radeonfb 
 
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01) 
Subsystem: Dell Latitude D610 
Flags: bus master, fast devsel, latency 0, IRQ 16 
Memory at dfcf0000 (64-bit, non-prefetchable) [size=64K] 
Expansion ROM at <ignored> [disabled] 
Capabilities: <access denied> 
Kernel driver in use: tg3 
Kernel modules: tg3 
 
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller 
Subsystem: Dell Device 0182 
Flags: bus master, medium devsel, latency 168, IRQ 19 
Memory at dfb00000 (32-bit, non-prefetchable) [size=4K] 
Bus: primary=03, secondary=04, subordinate=07, sec-latency=176 
Memory window 0: 80000000-83fff000 (prefetchable) 
Memory window 1: 88000000-8bfff000 
I/O window 0: 00003000-000030ff 
I/O window 1: 00003400-000034ff 
16-bit legacy interface ports at 0001 
Kernel driver in use: yenta_cardbus 
Kernel modules: yenta_socket 
 
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller 
Subsystem: Dell Device 0182 
Flags: medium devsel, IRQ 5 
Memory at dfbfd000 (32-bit, non-prefetchable) [size=4K] 
Memory at dfbfe000 (32-bit, non-prefetchable) [size=4K] 
Capabilities: <access denied> 
 
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05) 
Subsystem: Intel Corporation Device 1020 
Flags: bus master, medium devsel, latency 64, IRQ 17 
Memory at dfbff000 (32-bit, non-prefetchable) [size=4K] 
Capabilities: <access denied> 
Kernel driver in use: ipw2200 
Kernel modules: ipw2200 
     
```What am I doing wrong here?
Well what it looks like to me is that ati stopped support for your driver. That seems to be the issue, and it seems that the default mesa drivers didnt always have 3d acceleration either. Try installing the mesa drivers and get the dev files, they have a ati driver that works with older cards. usually better than the ati drivers actually. What i would do is install ubuntu tweak, and get and enable x.org repositories through there, both and then update, then check snaptic for the mesa experimental, those files have 3d acceleration and they work good on my card wich is a radeon hd 4350 from ati.

---


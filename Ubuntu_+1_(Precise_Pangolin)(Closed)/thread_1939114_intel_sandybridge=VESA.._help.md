---
title: "intel sandybridge=VESA.. help"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by gator on 2012-03-11
Hi i'm trying to get my toshiba touchscreen to get to its max res. Unless i boot with nomodeset i get nothing but a black screen ( although i hear the drums of login ). here's my lspci - 

 lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0d:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

I'm sure the intel driver will work but what do i need to do to stop vesa restrictions?

Ive tested the latest beta and ppa's - xorg-edgers and sna enabled intel driver.... still black screen

this is the exact hardware 
[http://www.mytoshiba.com.au/products/computers/all-in-one/dx1210/pqq09a-02900g/specifications#details](http://www.mytoshiba.com.au/products/computers/all-in-one/dx1210/pqq09a-02900g/specifications#details)

i can boot with nomodeset, but whats missing?

---

### Post by tista on 2012-03-11
OK..

Even though I'm not really sure that, so let us see your log:
/var/log/Xorg.0.log
/var/log/dmesg

Hopefully I want to see them on both "with" nomodeset and "without" nomodeset....

Cheers,
Tista

---

### Post by rtalcott on 2012-03-11
Have an HP...same problem...had to set some things in grub...cannot remember exactly...this link is helpful:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

and if you google a bit you will find a forum post that gives the parameters...I'll see if I can find it again.

EDIT:  This worked for me:
[http://ubuntuforums.org/showthread.php?t=1931562&highlight=hp+dm+2180](http://ubuntuforums.org/showthread.php?t=1931562&highlight=hp+dm+2180)

---

### Post by tista on 2012-03-11
> **rtalcott said:**
> Have an HP...same problem...had to set some things in grub...cannot remember exactly...this link is helpful:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

and if you google a bit you will find a forum post that gives the parameters...I'll see if I can find it again.

EDIT:  This worked for me:
[http://ubuntuforums.org/showthread.php?t=1931562&highlight=hp+dm+2180](http://ubuntuforums.org/showthread.php?t=1931562&highlight=hp+dm+2180)

@rtalcott,

Nice info! ;)

Regards,
Tista

---

### Post by gator on 2012-03-11
Thanks, i'll try this when i return to work. Fingers crossed

---

### Post by gator on 2012-03-13
i tried this morning and still a blackscreen, any other ideas??

---

### Post by gator on 2012-03-13
heres my xorg log with nomodeset, i'll try and get the one with modeset too.

---

### Post by gator on 2012-03-13
Here's the one with modeset. Interesting that the intel driver appears to load correctly, but my monitor stay black. There may be other moniors detected as i sometimes forget to unplug the displaylink adapters. I'm very close, i can feel it

EDIT:
After going through the log it appears it doesn't detect my touchscreen monitor. I'm guessing that i need a custom Xorg.conf with a monitor section.

 17.744] (II) intel(0): Output DP1 has no monitor section
[    17.744] (II) intel(0): EDID for output VGA1
[    17.888] (II) intel(0): EDID for output HDMI1
[    17.936] (II) intel(0): EDID for output DP1
[    17.936] (II) intel(0): Output VGA1 disconnected
[    17.936] (II) intel(0): Output HDMI1 disconnected
[    17.936] (II) intel(0): Output DP1 disconnected
[    17.936] (WW) intel(0): No outputs definitely connected, trying again...
[    17.936] (II) intel(0): Output VGA1 disconnected
[    17.936] (II) intel(0): Output HDMI1 disconnected
[    17.936] (II) intel(0): Output DP1 disconnected
[    17.936] (WW) intel(0): Unable to find connected outputs - setting 1024x768 initial framebuffer

---


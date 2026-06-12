---
title: "Ubuntu Server 14.04 No Video After GRUB"
date: 2014-06-14
forum: Server Platforms
---

### Post by iamdigitalman on 2014-06-14
Hello everyone. Recently I acquired a Fit-PC2i. Very nice piece of kit. Here are the specs:

1.6ghz Intel Atom
2gb of onboard RAM
802.11n wireless
2x gigabit NICs
30gb SSD
Intel GMA 500 onboard graphics, HDMI connector out back.

It also has 4 USB ports, 2 on back, 2 front via some weird not quite mini-a connectors. But I have the adapters. It also has full RS232 via another mini port on the front, again I have the adapter. And a micro? SD card slot.

I have been toying around with what OS to run on it, and settled on Ubuntu Server. It will be running headless as a web server, as well as Plex server, and act as a wireless bridge for some wired clients in my basement. But getting all this configured, I need a display. Setup went just fine, it even detected the onboard wireless, and used that for it. However, after the first boot, I get the GRUB menu, then a bit of scrolling boot text. After that my monitor goes black, and gives me the no signal message before hitting standby. I still see the HDD activity LED blink for a bit, so I assume it's booting fully. However, the wireless LED does not light up, so I can't SSH into it. Not sure why it detects that for setup but those settings don't carry over to the installed system...

I have tried it connected via a HDMI to DVI adapter to my monitor, as well as straight HDMI to my TV. Nothing works. I read some other forums about setting NOMODSET, and several other parameters, vga=x and whatnot. Nothing seems to work.

I also have a original EEE PC 701 in my possession with similar, but older GMA 900 graphics. I did a test install on that, and it works fine post GRUB, get my console and everything. So maybe it's a driver? I even remade the install USB thinking it was that. But nope.

My next step will probably be to roll back and install an older LTS of Ubuntu Server, 10.04 is still supported, or 12.04. If it works on there, some defaults got changed along the way.

---

### Post by elico on 2014-06-14
How about failsafe mode?

---

### Post by iamdigitalman on 2014-06-16
Not sure if I am going into it right, but selecting recovery mode from the grub menu, I get the boot text except at a lower resolution, then the monitor goes to standby. Maybe i'm not getting it into failsafe correctly...

---

### Post by iamdigitalman on 2014-06-17
bit more info: popped the SSD out of the fit, and hooked it to a USB adapter to my EEE 701 netbook. It boots just fine, sans boot splash. But I am able to login and everything. 

I was able to get the recovery menu to load too (something I couldn't do before), and there is no failsafe mode listed.

So, is there any package I need to install from here, or should I try another version of server? I know I was able to get the regular desktop version to install, but the GUI is so slow its unusable, and I need the server components.

---

### Post by wgordonharris on 2014-06-18
I'm having the same problem with server 14.04 with similar hardware.  Video on the attached monitor goes blank after grub.  Tried various tweaks to default/grub & updating grub, all to no avail.  VERY FRUSTRATING.

lspci -vv:

00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Foxconn International, Inc. Device 0d7c
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 50
        Region 0: Memory at dfc00000 (32-bit, non-prefetchable) [size=1M]
        Region 1: I/O ports at f100 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [d0] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [b0] Vendor Specific Information: Len=07 <?>
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
                Address: fee0f00c  Data: 4172
        Kernel driver in use: gma500

---

### Post by iamdigitalman on 2014-06-19
Interesting, how were you able to get that output? I would like to see what mine is. And yours is even using the GMA500 driver, which should have been working years ago.

---

### Post by Vegan on 2014-06-19
intel's graphics hardware is not really very much more then a software driver

might be better to use a desktop with radeon which evidently supports open source better than nvidia

---

### Post by iamdigitalman on 2014-06-19
The whole reason I am using this is it's a small fabless device that only draws 7 watts at full power, yet is powerful enough to run a home server. Ubuntu server should be lightweight enough and easy enough to use on this hardware.

---

### Post by Vegan on 2014-06-19
the atom is used widely for small form factor machines like netbooks and tablets

not the best choice for a server

amd makes low power processors for light duty machines

modern processors all use lower clocks now for light loads, so even a gaming cpu like my phenom falls to 1w when idle

---

### Post by mikewhatever on 2014-06-27
> **iamdigitalman said:**
> bit more info: popped the SSD out of the fit, and hooked it to a USB adapter to my EEE 701 netbook. It boots just fine, sans boot splash. But I am able to login and everything. 

I was able to get the recovery menu to load too (something I couldn't do before), and there is no failsafe mode listed.

So, is there any package I need to install from here, or should I try another version of server? I know I was able to get the regular desktop version to install, but the GUI is so slow its unusable, and I need the server components.

You should probably just install ssh server in recovery mode, and forget about the vicious beast Intel called gma500. 

PS: The regular desktop of Ubuntu requires hardware accelleration, and won't work well on hardware long abandoned by the vendor. That said, Lubuntu 14.04 runs decently.

---

### Post by cariboo on 2014-06-28
I'm running an atom powered minidlna server with absolutely zero problems, it runs headless, and sits in my media centre. I use wakeonlan when I want to use it, it starts up in seconds. Minidlna runs about 10% of cpu resources and doesn't have a problem serving most types of media. I access via ssh when I need to do something on it.

---


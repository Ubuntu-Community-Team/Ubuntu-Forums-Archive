---
title: "How many more feel the same about Jack"
date: 2011-08-20
forum: Ubuntu Studio
---

### Post by chkneater on 2011-08-20
I don't know how many people have had success with jack, then again I don't think that it is even possible to use jack.  I have had over 4 different distros of Ubuntu, included Jack in every one, used system sound used multiple sound cards, even 32bit and 64bit systems, and the only thing I get from Jack is crap.

I'm in the audio group so don't tell me that.

Jack is flawed fundamentally.  How many different connections and patches do you HAVE to have to make this stupid thing functional?  Doesn't work in RT, doesn't work with all the latency in the world, doesn't work with mem locked or unlocked.  I have tried every option to get this stupid program to work because apparently this is the only offering as far as recording semi-professionally.

And yes I know it's free, so I shouldn't be able to gripe right?  WRONG!!  I have put so much time and energy, changing towers and sound cards, ensuring my cables weren't at fault, no it turns out that jack is a piece of crap, for the record, sorry Paul Davis but maybe a little info  included WITH the program regarding it's capabilities and how to, I don't know, USE THE DAMN thing and maybe then I would be touting the wonders of jack from some green carpeted field in Switzerland with Julie Andrews, but I'm frankly pissed because after yet another Ubuntu upgrade, Jack is still the same POS it has always been.  Just to put the nail in the coffin, I can get Audacious to record better than Jack performs, so there you go.

I don't know why I put up with this

So, if anyone has a differing opinion, why don't you explain how jack works so idiots like me can understand a  little better?

And don't one person ask me if I unmuted ALSAMixer, I will have your throat!

Bump cuz I know someone identifies

---

### Post by sgx on 2011-08-20
Hi, lots of recent discussions here where people were successful using
the replies here along with their own ongoing research, to achieve good jackd results, you will be next, nothing is broken, so what is your souncard, soundchips, current installed linux version, cpu/memory/videocard, linux experience level?

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl), 

[https://help.ubuntu.com/community/Ho...CtlConnections](https://help.ubuntu.com/community/Ho...CtlConnections)

start with the bottom link, screenshots and info, and then the other articles.


The ps ux command will show whats running, in case somethings get's
using jackd before you do

killall name-of-process if anything named pulse is running.
Click Setup on the main qjackctl gui. The entries in the qjackctl setup panel

Input device >
Output device > 

(click the > widgets for the dropdown list are what your
kernel has discovered. Lookup in google

lsmod name-of-your-soundcard

others with similar gear and solutions
should be there.

Once you choose your soundcard, (something like hw:1 hw:0,0 or even a brand named entry), you'll have to make various connections, in one, two, or three of the qjackctl connections panels, and sometimes choose also an apps audio system preference, not all of them default to jackd. Once one of them is functional, the others will also be able to work, but maybe have different connections. Feed an ongoing sound source to the soundcard inputs while you make connections, to hear when you are successful. alsamixergui is good at displaying every sound input/output, part of the alsa-tools package, if not separately.

In the qjackctl connections panel (press Connect on the main gui)
you must choose input/output, and/or capture/playback for each software and hardware you want to use. The Alsa tab is for midi, the Audio tab is for audio capture/playback. Each has a left and right side, select an item from each side, and press this panels connect button (not the one on the main gui) and a connection line is drawn.

In the Alsa tab, a softsynth would appear on the right panel
and a midi keyboard on the left panel, select one on each side, connect them to send keyboard data to the softsynth.

In the audio tab, the softsynth sound output is on the left panel,
and would be connected to your soundcards output, on the right panel.
An fx app like rakarrack would show on the left and right panels,
so the softsynth output would go to rakarrack input, and rakarrack output, would go to your soundcards output.

a2jmidid makes use of the middle midi tab, for yoshimi and other apps
using newer jackd midi abilities.

You could install timemachine to test recording, and connect the sound outputs you choose, to the timemachine input, press record, and begin playing.

qjackctl saves a text file, .jackdrc with your current setup. A few minutes reading the jackd manpage, and taking notes

[http://fclose.com/p/linux/man/1-jackd/](http://fclose.com/p/linux/man/1-jackd/)

will explain the cryptic
entries in .jackdrc and you can make and keep special versions as a text file to run as a command, for setups you use only occasionally.


(as to your overall frustration, pclinuxos has a very different
approach to linux, very very conservative by not including problematic or the latest sometimes unproven packages. Ubuntu is on the other extreme, massive numbers of packages, and many are very new, sometimes exlusive at first, and a large group of supporters contribute with configurations, modifications, discoveries, and great knowledge of linux details.

jackd 1 Vs jackd2, and the way they are developed, released, named and included in various linux versions, can be confusing, but once sorted, its a great system with unmatched flexibility.

Cheers

---

### Post by sgx on 2011-08-20
Consider the way help forums work, no mindreaders anywhere, so we ask politely, provide our gear details, answer requests for more information, make the necessary changes and purchases, and keep a good sense of humour, because everyone is on a learning curve, with different goals and abilities.

youtube videos of ardour, hydrogen, zynaddsubfx, rakarrack and others often include qjackctl setup steps. 
Cheers

---

### Post by chkneater on 2011-08-20
thanx for the information and the links above sgx, I will be trying them shortly.

secondly, I wasn't actually asking for any help per se, just venting on jack seems to be broken in every version I get no matter what I do.

But since you asked, lspci -v:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel, IRQ 255
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: nv_tco, i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at f400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e000 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at cc00 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=128
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff
	Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

02:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450] (prog-if 00 [VGA controller])
	Subsystem: Diamond Multimedia Systems Device 5450
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdbc0000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 9c00 [size=256]
	Expansion ROM at fdba0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
	Subsystem: Diamond Multimedia Systems Device aa68
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at fdbfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

03:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 18
	I/O ports at ac00 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

hellkiller@hellkiller:~$ sudo lspci -v
[sudo] password for hellkiller: 
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping Enable+ Fixed-

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] #00 [00fe]
	Capabilities: [fc] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
	Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
	Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping Enable- Fixed-

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel, IRQ 255
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: nForce2_smbus
	Kernel modules: nv_tco, i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at f400 [size=16]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e000 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] MSI: Enable- Count=1/4 Maskable- 64bit+
	Capabilities: [cc] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at cc00 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] MSI: Enable- Count=1/4 Maskable- 64bit+
	Capabilities: [cc] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=128
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff
	Capabilities: [b8] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
	Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a45
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c800 [size=8]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

02:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450] (prog-if 00 [VGA controller])
	Subsystem: Diamond Multimedia Systems Device 5450
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdbc0000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 9c00 [size=256]
	Expansion ROM at fdba0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
	Subsystem: Diamond Multimedia Systems Device aa68
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at fdbfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

03:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 18
	I/O ports at ac00 [size=256]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

You can see there is some conflict going on with the HDMI output from the video card and the sound card

---

### Post by sgx on 2011-08-20
If after using the info at the links, it still is not working, try the lsmod  command, and look in the output for something like
snd_intel8x0, and something related to the  ati/diamond hdmi sound
system. You can possibly blacklist the ati sound, if it uses a special
kernel module. 

in /etc/modprobe.d folder, put a text file named blacklist,
containing a line

blacklist name-of-module

If the ati video is a pci card, and a motherboard video
chip exists, you could use the bios controls to switch off the ati,
and activate the motherboard video. 

[http://forum.xbmc.org/showthread.php?t=96537](http://forum.xbmc.org/showthread.php?t=96537) 

This topic related
to achieving 5.1 suround sound, (non-jackd) audio on similar hardware
using xbmc, which I am not familiar with. Maybe a ubuntu video forum would have more hdmi users?

[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

Cheers

---

### Post by chkneater on 2011-08-20
I wholeheartedly agree about that last part sgx, and I felt all along that blacklisting that module would prevent the HDMI from loading and would help unmuck this probem.  I still don't think it's the entire problem I'm having with jack, but I know I must fix that before moving on to other issues.

SGX, you raised another question that confounds me about jack, which is better jack1 or jack2, and why was jack used on previous versions and this uses qjacktl?  I know essentially they are similar, but come on??!

And as far as the pclinuxos you mentioned, is that good for strictly recording?  If so I can use Ubuntu for every day stuff and switch OS to record!

---

### Post by jejeman on 2011-08-21
> and why was jack used on previous versions and this uses qjacktl?Qjackctrl is not jack. It's just a qt frontend for jack, and is installed by default since 8.04. (as far as i can confirm)

---

### Post by sgx on 2011-08-21
> **chkneater said:**
> SGX, you raised another question that confounds me about jack, which is better jack1 or jack2, and why was jack used on previous versions and this uses qjacktl?  I know essentially they are similar, but come on??!

And as far as the pclinuxos you mentioned, is that good for strictly recording?  If so I can use Ubuntu for every day stuff and switch OS to record!
As jejeman says, there are a few gui for jackd, qjackctl, patchage,
and jp1,

[http://www.linuxdsp.co.uk/download/jack/download_jp1_jack/index.html](http://www.linuxdsp.co.uk/download/jack/download_jp1_jack/index.html)

which I like, due to less clicking needed, but I use
the features of qjackctl to switch between keyboard and guitar
interfaces. I open jp1, if it will be a very short, or very long session. I also edit my .bash_history file, so a few .jackdrc commands
are easy to recycle using the up-arrow key in a terminal

pclinuxos is .rpm based, not .deb  and has the needed audio basics in it's repositories, which use synaptic. A few packages, like yoshimi and rakarrack I need to use alien to convert from .deb to .rpm

alien -r yoshimi_0.058.1-0lucid0~autostatic1_i386.deb

rpm -i --nodeps yoshimi-0.058.1-1.i386.rpm

(rpm -i  is like dpkg -i in debian systems)

The pclinuxos kernels are 32 bit, and well crafted, with pae and bfs versions, ( [http://ck.kolivas.org/patches/bfs/bfs-faq.txt](http://ck.kolivas.org/patches/bfs/bfs-faq.txt) )and there are several mini distros, using E17, openbox, gnome, kde etc as chosen environments. A Full Monty dvd version is also available. It's a well maintained 'rolling release' distro, so periodically, you update all packages with synaptic, as system testing is done on that assumption. I use audacity, wineasio/reaper, hydrogen, rakarrack, yoshimi, phasex, calf plugins, timemachine, a few dozen free and commercial VSTs, and new things to test. Very very few crashes, due in part to the wonderfully supported mAudio 24/96 pci soundcard, and an nvidia graphics card that is configured by default the the nVidia driver,
(nice for some foobillard.

With this system stability, the differences between jackd 1 and 2, are
not noteworthy. But productivity is. 

With such a system, windows gets booted mainly to update
avast and spybot, run a handful of synthmaker plugins with gui issues, and I use it to register and upgrade a few
Native Instruments, and IK Multimedia products.

Most linux knowledge is portable, and I learn lots from the
braintrust at this forum! :)

---

### Post by chkneater on 2011-08-22
Awesome, thanks for the replies Jejeman and SGX, that clears up a lot for me.  I remember with either Heron or Ibis, the version of jack (which was not qtjack I believe) and I had no problems with it.  Ever since I upgraded from that distro Ihave not gotten it working since, I think because I've been using the default version instead of Jack.  Thanks much to all for your help.  I hope you don't mind if I PM any of you if I have any more jack questions?

---

### Post by JuanPabloCuervo on 2011-08-22
> **chkneater said:**
> I don't know how many people have had success with jack, then again I don't think that it is even possible to use jack.  I have had over 4 different distros of Ubuntu, included Jack in every one, used system sound used multiple sound cards, even 32bit and 64bit systems, and the only thing I get from Jack is crap.

I'm in the audio group so don't tell me that.

Jack is flawed fundamentally.  How many different connections and patches do you HAVE to have to make this stupid thing functional?  Doesn't work in RT, doesn't work with all the latency in the world, doesn't work with mem locked or unlocked.  I have tried every option to get this stupid program to work because apparently this is the only offering as far as recording semi-professionally.

And yes I know it's free, so I shouldn't be able to gripe right?  WRONG!!  I have put so much time and energy, changing towers and sound cards, ensuring my cables weren't at fault, no it turns out that jack is a piece of crap, for the record, sorry Paul Davis but maybe a little info  included WITH the program regarding it's capabilities and how to, I don't know, USE THE DAMN thing and maybe then I would be touting the wonders of jack from some green carpeted field in Switzerland with Julie Andrews, but I'm frankly pissed because after yet another Ubuntu upgrade, Jack is still the same POS it has always been.  Just to put the nail in the coffin, I can get Audacious to record better than Jack performs, so there you go.

I don't know why I put up with this

So, if anyone has a differing opinion, why don't you explain how jack works so idiots like me can understand a  little better?

And don't one person ask me if I unmuted ALSAMixer, I will have your throat!


Jack works great here...

---

### Post by chkneater on 2011-08-22
Which is EXACTLY why I thanked SGX and Jejeman for their input/help, whereas your comment is just gloating.  If you have no information to offer and you're not asking for help, then leave the snide comments aside and just be helpful.  Yes. maybe jack works super awesome for you, great congratulations, you are the king of the universe.  Then again, maybe when they programmed it, they programmed it with hardware similar to yours and not mine, therefore they couldn't accurately debug on systems like mine.  But thank you for making me feel like crap after all the effort I've put into getting it to work.  Good job reading the previous posts also Einstein.

---

### Post by JuanPabloCuervo on 2011-08-22
> **chkneater said:**
> Which is EXACTLY why I thanked SGX and Jejeman for their input/help, whereas your comment is just gloating.  If you have no information to offer and you're not asking for help, then leave the snide comments aside and just be helpful.  Yes. maybe jack works super awesome for you, great congratulations, you are the king of the universe.  Then again, maybe when they programmed it, they programmed it with hardware similar to yours and not mine, therefore they couldn't accurately debug on systems like mine.  But thank you for making me feel like crap after all the effort I've put into getting it to work.  Good job reading the previous posts also Einstein.

Einstein doesn't know :) how to make Jack Work. :lolflag:

---

### Post by mikeh789 on 2011-08-23
jack works great for me. i usually run gksudo qjackctl to trouble shoot for permissions errors. you *dont* want to run JACK as root all the time, but this has saved me time in the past when getting started with new gear. there are hardware cases that do not work well with JACK (such as IRQ issues with USB or firewire devices). if you can, simplify your setup. get down to one sound device, and try getting JACK to see and use it. if you can get on freenode and join the #ubuntustudio channel we can spend some time troubleshooting in realtime. im holstein in there, and im idle in there around the clock, and i check in often. getting JACK running is not trivial, but i assure you it works well for me on several hardware cases.

---

### Post by bluesscream on 2011-08-23
to be true without these forum peoples help I'd never been able to make my studio run an obsolete ice1712 card simulaneously with the onboard chip, make jackd cooperate with pulseaudio, get flash working, resolve firewire issues... and every approaching distupgrade makes me nervous (and curious :twisted: ) 
DAW on standard Linux is far away from working ootb. May be you'll be lucky with KXstudio or AVLinux, you can try it on livedvd, then for heaven's sake don't touch your running system any more.

---

### Post by akavir on 2011-08-24
I've been using JACK on many distros for 6 years now.  In the early days, I would totally agree with you.  It never work spectacularly for me either.  In the last, I'll say 3 years, it's worked on every system, every distro, and every input device I've thrown at it.  In the last few, I've found that using a well tailored studio distro like KXStudio and AV Linux are the way to go.  I use KXStudio on my main setup, and carry AV Linux 5.0 Live USB with me everywhere I go.  Though mileage may very, and every setup is different, it is a matter of testing, playing, and seeing what works for you!  Glad that people here helped get things working for you and the many other that have had issues with JACK.

---

### Post by chkneater on 2011-08-25
Interestingly, it was a combo of the suggestions on here and a discovery about my card.  

First my ATI video card has HDMI sound output and I had to blacklist its kernel in modprobe.d  Then I removed/purged EVERY sound file with an Nvidia card in place for the moment.  Replaced the ATI card, started it up and still didn't get jack working, although I could see it picking up some sound in the monitor, so I reach around to the sound card and it was the stereo line converter going to deep into the card and not connecting right so I had to pull it out just a touch.  Oh, and ALSA mixer had the MIC and LINE muted.  Perfect storm.

Now I just have to wait for a kernel upgrade to throw it all off again YAY!!  I am going to try some of those other distros as long as they're aimed at studio specifically.

---

### Post by sgx on 2011-08-25
And don't one person ask me if I unmuted ALSAMixer, I will have your  :P throat! :P  
----------------------------------------------------------------------
My pet blindspots include using the wrong headphones, forgetting I changed soundcards in qjackctl, and not having the usb the device plugged in. :(

Surely 'quiet' would be a better default mixer level,
than :evil: silent :evil: .

---

### Post by lavadisco on 2011-08-26
Ha. I specifically came to this forum because I tried pro audio on Ubuntu like two years ago, and it sucked (mostly because of Jack), but I thought maybe it'd gotten better since then. I see not.

---

### Post by sgx on 2011-08-26
Actually, jackd implementation is extremely solid, and once the few kinks are ironed out of personal hardware peculiarities, it's a great
system. Ubuntu has the unique dilemma of drawing great numbers of new users, to a linux with a rapid development cycle, and sometimes new kernel versions, or pulse audio implementation, or updated system libraries get in the way of instant success. So it may appear that it's
all a big jumble, because there are lots of new users with questions. (but weren't we all new once?) Most people who ask, and post details, get things working. And using a barebones distro with
just the basic audio apps added using synaptic and dpkg, can be very
rewarding, and productive, and bypass some side effects of rapid developement.
Cheers

---

### Post by chkneater on 2011-09-06
> **lavadisco said:**
> Ha. I specifically came to this forum because I tried pro audio on Ubuntu like two years ago, and it sucked (mostly because of Jack), but I thought maybe it'd gotten better since then. I see not.

You missed the point, it was a physical problem with line-in on the card and the fact that for some reason ALSA mutes Line-in and Mic for some reason.  Jack wasn't actually the problem which I assumed it was for the same reason you probably did.

"]And don't one person ask me if I unmuted ALSAMixer, I will have your  :P throat! :P"  


I wouldn't blame you a bit SGX! 

But I totally agree with you about the different implementations and versions and how confusing it can be.  Hell, I've been using Ubuntu exclusively since 2007 and things change all the time.  And at the same time, major OS distros are attempting to mimic Linux features, poorly albeit.  

If Ubuntu would make one distro that truely was LTS (at LEAST 10 years) that had a dedicated team that knew that distro in and out and could provide support, but i know, money, money, money...

Hey, Ubuntu is free, the frustration sucks, but I have never had a problem I wasn't able to get help with either on here or on launchpad.net, eventually; but I heard some head of Apple saying the other day that the future of computing is in music production, so I really hope that Linux can dominate the category and be the de-facto musicians production suite before the rest make it proprietary.

> **JuanPabloCuervo said:**
> Einstein doesn't know :) how to make Jack Work. :lolflag:
Einstein doesn't know how to make Jack Work. 

He figured out relativity and super-massive black holes using only a telescope.  He may be able to figure out jack???  Hell, I'd have a better chance at proving a Unifying Field than get jack working if I change kernels or something!

---

### Post by sgx on 2011-09-06
> **chkneater said:**
> "] but I heard some head of Apple saying the other day that the future of computing is in music production, so I really hope that Linux can dominate the category and be the de-facto musicians production suite before the rest make it proprietary.

Music production doesn't require enough cpu/ram to make custom linux
setups a viable option, as in the case of cinematic rendering farms.
So the apple guy assumes Microsofts infinite string of blunderOS will
assure them of good standing among those professionals whose billable time can't be frittered away fixing computer configurations. This leaves some middle ground for linux users to build systems, and studios
that are competitive in certain situations, and certainly great fun for
personal use. Linux will not dominate, short of a catastrophic international war where nukes disable the net, and general communications/daily life, for an extended time period.

As for your personal saga, just get a desktop PC, 3 ghz P4 or better, an mAudio pci card, an nVidia graphics card, and live happily ever after. You must plan your linux studio around working hardware, or you will be the ware working hard :)

Cheers

---

### Post by Thad E Ginathom on 2011-09-14
Well, me probably... but it it not so much a matter of how I feel about Jack, as how I feel about Firewire audio in Ubuntu and the fact that it is not simply a mater of having a driver for the device, but a complex series of issues, including the driver in FFADO, but also the necessity to address the device *through* Jack.

I can understand that it might be a wonderful tool for the studio, but it is a terrible thing to force upon the music listener. 
[QUOTE=sgx]As for your personal saga, just get a desktop PC, 3 ghz P4 or better, an  mAudio pci card, an nVidia graphics card, and live happily ever after.  You must plan your linux studio around working hardware, or you will be  the ware working hard[/QUOTE]Oh, so, so true, although all the more frustrating when , yes, your device is *supposed to be fully supported.*

My experience has resulted in my knowing more than I ever wanted to about real-time processing, priorities, latencies and all the stuff that needs to be tweeked to get my system just to play music through my firewire device (Audiofire2) without stuttering and dropping out. Then came handling the instabliity of the thing. I could listen to music for hours, one day, only to be back to 2-minute Xruns the next. I have spent hours watching system monitors and looking at logs, never ever finding out the actual causes. Some tweaks seemed to do nothing, others seemed to be the final piece of the jig-saw I was looking for --- only to be back to xruns the next day.

Compared to all this, my PCI sound card was plug-and-play.

Readers may ask, "Why on earth did he bother, then?" The answer is because history has left me owning the Audiofire, because it is a challenge, and, frustration aside, I have been quite enjoying some of the reawakening of fossilised Unix knowledge, and I didn't have much better to do. It was more stimulating to the brain than just browsing the net.

Now, the point of all this is, it seems (I'm still holding my breath) that salvation has come my way --- in the form of **[KXstudio]("http://kxstudio.sourceforge.net/Main_Page")**. Actually, now I'm having problems with realtime kernels but that's another story and the point is, that KXStudio's implementation of Jack2, and their Cadence tool, and the way that falkTX has tied together the whole of Linux audio is just superb**.  **I even get sound out of Wine. How? Just by logging in and opening an application!--- and, all of this under the same generic kernel which, with Ubuntu Studio 10.04, a few weeks ago, I could not even move the mouse on the screen without Jack going mad

---

### Post by oscarivera9 on 2011-09-14
> I don't know  how many people have had success with jack, then again I don't think  that it is even possible to use jack.  I have had over 4 different  distros of Ubuntu, included Jack in every one, used system sound used  multiple sound cards, even 32bit and 64bit systems, and the only thing I  get from Jack is crap.

I used to feel just like what you said above.  I thought I didn't know Jack.  I kept trying all sorts of different things and nothing worked.  I was ready to give up and then something happened.  Don't ask me what it was, because I still don't know what happened and I still don't know Jack, but now it works.  Not only does it work, it actually works like a charm.  I do think that the latency I'm getting now using Ubuntu Studio is a bit better than what I get when I use Windows 7.  However, I don't want you to think that one day it was up and running and everything was fine, because it wasn't like that.  It was more like I got a different recording interface (Lexicon Alpha) and disabled my Line6 Tone Port UX1 and in the process, there were a couple of other changes that took place, but they were done in the background without my knowledge.  I had this thought that the Line6 Tone Port might be incompatible with Linux, even though it was recognized by the OS and there were plenty of references to it being able to work.  So I went ahead and blacklisted it and all sorts of problems that I used to have are now gone.  I have a dual-boot system (Windows 7) so the device is still plugged in and I still use it with Windows, but Ubuntu no longer even recognizes it (because it's blacklisted of course).  Somehow, when I made that change, Jack began to work just fine.  I opened up Jack and hit the Start button and that's it.
I wish I could help you but in reality what I'm doing is simply telling you that there's hope and that one day you'll find something that will make Jack work.  It happened with me.

---

### Post by sgx on 2011-09-14
You might like a Fender Mustang usb amp, used $50, new $99 or less
plug-n-play in linux, shows up as Mustang in qjackctl. There is even a linux gui called plug, to replicate the amp modelling aspects of the windows/mac Fuse software, so new presets can be made without dual booting.

---

### Post by chkneater on 2012-09-08
> **akavir said:**
>   I use KXStudio on my main setup, and carry AV Linux 5.0 Live USB with me everywhere I go

Absolutely, I just installed AV and after making sure the devices were correct I've been able to run Jack in RT for over 9 hours using flash and video and everything with about 2 xruns I didn't even notice.  It seems that even tho I'm running jack for all my audio, my comp is running smoother than just using ALSA.  Even tunemybass.com works which I sincerely doubted. Thanks again for all the help.

> **sgx said:**
> You might like a Fender Mustang usb amp, used $50, new $99 or less
plug-n-play in linux, shows up as Mustang in qjackctl. .


As for your personal saga, just get a desktop PC, 3 ghz P4 or better, an mAudio pci card, an nVidia graphics card, and live happily ever after. [/QUOTE]


I'll have to keep an eye out for the amp, as far as my personal saga, I WISH!  I'm lucky I was able to wipe windows and save this one!!  My next purchase will be a better tower, I refuse to pay for windows tho.  I'm an ATI/AMD guy, is nVidia better for recording or just better at avoiding conflicts?

> **oscarivera9 said:**
> 
I wish I could help you but in reality what I'm doing is simply telling you that there's hope and that one day you'll find something that will make Jack work.  It happened with me.

Actually that's very similar to what happened to me, alsamixer had the wrong card as the default for some reason (even tho I blacklisted it in modprobe.d), once I figured that out I was able to backtrace everything and get it working and it's been semi-OK pretty much... actually it runs pretty well for *most* things now, even in RT.  I figured using jack that alsamixer settings would be irrelevant but I was wrong apparently.  It's funny looking back at my level of frustration!

---

### Post by bhilmers on 2012-09-08
> **chkneater said:**
> It's funny looking back at my level of frustration!
I don't find it funny at all actually. Your point is very strong. Pro audio on Linux is a colossal joke. It works within such strict parameters to be practically useless, especially for everyday users -- You know, the musicians who don't have Computer Science degrees? I'm still amazed that Linux can't do what I was able to do easily in Windows 98.

Right now I have a Jack problem where sometimes it works and sometimes it doesn't. I've got a fresh install and there is a 50/50 chance Jack will work when I start it. There is no rhyme or reason to the behavior either. At one time I thought it was because some other application was taking over the soundcard, but even after a system restart there is still a 50/50 chance it will work. Even if it does run, there is a constant stream of xruns and latency is way too high for recording performances.

And forget about the "help" on the forums. It's a bunch of people posting anecdotal crap (if they offer anything at all). They contribute code that worked for them, and as you try their suggestions your system breaks even more. So many just want to blame the user. I don't even bother asking for help anymore. I don't need something "community driven," I need real answers from people who know what they are talking about so I can be productive. In fact, I shouldn't need to search for answers at all. It should "just work" like it does on Win/Mac. Those guys had it perfected over a decade ago. The fact Linux can't get it right is embarrassing beyond belief.

It's too bad. Linux is almost the perfect OS. I use it for all business and art all the time. But audio? Forget it. I'm just passing time until I can afford a real OS to do audio on. Of course, I can always install an old copy of WinXP on a computer and use that for audio, but why not just do everything on Windows then?

---

### Post by Thad E Ginathom on 2012-09-09
> **Thad E Ginathom said:**
> Well, me probably... but it it not so much a matter of how I feel about Jack, as how I feel about Firewire audio in Ubuntu and the fact that it is not simply a mater of having a driver for the device, but a complex series of issues, including the driver in FFADO, but also the necessity to address the device *through* Jack.

...

Now, the point of all this is, it seems (I'm still holding my breath) that salvation has come my way --- in the form of **[KXstudio]("http://kxstudio.sourceforge.net/Main_Page")**....

And, a year later, I am happily listening to music, courtesy of KXStudio, barely aware (unless I want to be) that Jack is there. It just works. Wonderful.

On the other hand, when I *want* to play *studio*... a world of tweaks and effects and stuff is there and the KXStudio tools make it all so easy to wire things together.

With the front-end Cadence tools, Jack is no longer either a dumb slave or an unwilling beast: it is a tallented coworker (for those that need to ork cows).

A year later ...I *don't *feel the same about Jack :)

(I do feel the same about Ubuntu firewire support, although it has improved, and the unwillingness of some manufacturers to provide linux support, but then, I suppose that is a feature of our Linux world)

---

### Post by sgx on 2012-09-10
> **bhilmers said:**
> Pro audio on Linux is a colossal joke.

The joke is on you, if you prefer choosing to make
ridiculous assertions about things you fail to understand, rather than hitting a search engine, and sorting out your issues.

Every computer OS under the sun works
ONLY when you choose it's strictly correct settings.
The 'computer science' platitude is cyber peasantry,
not impressive. Feed relevant data in a search engine

name-of-souncard
motherboard-chipset
qjackctl
and words like problem, error, fails

Your issue has probably been covered many times.
Cheers

---

### Post by bhilmers on 2012-09-10
> **sgx said:**
> The joke is on you, if you prefer choosing to make
ridiculous assertions about things you fail to understand, rather than hitting a search engine, and sorting out your issues.

Every computer OS under the sun works
ONLY when you choose it's strictly correct settings.
The 'computer science' platitude is cyber peasantry,
not impressive. Feed relevant data in a search engine

name-of-souncard
motherboard-chipset
qjackctl
and words like problem, error, fails

Your issue has probably been covered many times.
Cheers
Been there, done that. I've looked at hundreds of threads and web pages over the past two years trying to get a stable, effective workflow. It's not from lack of trying or lack of understanding. Here is [a great example]("http://ubuntuforums.org/showthread.php?t=2050044") of community driven support. I'm a average user. I have no intention of getting a degree in Computer Science so I can play music, I'll just use another system. And yes, Linux audio is a joke. You can see this in the number of professional musicians/djs/producers that use it, which is practically none. Compile a list of studios that rely on Ardour versus Pro Tools and you can see the proof in practice. Take your ideology and keep it to yourself, I don't need the Linux "blame the user" mentality.

Have a nice day.

---

### Post by sgx on 2012-09-12
Instead of another rerun of failures, you should mention
the soundcard, video card, and motherboard chipset,
and post the .jackdrc textfile, and it's backup.

a basic command that almost never fails is

jackd -d alsa -r 44100

then start qjackctl.

The boot process can reassign your soundcard hw: ID, when things are
plugged in or out, as may be the case with a graphic artist using special external drawing devices.
Cheers

---

### Post by Sylos on 2012-09-15
> **bhilmers said:**
> 

And forget about the "help" on the forums. It's a bunch of people posting anecdotal crap (if they offer anything at all). They contribute code that worked for them, and as you try their suggestions your system breaks even more. So many just want to blame the user. I don't even bother asking for help anymore. *I don't need something "community driven," I need real answers from people who know what they are talking about so I can be productive.* In fact, I shouldn't need to search for answers at all. It should "just work" like it does on Win/Mac. Those guys had it perfected over a decade ago. The fact Linux can't get it right is embarrassing beyond belief.



Well then perhaps we all ought to start paying Paul Davis £250 a shot for ardour and jack and then he can employ a nice team to offer support so that people can get the information from people that know rather forum troglodites, eh?

Seriously man, coming into the support section and insulting the help users try to give is bad form. I agree that much of what is said on here is derived from peoples own experiences and how they fixed their system (something which may not work for yours) but as far as I am aware, most people here are not developers of the software we are using. Just people prepared to tinker (and take time out of their "productive" part of the day to try and help people who are struggling). People like sgx are constantly on this forum it seems, dishing out help and spending time researching problems and trying to come up with solutions. And I think that should be applauded, not mocked. I dont have a degree in IT or anything like that but I manage to get by with the help of people like that and I appreciate that. In turn, I try to help others where possible (even if its only be asking for my details and seeing the thread bump up to the top of the list again).

As for the old, "it should work like it does on mac/windows.." well then lobby the hardware manufacturers to get proper linux support for their products. Windows/mac works so well with the hardware because the guys who designed it also wrote a driver for it, and installer for it, then popped it on a disc for you and stuck it in the box. If we had that on linux we would, Im sure, be a lot further forward.

Many of us have had problems that appeared to be beyond the abilities of the forum community to fix (I certainly have). Its really frustrating! But its churlish to start bad mouthing the community because they couldnt fix your problem. As sgx has already said, maybe you should try posting up some specs and details about your problem and what you have tried to remedy it. Then at worst you will be able to say "I told you so" when nobody can fix it.

If you dont like linux audio, thats your opinion and its valid to voice your issues with it (criticism is required for growth anyway). But I doubt Im the only one who finds it objectionable to start having a go at volunteers trying to help people.

Cheers

---

### Post by sgx on 2012-09-15
There have been some great efforts in long long threads,
the E-mu 0404, FLStudio, M-Audio FastTrack Ultra Pro,
and many firewire and usb topics. I learn much from them,
without contributing, and see lots of determination
against the odds, with results that are sometimes unexpected.

Hopefully, the release of Ardour 3 will be accompanied,
or soon followed by,
some precision and clarification of the two main jackd
variants, and the interworkings of alsa, pulse, jackd, and jack-midi.
Cheers

---

### Post by smartboyhw on 2012-09-15
> **sgx said:**
> There have been some great efforts in long long threads,
the E-mu 0404, FLStudio, M-Audio FastTrack Ultra Pro,
and many firewire and usb topics. I learn much from them,
without contributing, and see lots of determination
against the odds, with results that are sometimes unexpected.

Hopefully, the release of Ardour 3 will be accompanied,
or soon followed by,
some precision and clarification of the two main jackd
variants, and the interworkings of alsa, pulse, jackd, and jack-midi.
Cheers

Hmm the thread "How many more feel the same about Jack"...

I do agree Jack is a difficult thing to set up.

Indeed most questions in here and in #ubuntustudio are about Jack. 

I think Kaj Ailomaa (documentation lead of Studio) will write one big tutorial about it..

But anyway, try to do your best everybody...

Sgx: Ever want to help Ubuntu Studio in anyway? (contributing) :)

---

### Post by Elfy on 2012-09-15
Old thread closed.

---


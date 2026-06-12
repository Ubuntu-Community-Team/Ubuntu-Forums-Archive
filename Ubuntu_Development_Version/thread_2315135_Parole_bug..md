---
title: "Parole bug."
date: 2016-02-26
forum: Ubuntu Development Version
---

### Post by mikewhatever on 2016-02-26
I've recently filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1550009"), which was marked as invalid. It says there are no debug symbols for nvidia-304, libfribidi0, libflac8, so I've looked up [DebuggingProgramCrash]("https://wiki.ubuntu.com/DebuggingProgramCrash"), and followed the steps of looking for the appropriate -dbg and -dbgsym packages, adding the "deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) $(lsb_release -cs) main restricted universe multiverse" repository, looking again, but there are no debug packages in the repositories for the above three. The system is, of cause, fully updated (it's Xubuntu 16.04).

The machine in question is an old Pentium 4 with Nvidia GeForce 6200 AGP graphics card and 1.5GB of RAM.

```

$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
	Subsystem: ABIT Computer Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface [147b:1049]
	Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P AGP Bridge [8086:2571] (rev 02)
	Kernel modules: shpchp
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
	Subsystem: ABIT Computer Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI Controller [147b:1049]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
	Subsystem: ABIT Computer Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI Controller [147b:1049]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
	Subsystem: ABIT Computer Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI Controller [147b:1049]
	Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
	Subsystem: ABIT Computer Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI Controller [147b:1049]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
	Subsystem: ABIT Computer Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [147b:1049]
	Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
	Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
	Kernel driver in use: lpc_ich
	Kernel modules: intel_rng, lpc_ich
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
	Subsystem: ABIT Computer Corp. 82801EB/ER (ICH5/ICH5R) IDE Controller [147b:1049]
	Kernel driver in use: ata_piix
	Kernel modules: pata_acpi
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)
	Subsystem: ABIT Computer Corp. 82801EB (ICH5) SATA Controller [147b:1049]
	Kernel driver in use: ata_piix
	Kernel modules: pata_acpi
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
	Subsystem: ABIT Computer Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller [147b:1049]
	Kernel modules: i2c_i801
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
	Subsystem: ABIT Computer Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [147b:1049]
	Kernel driver in use: snd_intel8x0
	Kernel modules: snd_intel8x0
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV44 [GeForce 6200 A-LE] [10de:0222] (rev a1)
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_304
02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: ABIT Computer Corp. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [147b:1049]
	Kernel driver in use: 8139too
	Kernel modules: 8139cp, 8139too

```

Can anyone advise how to proceed.

---

### Post by MikeMecanic on 2016-02-26
By default, video output is not enable in Parole.  You must enable it in settings.

---

### Post by mikewhatever on 2016-02-26
Not sure what you mean by "video output is not enable". It is, and Parole plays videos, but segfaults when I try to skip forward. If you want me to enable something in the setting, please be more specific. ...insanely more specific, compared to the above.

---

### Post by QDR06VV9 on 2016-02-26
> **mikewhatever said:**
> Not sure what you mean by "video output is not enable". It is, and Parole plays videos, but segfaults when I try to skip forward. If you want me to enable something in the setting, please be more specific. ...insanely more specific, compared to the above.
+1

---

### Post by MikeMecanic on 2016-02-26
Well, I'm not on Xubuntu and Parole is not in Ubuntu.  If you can play video, I would say that they fix the bug.  Don't remember exactly where in the settings?

---

### Post by howefield on 2016-02-26
Stock Ubuntu - daily iso fully up to date with Parole installed, plays movies fine without resorting to any settings twiddling.

---

### Post by mc4man on 2016-02-26
Those sources mentioned don't have debug symbols in Ubuntu.
You could try filing a bug directly (ubuntu-bug parole), provide info as to what causes the crash, hardware info & also then mark your current bug as a dupe of new bug.

Locally it seems to be an issue with the volume control when you seek. Maybe try - 
Set parole to use X window system (no Xv) if currently using X window system (X11/XShm/Xv) or if using Clutter than switch to one or the other of the X11
(If not on clutter than I'd advise not trying, may cause empty parole window inc. parole's preferences window.

Also maybe try disabling the mpris2 plugin if it's enabled

Edit; to clarify - does the crash occur while seeking or when closing parole after seeking?

---

### Post by mikewhatever on 2016-02-26
Hey mc4man, I've tried the three video output options, all three worked for playing videos, but segfaulted the second I tried moving the slider forward. Visually, what happens is the playback stops, and the Parole windows closes.
Here is what it looks like, if launched from a terminal window:
```

$ parole test.mp4 

** (parole:3145): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-ELwoGajH7L: Connection refused

(parole:3145): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2149:29: Expected a valid selector
Protocol error: bad 3 (Window); Sequence Number 5
 Opcode (20, 0) = GetProperty
 Bad resource 930383683 (0x37748743)
 at -e line 15.
Segmentation fault (core dumped)

```
Everything before the segfault line appears at launch, disabling mpris2 doesn't seem to have any effect.

I've also tried to install mplayer and gnome-mplayer. Mplayer plays all, and seeks forward and backward without problems. Gnome-mplayer just opens a small window that says 'Loading...' at bottom, and never loads or plays anything. I have to close it after a while.
```

$ gnome-mplayer test.mp4 

** (gnome-mplayer:4432): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-ELwoGajH7L: Connection refused

(gnome-mplayer:4432): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2149:29: Expected a valid selector

(gnome-mplayer:4432): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2149:29: Expected a valid selector
GMLIB-Message: after init: position=0.000 length=0.000 start_time=0.000 run_time=0.000 volume=0.00 player=dead media=unknown uri=
GMLIB-Message: GET not implemented for interface: org.mpris.MediaPlayer2.Playlists property: PlaylistCount

(gnome-mplayer:4432): GLib-CRITICAL **: Source ID 68 was not found when attempting to remove it

(gnome-mplayer:4432): GLib-CRITICAL **: Source ID 69 was not found when attempting to remove it

(gnome-mplayer:4432): GLib-CRITICAL **: Source ID 70 was not found when attempting to remove it

```

PS: Here is a new bug report: [https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1550444](https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1550444)

---

### Post by QDR06VV9 on 2016-02-26
I can confirm...  so far using the Clutter(OpenGL) Video Out-put has worked for me.
Will keep on testing it more though..
Thanks mc4man

---

### Post by mikewhatever on 2016-03-12
Switched from Xubuntu to Ubuntu 16.04 gnome-flashback. Totem segfaults as well, just after opening it.
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1556435](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1556435)

---

### Post by mikewhatever on 2016-03-19
Installed VLC player on Xubuntu, and it doesn't any problems playing or skipping.

---


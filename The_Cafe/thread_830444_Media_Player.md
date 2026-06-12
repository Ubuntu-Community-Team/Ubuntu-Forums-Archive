---
title: "Media Player"
date: 2008-06-15
forum: The Cafe
---

### Post by XTR0RDiNAiRE on 2008-06-15
is there a better nicer looking media player i can download 
on ubuntu, cause this one im using now:(

---

### Post by powerpleb on 2008-06-15
I think the best media player is VLC but as far as appearances go it's pretty basic.

---

### Post by LaRoza on 2008-06-15
> **XTR0RDiNAiRE said:**
> is there a better nicer looking media player i can download 
on ubuntu, cause this one im using now:(

You might want to specify for what you are looking.

The most popular player seems to be VLC, that is what I use.

---

### Post by Mateo on 2008-06-15
linux doesn't really do "media" players all that often.  Even though they are out there, and many players can play both audio and video, they are really "meant" for one or the other.

---

### Post by bobbocanfly on 2008-06-15
Banshee (IMO) is the best music player, which has limited video support. Though, there are dozens of high profile music players on Linux, Amarok is very popular, Audacious + BMP are popular jukebox style music players. 

VLC is best for video (but pretty terrible for music), as it plays *loads* of formats.

---

### Post by init1 on 2008-06-15
I use mplayer
[apt:mplayer]("apt:mplayer")

---

### Post by bufsabre666 on 2008-06-15
eh, i like totem, i use it myself often, but theres not really a "nice" looking media player, they all seem very minimal, which i personally prefer, vlc is very nice and cross platform, totem is pretty basic but it works for all i play

as for audio players i like rhytmbox, i like amarok, i like exaile, but i love banshee

theres not really a one fits all media player like windows media player, but i like it better this way, get 2or 3 programs that do a very good job rather than 1 program that is mediocre

---

### Post by ma_nkooo on 2008-06-15
I use smplayer

---

### Post by RiceMonster on 2008-06-16
Use Gnome MPlayer for videos (a frontend for MPlayer, and a replacement for the annoying default GUI) and Amarok or Exaile for music.

---

### Post by XTR0RDiNAiRE on 2008-06-16
i tried vlc

still laggs alot! when i put it on fullscreen
the files i am playing are avi format

---

### Post by FuturePilot on 2008-06-16
Perhaps it's a graphics driver issue. What graphics card do you have? Did you install any drivers for it? Are you using Compiz?

---

### Post by XTR0RDiNAiRE on 2008-06-16
> **FuturePilot said:**
> Perhaps it's a graphics driver issue. What graphics card do you have? Did you install any drivers for it? Are you using Compiz?

im not sure how to check that stuff
all i know is that with windows i never had that 
problem


:(

---

### Post by bufsabre666 on 2008-06-16
use 
```
lspci -v
```
to tell us what your graphics adapter cause it sounds like you need proprietary drivers

---

### Post by XTR0RDiNAiRE on 2008-06-17
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdd00000-fdefffff
	Prefetchable memory behind bridge: 00000000f8000000-00000000fbffffff
	Capabilities: <access denied>

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at ff00 [size=8]
	I/O ports at fe00 [size=4]
	I/O ports at fd00 [size=8]
	I/O ports at fc00 [size=4]
	I/O ports at fb00 [size=16]
	Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fe029000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: 66MHz, medium devsel
	I/O ports at 0b00 [size=16]
	Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f900 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: fda00000-fdafffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series] (prog-if 00 [VGA controller])
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at f8000000 (64-bit, prefetchable) [size=64M]
	Memory at fdee0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at de00 [size=256]
	Memory at fdd00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at fdefc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 20)
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, fast devsel, latency 0, IRQ 510
	Memory at fdcfc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at ee00 [size=256]
	[virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
	Capabilities: <access denied>

03:01.0 Modem: Motorola SM56 Data Fax Modem (rev 04) (prog-if 00 [Generic])
	Subsystem: Motorola Unknown device 3020
	Flags: bus master, stepping, medium devsel, latency 64, IRQ 21
	Memory at fdbff000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ce00 [size=256]
	Capabilities: <access denied>

03:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: Foxconn International, Inc. Unknown device 0e0a
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at fdbfe000 (32-bit, non-prefetchable) [size=2K]
	Memory at fdbf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

---

### Post by bufsabre666 on 2008-06-17
```
sudo apt-get update && sudo apt-get install envyng-core envyng-gtk
```

applications->system tools-)envyng

install the ati driver

restart

performance should increase quite a bit

---

### Post by billgoldberg on 2008-06-17
VLC or Miro for video,

Bmpx for music (or exaile, depends).

---

### Post by SupaSonic on 2008-06-17
+1 for smplayer.

---

### Post by samjh on 2008-06-17
Desktop video: VLC

Plays pretty much everything correctly, even DVDs with menus and FLV-contained videos.  Versatile when you want to encode or transcode into different formats too.

Browser embedded: mozilla-mplayer

I use mplayer-nogui with mozilla-mplayer for listening/viewing media embedded in web pages.  Works well with most formats.

Audio: Rhythmbox

Personally I don't use this much, but I find it useful for cataloguing collections of audio files.

---

### Post by BreakDecks on 2008-06-17
xine-ui anyone?  That's always my media player of choice.

---

### Post by hessiess on 2008-06-17
get a nvidia card, ATI's drivers are still pritty poor.

---

### Post by damoxc on 2008-06-17
Not long till that will be vica-versa with the opensource ati drivers coming along.

---

### Post by dje on 2008-06-17
rhythmbox (although recently tempted by banshee 1.0) for music and vlc for video

---

### Post by kk0sse54 on 2008-06-18
I used to be an avid Exaile user but when I tried Songbird it just blew me away

---

### Post by Chrysalis on 2008-06-18
Of the gui type audio players pretty much all fail miserably at basic tagging and other features like gapless playback, cue sheet support, replaygain etc and managing more then a few hundred songs at a time is a torture.

Some highlights:
Amarok in KDE - has replaygain (i think) and limited cue sheet support
Exaile in gnome - replaygain
Exaile & xfmedia in xfce - xfmedia is still in its very early stages, but it was the only one that could load all my media at once seamlessly and play it. Takes a little different approach then the rest itunes wannabes so something good could come out of it in the feature.
MPD - best for just loading a huge library and playing all your music in the background seamlessly. Very limited gapless playback with like just lame mp3s (i think, ive never actually got it to work) so at least its getting there unlike the others and no cue sheet support, has replaygain though. Initial set up is tricky and to get the best out of it you need the svn version cause the one in the repos is missing half the features and support for a bunch of media formats.

If i were to rate the above simply on features i think it'll be something like 3-4 out of 10 because as far as i am concerned they are nothing more then mpg123/ogg123 if you can live without the album art and control buttons. I am not sure if gstreamer/xine or the actuall players are to blame here though, but its a sad state however you look at it. The above doesnt apply to MPD, its in its own category and unfair to compare to anything else.

foobar2000/wine - do i need say more? its the perfect audio player, i am so spoiled by it that everything else looks like a side project to toy around with and nothing more but a fat gui on top of a play button. This is the player everyone should be looking up to instead of making an itunes clone after another. Its my single most favorite application of all time and what kept me away from linux for so long.

So basically i use fb2k and MPD with mpc/sonata. Foobar runs pretty nice in wine and mpd the rest of the time for listening in the background. Mplayer for video or if i wanna listen to something real quick from cli.

---


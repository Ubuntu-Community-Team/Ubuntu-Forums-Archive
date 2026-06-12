---
title: "Hammerfall (9636) Setup"
date: 2009-02-20
forum: Ubuntu Studio
---

### Post by tbrooke on 2009-02-20
I have checked numerous threads and I still haven't figured this out. I have the RME Hammerfall 9636. The card does output analog sound through the RME_AEB O using jack. I cannot figure out how to configure the card to change the sample rate and configure spdif.

hdspconf  shows: 

om@Ubuntu:~$ hdspconf

HDSPConf 1.4 - Copyright (C) 2003 Thomas Charbonnel <thomas@undata.org>
This program comes WITH ABSOLUTELY NO WARRANTY
HDSPConf is free software, see the file copying for details

Looking for HDSP cards :
Card 0 : RME Digi9636 (Rev 1.5) at 0xfd000000, irq 16
No Hammerfall DSP card found.

I can load the alsamixer and the amixer output is at the end of this message. 

Am I missing something to get hdspconf running?

Does hdspconf and hdspmixer even work with my card?

How do I change sample rate and configure spdif without hdspconf? 

Tom Brooke 

amixer shows:

tom@Ubuntu:~$ amixer
Simple mixer control 'IEC958 Input Connector',0
 Capabilities: enum
 Items: 'ADAT1' 'Coaxial' 'Internal'
 Item0: 'Internal'
Simple mixer control 'IEC958 Output also on ADAT1',0
 Capabilities: pswitch pswitch-joined
 Playback channels: Mono
 Mono: Playback [off]
Simple mixer control 'IEC958 Sample Rate',0
 Capabilities: volume volume-joined
 Playback channels: Mono
 Capture channels: Mono
 Limits: 0 - 96000
 Mono: 0 [0%]
Simple mixer control 'ADAT1 Input Source',0
 Capabilities: enum
 Items: 'ADAT1' 'Internal'
 Item0: 'ADAT1'
Simple mixer control 'ADAT1 Sync Check',0
 Capabilities: enum
 Items: 'No Lock' 'Lock' 'No Lock Sync' 'Lock Sync'
 Item0: 'No Lock'
Simple mixer control 'ADAT2 Sync Check',0
 Capabilities: enum
 Items: 'No Lock' 'Lock' 'No Lock Sync' 'Lock Sync'
 Item0: 'No Lock'
Simple mixer control 'Channels Thru',0
 Capabilities: pswitch
 Playback channels: Front Left - Front Right - Rear Left - Rear Right
- Front Center - Woofer - Side Left - Side Right - Rear Center - ? - ?
- ? - ? - ? - ? - ? - ? - ?
 Mono:
 Front Left: Playback [off]
 Front Right: Playback [off]
 Rear Left: Playback [off]
 Rear Right: Playback [off]
 Front Center: Playback [off]
 Woofer: Playback [off]
 Side Left: Playback [off]
 Side Right: Playback [off]
 Rear Center: Playback [off]
 ?: Playback [off]
 ?: Playback [off]
 ?: Playback [off]
 ?: Playback [off]
 ?: Playback [off]
 ?: Playback [off]
 ?: Playback [off]
 ?: Playback [off]
 ?: Playback [off]
Simple mixer control 'Passthru',0
 Capabilities: pswitch pswitch-joined
 Playback channels: Mono
 Mono: Playback [off]
Simple mixer control 'Preferred Sync Source',0
 Capabilities: enum
 Items: 'IEC958 In' 'ADAT1 In' 'ADAT2 In'
 Item0: 'ADAT1 In'
Simple mixer control 'Sync Mode',0
 Capabilities: enum
 Items: 'AutoSync' 'Master' 'Word Clock'
 Item0: 'AutoSync'
Simple mixer control 'Timecode Valid',0
 Capabilities: pswitch pswitch-joined
 Playback channels: Mono

---


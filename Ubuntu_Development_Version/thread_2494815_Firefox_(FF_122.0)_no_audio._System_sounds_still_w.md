---
title: "Firefox (FF 122.0) no audio. System sounds still works."
date: 2024-01-27
forum: Ubuntu Development Version
---

### Post by Smask on 2024-01-27
I can't get sound from Firefox after latest reboot. Tried fiddling with pavucontrol with no luck. There are some entries in the log file in the Security section:

Sender: Isolated Web Co
Message: Child 3949, MediaDecoderStateMachine #2] WARNING: Decoder=7df061204000 [OnMediaSinkAudioError]: file /build/firefox/parts/firefox/build/dom/media/MediaDecoderStateMachine.cpp:4650

Sender: wireplumber
Message: <WpSiAudioAdapter:0x5b0b56a8f110> tried to link on last rescan, not retrying 

(This message is repeated several times. And as the log file browser seems to be buggy at the moment, I won't delve deeper into this.)

---

### Post by jbicha on 2024-01-29
This is likely a duplicate of [https://ubuntuforums.org/showthread.php?t=2494753](https://ubuntuforums.org/showthread.php?t=2494753)

---


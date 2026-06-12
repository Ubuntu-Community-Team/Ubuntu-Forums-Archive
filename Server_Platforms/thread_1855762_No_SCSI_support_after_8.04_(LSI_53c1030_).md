---
title: "No SCSI support after 8.04 (LSI 53c1030 )"
date: 2011-10-06
forum: Server Platforms
---

### Post by JackRabid on 2011-10-06
The Situation:

Machine: _IBM eServer xSeries 225_
OS: _Ubuntu Server_
SCSI controller: _LSI Logic / Symbios Logic) 53c1030 Fusion-MPT Ultra320_


The Problem: OS installs fine under 8.04 LTS but the versions on my old (but newer than) discs fail during install.

As I was initially trying to install one of the installers made it as far as telling me that it was unable to identify any hard drives and presented me with a list to choose from. Looked around the internet, tried a couple from the list (IBM Linux driver is named 'mptscsi' the list had 'mptscsih' so I tried it, etc.) when that didn't work I tried a 6.06 disc I had and it worked... So I tried a 9.10... and it worked too but isn't an LTS... So I made a new 8.04 LTS and tried upgrading to 10.04... and wasn't surprised when I was greeted by flashing lights on my keyboard.

So... I've spent all day looking for possible solutions and still being at a loss I've done a fresh 8.04 so I can move on for the time being...

My question... Is there something that *I* am doing wrong? I'm new to SCSI so it could be because I'm doing things out of order or maybe totally missing a step. After I post this I'll probably look into updating BIOS's and such.

Anyone know of anything else I may be missing? Was the 53c1030 driver support pulled for some reason? I tried the bug tracker but LaunchPad is bugged with FireFox7.... 

Suggestions? HELP?!?! (please?)

---


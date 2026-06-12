---
title: "Server crash troubleshoot help request"
date: 2011-03-08
forum: Server Platforms
---

### Post by Pro_D on 2011-03-08
Currently running Ubuntu 10.04 server.
History:
Originally 9.04 x64 server.
Added desktop on top for related programs and VNC viewer sessions.
Originally 2 GB ram, later added 2 more (4 total).
Found out motherboard has issue with more than roughly 3 gb ram.
Have run memory tests and the ram shows no errors.

Problem:
Kernel Panic (crash dump on screen, flashing numlock/scroll lock lights).
No logs of the crash present on the hard drive.  Strangely the most recent crashed wiped all my logs - crash happened after midnight and all logs are from today.  I keep forgetting about shift+pgup/down to scroll the terminal, if that works on a kernel panic...

Suspect ram (specifically an odd problem the motherboard has with addressing more than about 3gb even though it's a board that supports 64 bit processors).  Crashes started around the time that added 2 more sticks of ram (only got 1.2 more gigs of addressable ram) and changed mysql to use that extra ram.
Noticed increased stability when I removed 1 stick, system would crash within hours under heavy load, now crashes after a day or so.

Questions:
1 - Is there somewhere else that logs are saved, specifically the crash log?
2 - Is there a way to tell the kernel to limit the ram it will use?  Something simple perhaps like only use 2.9 GB.

---


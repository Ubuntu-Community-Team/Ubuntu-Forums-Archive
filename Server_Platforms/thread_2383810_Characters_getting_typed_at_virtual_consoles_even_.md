---
title: "Characters getting typed at virtual consoles even with no keyboard present. (17.10)"
date: 2018-01-29
forum: Server Platforms
---

### Post by benjamingeiger on 2018-01-29
In a fresh install of Server 17.10, as soon as the new system boots to the virtual console's login prompt, a character gets typed approximately once a second. It echoes as [FONT=lucida console]^@[/FONT] and makes logging into the console effectively impossible. The characters show up even with no keyboard attached to the system.

This does occur in recovery mode, but the typed characters are invisible at the command line.

It does not occur in 16.10 (confirmed) or the 17.10 installer (if memory serves).

Any suggestions on how to troubleshoot? Is this a known issue?

---

### Post by LHammonds on 2018-01-30
> **benjamingeiger said:**
> virtual consoleAny hint as to what your virtual server is and what version?  VirtualBox 5.2.6?  ESXi 6.0.0?  And what is the host system?  Mac OS X, Windows 10, Ubuntu Desktop 16.04?

LHammonds

---

### Post by benjamingeiger on 2018-01-30
"Virtual consoles" are the consoles that show up when you press Ctrl-Alt-F1 through -F6. The OS is running on bare metal.

[https://en.wikipedia.org/wiki/Virtual_console](https://en.wikipedia.org/wiki/Virtual_console)

---

### Post by benjamingeiger on 2018-01-31
I still don't know what is causing the problem, but I found out that the kernel version has something to do with it. The kernel from 17.04 (4.10.x) works. The kernel from 17.10 (4.13.x) fails. An upgraded kernel (4.14.16) works.

So, if anyone else runs into this, try upgrading your kernel.

---


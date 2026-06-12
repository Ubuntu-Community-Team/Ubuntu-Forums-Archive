---
title: "Update to Neon broke Vorta"
date: 2021-06-05
forum: Ubuntu/Debian BASED
---

### Post by timgood on 2021-06-05
Latest update to Neon borked Vorta which was automatically un-installed during update. Attempting to re-install gives errors:

```
Reading state information... Done
Starting pkgProblemResolver with broken count: 1
Starting 2 pkgProblemResolver with broken count: 1
Investigating (0) python3-pyqt5:amd64 < 5.15.4+dfsg-1+20.04+focal+unstable+build20 @ii mK Ib >
Broken python3-pyqt5:amd64 Breaks on python3-pyqt5.qsci:amd64 < none -> 2.11.2+dfsg-6 @un uN > (< 2.11.5~)
  Considering python3-pyqt5.qsci:amd64 -1 as a solution to python3-pyqt5:amd64 4
  Added python3-pyqt5.qsci:amd64 to the remove list
  Fixing python3-pyqt5:amd64 via keep of python3-pyqt5.qsci:amd64
Investigating (1) vorta:amd64 < none -> 0.7.4-0ubuntu0ppa2 @un puN Ib >
Broken vorta:amd64 Depends on python3-pyqt5.qsci:amd64 < none | 2.11.2+dfsg-6 @un uH >
  Considering python3-pyqt5.qsci:amd64 -1 as a solution to vorta:amd64 9999
  Re-Instated python3-pyqt5.qsci:amd64
Investigating (1) python3-pyqt5:amd64 < 5.15.4+dfsg-1+20.04+focal+unstable+build20 @ii mK Ib >
Broken python3-pyqt5:amd64 Breaks on python3-pyqt5.qsci:amd64 < none -> 2.11.2+dfsg-6 @un uN > (< 2.11.5~)
  Considering python3-pyqt5.qsci:amd64 -1 as a solution to python3-pyqt5:amd64 4
  Added python3-pyqt5.qsci:amd64 to the remove list
  Fixing python3-pyqt5:amd64 via keep of python3-pyqt5.qsci:amd64
Investigating (2) vorta:amd64 < none -> 0.7.4-0ubuntu0ppa2 @un puN Ib >
Broken vorta:amd64 Depends on python3-pyqt5.qsci:amd64 < none | 2.11.2+dfsg-6 @un uH >
  Considering python3-pyqt5.qsci:amd64 -1 as a solution to vorta:amd64 9999
Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 vorta : Depends: python3-pyqt5.qsci but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

System:

Operating System: KDE neon 5.21
KDE Plasma Version: 5.21.5
KDE Frameworks Version: 5.82.0
Qt Version: 5.15.3
Kernel Version: 5.4.0-74-generic
OS Type: 64-bit
Graphics Platform: X11
Processors: 8 × AMD FX(tm)-8150 Eight-Core Processor
Memory: 15.6 GiB of RAM
Graphics Processor: GeForce GT 1030/PCIe/SSE2

Ideas gratefully accepted.

---

### Post by timgood on 2021-06-05
Problem solved - Vorta ppa is no longer updated. Installed flatpak version and it's now working fine.

---


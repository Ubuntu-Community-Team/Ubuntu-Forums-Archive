---
title: "wachandler through wine"
date: 2010-09-05
forum: Wine
---

### Post by m3t3ors on 2010-09-05
i used wachandler on windows for my wireless hifi and am trying to get it running under ubuntu, ive followed the step acoording to wachandler website but keep getting an error
ive saved the bug report in case anyone can help sort this error for me



BUG REPORT AS FOLLOWS

date/time         : 2010-09-06, 01:54:19, 641ms

computer name     : john

user name         : john <admin>

operating system  : Windows XP Service Pack 3 build 2600

system language   : English

system up time    : 4 minutes 20 seconds

program up time   : 1 second

physical memory   : 324/488 MB (free/total)

free disk space   : (C:) 46.99 GB (Z:) 46.99 GB

display mode      : 1024x768, 32 bit

process id        : $31

allocated memory  : 18.32 MB

executable        : WACHandler.exe

exec. date/time   : 2010-01-04 21:54

version           : 2.2.52.186

compiled with     : BCB5

madExcept version : 3.0e

callstack crc     : $c8fbbd2c, $a2ab2ef7, $90f26d93

contact name      : john

contact email     : [email]

exception number  : 1

exception class   : EAccessViolation

exception message : EAccessViolation.



main thread ($33):

687934b5 comctl32.dll    ImageList_GetIconSize

007cc674 WACHandler.exe  __startup



thread $b (MTTrackScanner): <suspended>

68000832 ???

>> created by main thread ($33) at:

005677d7 WACHandler.exe mttrackscanner.cpp 14 MTTrackScanner.Create



thread $42: <priority:1>

68000830 ???

0062ad71 WACHandler.exe Madexcept _17174

0062addb WACHandler.exe Madexcept _17175

>> created by main thread ($33) at:

1b003481 msjet40.dll



thread $44: <priority:1>

68000830 ???

0062ad71 WACHandler.exe Madexcept _17174

0062addb WACHandler.exe Madexcept _17175

>> created by main thread ($33) at:

1b003481 msjet40.dll



thread $47: <priority:1>

68000830 ???

0062ad71 WACHandler.exe Madexcept _17174

0062addb WACHandler.exe Madexcept _17175

>> created by main thread ($33) at:

1b003481 msjet40.dll



thread $21:

68000830 ???

0062ad71 WACHandler.exe Madexcept _17174

0062addb WACHandler.exe Madexcept _17175

>> created by main thread ($33) at:

69a2201f mtxdm.dll



thread $25 (TDummyThread): <suspended>

68000832 ???

>> created by main thread ($33) at:

0077b18c WACHandler.exe gifimage 12417 initialization



hope someone can help me

---

### Post by m3t3ors on 2010-09-06
anyone got philips streamium wac7000 software to run under wine or the wachandler

---


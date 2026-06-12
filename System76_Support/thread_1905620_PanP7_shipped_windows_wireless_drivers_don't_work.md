---
title: "PanP7 shipped windows wireless drivers don't work"
date: 2012-01-07
forum: System76 Support
---

### Post by hamstap85 on 2012-01-07
Unfortunately, I need to start doing things with a computer that Linux just isn't cut out for, and I need Windows. I looked on the knowledge76 panp7 page for the drivers, but those links didn't work. The base URL path worked, though, and it had a list of other drivers that worked wonderfully, except for wireless which were:
09a-default_wireless-panp7.exe
09b-intel_wireless-panp7.exe

The original broken link was Intel so I decided to go with Intel. It extracted to this:
x64/
x86/
x64/dpinst64.exe
x64/iProDifX.dll
x64/iProDifX.exe
x64/NETw5v64.cat
x64/NETw5v64.inf
x64/NETw5v64.sys
and the same files under x86/ just numbered 32 instead of 64

Neither exe does anything. Did anyone else have the same problem?

---

### Post by Noah0504 on 2012-01-08
You should be able to go to the Intel website and have the driver needed automatically detected by the site.  If it's a Intel wireless card anyway.  I have a PanP6, so I don't know if some of the hardware is the same or not.  And if you're installing Windows 7, most of the hardware should be detected and can be installed through Windows Update.

---

### Post by isantop on 2012-01-09
Do you know which wireless card you ordered? It may be that you actually have the default card, and not the Intel one.

EDIT: By the way, I've fixed the knowledge base article and the driver links are all up to date now.

---

### Post by hamstap85 on 2012-01-10
Thanks for that.

And I apologize for completely neglecting to say that I solved it. I saw the vendor id (8086) and device id (422b), ran a search on pcidatabase.com and found the drivers. Thanks for replying anyway.

---


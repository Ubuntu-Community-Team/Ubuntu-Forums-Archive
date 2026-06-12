---
title: "Garmin POI Loader - stopped working"
date: 2010-06-05
forum: Wine
---

### Post by rijidij on 2010-06-05
Hello all,

I had Garmin POI Loader working perfectly under Wine on Karmic.
I upgraded to Lucid not long after release, but have only just now got around to upgrading Wine and POI Loader.
Installation appeared to go fine, but the application will not run. When I try to launch POI Loader a blank screen comes up briefly then disappears without any error message.

Version numbers are:
POI Loader for Windows 2.5.4
Wine: 1.2-rc2 (I have also tried v1.1.38 )
Ubuntu: 10.04 LTS
Kernel: Linux 2.6.32-22-generic

Ubuntu was a fresh install (except for /home) on my EeePC901
I renamed ~/.wine to ~/.wine_old before installing Wine and PIO Loader.

Can anybody shed some light on this problem please?


TIA,
Craig

---

### Post by rijidij on 2010-06-06
OK. This has already been reported as a bug. [#22544]("http://bugs.winehq.org/show_bug.cgi?id=22544")
(and apparently closed, as a duplicate)

I don't really understand the regression testing/patching/unpatching procedure. Nor do I have the time to get involved at the moment.
However, I can confirm that rolling back to v1.1.28 of Wine fixes this particular problem with POI Loader.

---

### Post by rijidij on 2010-06-07
I may have spoken too soon.
Although POI Loader will now launch, I had to go back to version 1.0.1 of Wine (via Synaptic) before it would recognise my SatNav on a USB port.

Oh well. :rolleyes:

---


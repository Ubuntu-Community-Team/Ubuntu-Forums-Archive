---
title: "Will the next Ubuntu DVD include an up-to-date Memtest86+?"
date: 2014-11-02
forum: Ubuntu Development Version
---

### Post by MIJ-VI on 2014-11-02
The version of Memtest86+ (ver. 4.20 IIRC) included on the Ubuntu 14.10 Desktop Live DVD won't properly recognized an FX-8350 (first marketed in Oct. 2012 I believe) running on a 2011-era Asus M5A88-V EVO (BIOS 1801).

The current version of Memtest86+, Memtest86+ V5.01 (27/09/2013) does:

> New Features 
            Added support for up to 2 TB of RAM on X64 CPUs 
            Added experimental SMT support up to 32 cores (Press F2 to enable at startup) 
            Added complete detection for memory controllers 
            Added Motherboard Manufacturer & Model reporting 
            Added CPU temperature reporting 
            Added enhanced Fail Safe Mode (Press F1 at startup) 
            Added support for Intel "Sandy Bridge-E" CPUs 
            Added support for Intel "Ivy Bridge" CPUs 
            Added preliminary support for Intel "Haswell" CPUs (Core 4th Gen) 
            Added preliminary support for Intel "Haswell-ULT" CPUs 
            Added support for AMD "Kabini" (K16) CPUs 
            Added support for AMD "Bulldozer" CPUs 
            Added support for AMD "Trinity" CPUs 
            Added support for AMD E-/C-/G-/Z- "Bobcat" CPUs 
            Added support for Intel Atom "Pineview" CPUs 
            Added support for Intel Atom "Cedar Trail" CPUs 
            Added SPD detection on most AMD Chipsets 
         
Bug Fixes    
            Enforced Coreboot support 
            Optimized run time for faster memory error detection 
            Rewriten lots of memory timings detection cod 
            Corrected bugs, bugs and more bugs (some could remain)

Memtest86+ - Advanced Memory Diagnostic Tool 
[http://www.memtest.org/](http://www.memtest.org/)

Thank you.

---

### Post by cariboo on 2014-11-03
We should see memtest86+ (5.01-2), in vivid, as that's the version that is in Debian unstable, which Vivid is based on.

---

### Post by MIJ-VI on 2014-11-03
:)

---


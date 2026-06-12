---
title: "cannot enable S.M.A.R.T"
date: 2011-06-17
forum: Server Platforms
---

### Post by lister171254 on 2011-06-17
I've just added another drive and while the device has SMART capability I cannot enable it.

>> sudo smartctl -i /dev/sdd1 

----------------------------------
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WCAZA4779401
Firmware Version: 0953
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Jun 17 23:44:13 2011 EST
SMART support is: Available - device has SMART capability.
SMART support is: Disabled
--------------------------------------------

Enabling SMART produces no errors

>> sudo smartctl --smart=on --saveauto=on  /dev/sdd1
------------------------------------------
=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.
SMART Attribute Autosave Enabled.
------------------------------------------

But getting info again, shows that SMART support is still disabled
-------------------------------------
=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WCAZA4779401
Firmware Version: 0953
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Jun 17 23:47:34 2011 EST
SMART support is: Available - device has SMART capability.
SMART support is: Disabled
--------------------------------------------------

I have another Western Digital drive that has been previously enabled without any problems
--------------------------------------------------
=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WCAZA6065523
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Jun 17 23:49:05 2011 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
--------------------------------------------

Appreciate any suggestions.

---

### Post by gordintoronto on 2011-06-17
sdd1 is not a device, sdd is a device. I don't know if it makes any difference.

---

### Post by lister171254 on 2011-06-17
Yor are of course correct, but "sudo smartctl --smart=on --saveauto=on  /dev/sdd" produces no errors, but still does not enable SMART

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WCAZA4779401
Firmware Version: 0953
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Jun 18 10:33:47 2011 EST
SMART support is: Available - device has SMART capability.
SMART support is: Disabled

--------------

Given that the disks that are enabled are the same (Manufactures, capacity, etc) as the new one that I have the problem with, the only difference I can see is the the AT Version for the disks that are enable is 8, while the new one is 7. Other than that they look identical.

Following is one that is enabled

---------------------
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WCAZA6054113
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Jun 18 10:31:00 2011 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
-------------------------------

---

### Post by lister171254 on 2011-07-06
The drive was plugged into a different controller to the others. That controller also reported the incorrect revision number. I've raised this with the SMART group.

---


---
title: "dell poweredge 2600 wake on lan"
date: 2012-07-22
forum: Server Platforms
---

### Post by jldoll on 2012-07-22
I have a dell poweredge 2600.  I've configured the nic card for wol per dell support site.  I've used ethtool to confirm wol g. If I pull the power cord from the server, and restore it;  or I go to standby using the power switch, I can resume with <wakeonlan -p1 macaddress>.  If I try any system command (pm-suspend, pm-hibernate, shutdown, or poweroff) to shut the server down I cannot wake it.  It there a different command that would more accurately emulate going to standby with the power switch?

---

### Post by jldoll on 2012-07-23
***UPDATE****
Realized that wol only works from power switch if os has never been loaded.  I was hasty in my testing and cycling the switch for standby before os was getting fully loaded. So wol only works once after a power loss (assuming system is allowed to fully start-up).

---

### Post by jldoll on 2012-07-25
***UPDATE***
Wondering if anyone may have any suggestions based on the following more detailed info:

According to dell wol documentation, my card should support wol.
I don't really have any bios settings.  There is a dell utility that runs from a boot disk to modify nic firmware.  This is how I got wol to work in "out of box" mode (after power loss).  By running that utility the card should be set to wol g by default.  This appears to be true based on ethtool feedback.  I tried issuing the ethtool eth0 wol g command anyway, and tried putting in rc.local per many other posts. If I look in the /sys files eth0 appears to be enabled for eth0 by default.  If look into /proc files no pci devices are enabled by default. I enabled all of them for testing no luck.  Upon further review none of pci devices actually have the address of the ethernet controller per lspci. I think acpi is working in general because I can sleep and wake the server using rtcwake.  Any suggestions as to why ethtool thinks wol is supported, but my card address is not in the acpi wakeup file.  Is there a way to the card to the acpi wakeup file?

---

### Post by jldoll on 2012-11-05
***UPDATE***
Decided to revisit after using rtcwake for months.  Don't recall if I tried this previously, but it works now with no additional changes other than standard updates.

shutdown -P now

I believe I had always been using "shutdown -h now" or some variant of halt directly.

---


---
title: "AppArmor is denying i2p after upgrade to 15.04"
date: 2015-05-18
forum: Security
---

### Post by welefort on 2015-05-18
Just upgraded from 14.04 to 15.04.  Before the upgrade i2p was working correctly but after the upgrade is unable to start.

The syslog message is 

```
audit: type=1400 audit(1431955956.998:62): apparmor="DENIED" operation="open" profile="/usr/bin/i2prouter" name="/usr/share/java/jayatanaag.jar" pid=23446 comm="java" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```

I realize that apparmor is stopping it,  but I dont know enough about to allow it.

If it helps here is the output of aa-status.
```
sudo aa-status
apparmor module is loaded.
26 profiles are loaded.
26 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/bin/i2prouter
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/lib/telepathy/mission-control-5
   /usr/lib/telepathy/telepathy-*
   /usr/lib/telepathy/telepathy-*//pxgsettings
   /usr/lib/telepathy/telepathy-*//sanitized_helper
   /usr/lib/telepathy/telepathy-ofono
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
   system_i2p
   system_tor
0 profiles are in complain mode.
7 processes have profiles defined.
7 processes are in enforce mode.
   /usr/lib/telepathy/mission-control-5 (17507) 
   /usr/lib/telepathy/mission-control-5 (20270) 
   /usr/sbin/cups-browsed (2832) 
   /usr/sbin/cupsd (29010) 
   /usr/sbin/cupsd (29024) 
   /usr/sbin/ntpd (4307) 
   system_tor (28419) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
```

---


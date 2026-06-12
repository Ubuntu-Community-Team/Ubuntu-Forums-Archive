---
title: "apparmor profile_replace problem"
date: 2013-08-18
forum: Security
---

### Post by kmand on 2013-08-18
I'm running Ubuntu 13.04 and take all updates. Somewhere around August 7 mysql stopped working and now I see several errors when apparmor starts, log at the end of the posting. This seems to be more than a mysql issue since its complaining about several commands. I did see a posting about mysql suggesting that the /var/run lines in the apparmor config for mysql needed to be replaced by /run. I actually had both, but deleting the /var/run's didn't help.

Suggestions?


```
Aug 18 11:51:59 orac kernel: [156414.971530] type=1400 audit(1376841119.883:87): apparmor="STATUS" operation="profile_replace" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1293 comm="apparmor_parser"
Aug 18 11:51:59 orac kernel: [156414.971714] type=1400 audit(1376841119.883:88): apparmor="STATUS" operation="profile_replace" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1293 comm="apparmor_parser"
Aug 18 11:51:59 orac kernel: [156415.007751] type=1400 audit(1376841119.919:89): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1295 comm="apparmor_parser"
Aug 18 11:51:59 orac kernel: [156415.007839] type=1400 audit(1376841119.919:90): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1295 comm="apparmor_parser"
Aug 18 11:51:59 orac kernel: [156415.007890] type=1400 audit(1376841119.919:91): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1295 comm="apparmor_parser"
Aug 18 11:51:59 orac kernel: [156415.041185] type=1400 audit(1376841119.951:92): apparmor="STATUS" operation="profile_replace" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1294 comm="apparmor_parser"
Aug 18 11:51:59 orac kernel: [156415.041461] type=1400 audit(1376841119.951:93): apparmor="STATUS" operation="profile_replace" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1294 comm="apparmor_parser"
Aug 18 11:52:00 orac kernel: [156415.098470] type=1400 audit(1376841120.011:94): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1302 comm="apparmor_parser"
```

---

### Post by kmand on 2013-09-02
It turns out that it was not really an apparmor problem. Some sort of problem with mysql itself must have occured during one of the patches/updates. A reinstall of mysql fixed it.

---


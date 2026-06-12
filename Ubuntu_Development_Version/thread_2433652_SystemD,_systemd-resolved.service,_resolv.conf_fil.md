---
title: "SystemD, systemd-resolved.service, resolv.conf file with „options edns0“"
date: 2019-12-23
forum: Ubuntu Development Version
---

### Post by zika on 2019-12-23
If You use **systemd-resolved.service** have sudden network slowdowns or similar problems You migh have trouble with ```
options edns0
```that turns on [COLOR=#000000][FONT=Ubuntu]Extension Mechanisms for DNS (EDNS(0)) (which does not work nice in many countries) [/FONT][/COLOR]in file */etc/resolv.conf.*  That file is, if You use that service, a symbolic link to file */run/systemd/resolve/stub-resolv.conf *that is session-lasting file. If You want to remove that option for ever, restart-safe, just put **#** in front of that line in file */usr/lib/systemd/resolv.conf *and You're done. Yes, bug is submitted several times for quite a while... It's a shame not to use such a nice service just because of this persistentcy of this-service-developer(s)... This patch I've proposed will work for ou until new upgrade of SystemD and You will have to do it again after it if You wish, if bug persists...


[COLOR=#000000][FONT=Ubuntu]Update&#8321;: [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]*/etc/resolv.conf*[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]  is again updated with unwanted option so the solution, even though edited file is intact , now, is to rename symbolic link file and create new (immutable bit set) [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]*/etc/resolv.conf*[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]  containing[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]Code:

nameserver 127.0.0.53
[/FONT][/COLOR]
[URL="http://forum.ubuntu-rs.org/Thread-ubuntu-20-04-systemd-mreza-resolv-conf-edns0"]
http://forum.ubuntu-rs.org/Thread-ubuntu-20-04-systemd-mreza-resolv-conf-edns0[/URL]

---


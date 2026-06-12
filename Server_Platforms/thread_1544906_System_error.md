---
title: "System error"
date: 2010-08-03
forum: Server Platforms
---

### Post by Thyagaraj on 2010-08-03
When I try to use VIM editor to edit any file I'm getting following error on my server.
I'm getting this error before opening and after closing.


E575: viminfo: Illegal starting char in line: buntu5
E575: viminfo: Illegal starting char in line: Depends: netbase, libc6 (>= 2.4), libcap2 (>= 2.10), libssl0.9.8 (>= 0.9.8f-5)
E575: viminfo: Illegal starting char in line: Recommends: lockfile-progs
E575: viminfo: Illegal starting char in line: Conffiles:
E575: viminfo: Illegal starting char in line:  /etc/dhcp3/dhclient-exit-hooks.d/ntpdate 714c145c22765fdfef242d456307e1c4
E575: viminfo: Illegal starting char in line:  /etc/default/ntpdate 39415ec9778476795fdbb832adc43b9b
E575: viminfo: Illegal starting char in line:  /etc/logcheck/ignore.d.server/ntpdate 68d4df7cceb0e97bde87126c3a56b219
E575: viminfo: Illegal starting char in line:  /etc/network/if-up.d/ntpdate 3a5fa4e3ba54c145e090dbcb40a012a4
E575: viminfo: Illegal starting char in line: Description: client for setting system time from NTP servers
E575: viminfo: Illegal starting char in line:  NTP, the Network Time Protocol, is used to keep computer clocks
E136: viminfo: Too many errors, skipping rest of file


please need help...

---

### Post by ruffEdgz on 2010-08-03
Google is a wonderful thing :D

[http://www.karakas-online.de/forum/viewtopic.php?t=656](http://www.karakas-online.de/forum/viewtopic.php?t=656)

Solution: Delete your ~/.viminfo file and you should be good to go. If this solves your problem, please mark this post as "Resolved".

---

### Post by Thyagaraj on 2010-08-03
Thanks a lot!. It's resolved

---


---
title: "Server wireless only works on network service restart"
date: 2013-01-28
forum: Server Platforms
---

### Post by ptn107 on 2013-01-28
So I have a test server running Raring Ringtail x86_64.  It is [temporarily] configured to connect to my wireless network for internet access (I know it's not hard-wired, so sue me).  Only when it is officially released and running perfectly will I consider replacing my production server with it.  Anyway...

I didn't need any special drivers for wireless to work or anything.  All I had to do was manually edit /etc/network/interfaces a little (wpa-ssid, wpa-psk..., blah blah) so it could connect with a WPA2 64bit key.  The problem is that after a server restart, wireless will only work after I log in and do a 'sudo service networking restart'.  Shouldn't it just start working outright?  After the service is restarted it works fine.

I've Googled the hell out of this and can't find any cause for the problem.  All I find are various workarounds.  I did add it to /etc/rc.local but I want a permanent fix.  I can post the contents of /etc/networking/interfaces when I get home if need be.

---

### Post by ptn107 on 2013-01-28
Update: Ok so it's a time issue.  The server works fine w/o logging in or restarting the network service.  It just takes an additional 5 minutes after startup before anything actually happens.

---


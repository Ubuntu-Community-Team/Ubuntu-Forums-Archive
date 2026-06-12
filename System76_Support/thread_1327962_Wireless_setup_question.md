---
title: "Wireless setup question"
date: 2009-11-16
forum: System76 Support
---

### Post by japhyr on 2009-11-16
Hi everyone,

I set up a new router tonight, with wireless g/b/n capablities.  When I set the router to mixed mode, I can connect to it.  When I set the router to n-only, I can no longer connect.  My wife stays connected in either mode on her macbook.

I have a Pangolin panp5 running 9.04, and a Linksys WRT160N.
```
lspci | grep Wireless
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
```

How can I get the Pangolin to connect on n-only mode?

---

### Post by thomasaaron on 2009-11-16
Try running...

sudo apt-get install linux-backports-modules-jaunty

...and rebooting. If that doesn't fix it, respond back and I'll dig deeper into it tomorrow. I'm out of the office today and can't do any testing.

---

### Post by japhyr on 2009-11-17
I tried running that command, and it said the package installed is already the newest version.

When I got home tonight, I could not connect to wireless even with the mixed mode settings that worked last night.  I went out for a couple hours, came back, and I was able to connect in mixed mode.  I switched to n-only, and could not connect.

I wired into the router and removed the security settings, and set the mode to n-only.  I am now connected to wireless on n-only mode with no security.  Tomorrow I will add security again and see if it can stay connected on the n-only mode.

I tried using WPA personal on this router.  Is there a best kind of security to use with ubuntu, with this wireless card, or with this router?  It is a home network in a small town so I'm not too worried about security, but I would like some level of security.

---

### Post by thomasaaron on 2009-11-17
WPA Personal is pretty darn good. Much better than WEP.

---


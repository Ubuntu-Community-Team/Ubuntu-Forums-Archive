---
title: "No wicd after last update mgr update"
date: 2010-03-18
forum: System76 Support
---

### Post by jbraswell on 2010-03-18
I just ran the update at the update manager's prompt. Apparently, it was installing a new kernel version.

Anyway, after I rebooted, I had no networking.  I noticed wicd was running, and it would start either.  Checking out the wicd log, I saw this:

```
wicd is version 1.6.1 426
2010/03/17 23:02:23 :: Traceback (most recent call last):
2010/03/17 23:02:23 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/03/17 23:02:23 ::     main(sys.argv)
2010/03/17 23:02:23 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/03/17 23:02:23 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/03/17 23:02:23 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/03/17 23:02:23 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/03/17 23:02:23 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/03/17 23:02:23 ::     debug=debug)
2010/03/17 23:02:23 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/03/17 23:02:23 ::     self.read(path)
2010/03/17 23:02:23 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/03/17 23:02:23 ::     self._read(fp, filename)
2010/03/17 23:02:23 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/03/17 23:02:23 ::     raise e
2010/03/17 23:02:23 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/03/17 23:02:23 ::  [line 20]: '[]\n'
```

Looking at the referenced conf file, there was indeed a part of empty brackets at the bottom.  I deleted them and tried again, and wicd started up and seems to be working now.  

It seems fine now, but anybody know what the heck caused that?

---

### Post by thomasaaron on 2010-03-18
That's the first time that's been reported around here. But most of our customers use Network Manager -- as not many of them have need for wicd.

---

### Post by HobbitTR on 2010-04-10
> **thomasaaron said:**
> That's the first time that's been reported around here. But most of our customers use Network Manager -- as not many of them have need for wicd.
I had the same problem and I found the solution here:
[http://ubuntuforums.org/showthread.php?t=1243485](http://ubuntuforums.org/showthread.php?t=1243485)

I posted the same solution to several different pleas for help. Hardly the "first time" it has been reported. However, I do not know why for sure it happened to me. My wife has not had a similar problem.

I started using wicd because of the MANY postings of problems with Network Manager, especially the excessive wpa-supplicant polling of the network and subsequent crashes.

---


---
title: "powernap on ubuntu 15.10"
date: 2015-11-28
forum: Server Platforms
---

### Post by akajes on 2015-11-28
it acceptable for 
powernap  2.21-0ubuntu1
when service not start

FIX #1

You can find possible error in **/var/log/powernap.err** like
```
ValueError: invalid literal for int () with base 10.
```
it is due to changes in **/proc/interrupts** format file
resolved as duplicate row in python file **/usr/lib/python2.7/dist-packages/powernap/monitors/ConsoleMonitor.py **row #40 
change 
```
items.pop()
```
to (remember about indents - its must be same - dont use tabs - just duplicate)
```
items.pop()
items.pop()
```

FIX #2

when You start service ang get error
```
Failed to start powernap.service: Unit network.service failed to load: No such file or directory
```

I change some lines in **/lib/systemd/system/powernap.service**
```
Requires=network.service
After=network.service
```
to
```
Requires=networking.service
After=networking.service

```
And add to **service section** - its need for forking type of service
```
RemainAfterExit=yes
```

FIX #3

as default package installed with no autostart at boot of system
to enable autostart You need remove file
[B]/etc/init/powernap.override
[/B]and run **systemctl enable powernap**


Tnx!

---

### Post by selkovjr-s on 2016-06-15
Thank you for the fixes. I had to apply all of the to get powernap to work in 16.04.

---


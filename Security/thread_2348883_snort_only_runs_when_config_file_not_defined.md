---
title: "snort only runs when config file not defined"
date: 2017-01-08
forum: Security
---

### Post by sniper8752 on 2017-01-08
```
pi@raspberrypi:/etc/snort $ sudo nano /etc/snort/snort.confpi@raspberrypi:/etc/snort $ sudo snort -D -c /etc/snort/snort.conf -u snort -g snort
pi@raspberrypi:/etc/snort $ ps aux | grep snort
pi        2862  0.0  0.2   4276  2016 pts/0    S+   18:14   0:00 grep --color=auto snort
pi@raspberrypi:/etc/snort $ sudo snort -D -u snort -g snort                     Spawning daemon child...
My daemon child 2872 lives...
Daemon parent exiting (0)
pi@raspberrypi:/etc/snort $ ps aux | grep snort
snort     2872  0.0  1.2  28228 12140 ?        Ss   18:14   0:00 snort -D -u snort -g snort
pi        2877  0.0  0.2   4276  2020 pts/0    S+   18:14   0:00 grep --color=auto snort

```
I am baffled, and not sure where to go from here, since there is no output.  I even uninstalled by "purge", and re-installed, but this continues to happen....

Also, this happens when I attempt to install:
```
Setting up snort-common (2.9.7.0-3) ...Setting up snort (2.9.7.0-3) ...
Job for snort.service failed. See 'systemctl status snort.service' and 'journalctl -xn' for details.
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing package snort (--configure):
 subprocess installed post-installation script returned error exit status 1
....
pi@raspberrypi:/etc/init.d $ systemctl status snort.service&#9679; snort.service - LSB: Lightweight network intrusion detection system
   Loaded: loaded (/etc/init.d/snort)
   Active: failed (Result: exit-code) since Sun 2017-01-08 18:42:46 EST; 1min 28s ago




```

---

### Post by Habitual on 2017-01-09
looks funny to me. ... around 
```
sudo nano /etc/snort/snort.confpi@raspberrypi:/etc/snort
```

---


---
title: "Transmission issues."
date: 2016-01-21
forum: Ubuntu/Debian BASED
---

### Post by pingaan on 2016-01-21
Hi,


Transmission daemon won’t start. Doesn’t matter where or when I start it but when I run “sudo service /etc/init.d/transmission-daemon start” I get the output:


```
[FAILED] Failed to start Transmission BitTottent Daemon.
See ‘systemctl status transmission-daemon.service’ for details.
```


Running “systemctl status transmission-daemon.service” gives me the output:


```
transmission-daemon.service – Transmission BitTorrent Daemon
Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled)
Active: failed (result: exit-code) since Mon 2016-01-18 21:12:02 UT; 7in ago
Process: 592 ExecStart=/usr/bin/transmission-daemon -f –lo-error (code=exited, status=255)
Main PID: 592 (code=exited, status=255)
```


This is no copy-paste, so there might be a few typing errors..


Is this a permission issue?


Regards.

---

### Post by Nuno_Abreu on 2016-01-22
I'm not sure about it, but it seems it is not a permission issue - if you try to run it as **root**, it will probably give you the same output.

What if you try to run CLI Transmission version? Type this in the Terminal:

```
transmission-cli
```

---

### Post by Yellow Pasque on 2016-01-24
Have you tried looking at the system journal after you fail to start it?
```
journalctl -r
```

---

### Post by pingaan on 2016-02-04
There are no journalfiles present. However "systemctl status transmission-daemon.service" gave me the outcome:

```
&#9679; transmission-daemon.service - Transmission BitTorrent Daemon
   Loaded: loaded (/lib/systemd/system/transmission-daemon.service; enabled)
   Active: failed (Result: exit-code) since Thu 2016-02-04 21:19:55 CET; 2min 51s ago
  Process: 471 ExecStart=/usr/bin/transmission-daemon -f --log-error (code=exited, status=255)
 Main PID: 471 (code=exited, status=255)
```

---

### Post by Vladlenin5000 on 2016-02-04
Does this sound familiar?
[https://www.raspberrypi.org/forums/viewtopic.php?t=18274&p=180533](https://www.raspberrypi.org/forums/viewtopic.php?t=18274&p=180533)

Also please give some more information about the 'environment', i. e., what OS are you running, whether is headless or not and if not, the reason you aren't opening Transmission like any other GUI program... Normal users with any DE don't need to manually start daemons, you know.

---

### Post by pingaan on 2016-02-05
I am running Raspbian. Concerning this matter it makes no difference(?). 

No, it has nothing to do with that. I had a look at [this](http://www.makeuseof.com/tag/how-to-turn-your-raspberry-pi-into-an-always-on-downloading-megalith/) (scroll down to the Transmission part) while setting up my Pi.
I could go with the transmission-gtk, as well. The micro slight difference would be power consumption, I guess, but the problem is actually auto starting the GUI. I don't see how in Raspbian. That's why I chose the daemon instead.

---

### Post by howefield on 2016-02-05
Moved to "*Ubuntu/Debian BASED*" forum.

---


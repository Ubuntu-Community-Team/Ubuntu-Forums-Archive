---
title: "commands on /etc/rc.local"
date: 2016-02-27
forum: Ubuntu Development Version
---

### Post by leofzky on 2016-02-27
I'm using ubuntu 16.04 beta and commands on /etc/rc.local are not running at boot anymore, is there a new config file for that?

thanks

---

### Post by TheFu on 2016-02-27
Welcome to systemd.


[https://unix.stackexchange.com/questions/47695/how-to-write-startup-script-for-systemd](https://unix.stackexchange.com/questions/47695/how-to-write-startup-script-for-systemd)

---

### Post by springshades on 2016-05-09
I'll answer this in a few places because it's useful information and not terribly easy to find right now. Ubuntu is now using systemd, and rc.local is now considered a service which is turned "off" by default. You can turn rc.local "on" by entering the following command and rebooting:

sudo systemctl enable rc-local.service

---

### Post by cariboo on 2016-05-09
Thread closed.

---


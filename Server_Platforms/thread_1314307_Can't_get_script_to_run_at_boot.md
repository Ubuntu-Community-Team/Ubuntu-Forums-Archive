---
title: "Can't get script to run at boot"
date: 2009-11-04
forum: Server Platforms
---

### Post by trobrock on 2009-11-04
I am trying to get snort to run with the command "snort -c /etc/snort/snort.conf -i eth0 -D" at boot up on my 9.04 server. I have added it to the rc.local file and after boot i try "ps aux | grep snort" and dont find it running, I have also tried adding "@reboot snort -c /etc/snort/snort.conf -i eth0 -D" to my crontab and it still will not run, what am I missing?

---

### Post by karlson on 2009-11-04
> **trobrock said:**
> I am trying to get snort to run with the command "snort -c /etc/snort/snort.conf -i eth0 -D" at boot up on my 9.04 server. I have added it to the rc.local file and after boot i try "ps aux | grep snort" and dont find it running, I have also tried adding "@reboot snort -c /etc/snort/snort.conf -i eth0 -D" to my crontab and it still will not run, what am I missing?

SNORT or /var/log/daemon.log or /var/log/dmesg or /var/log/messages?

Do they tell you anything?

---

### Post by cdenley on 2009-11-04
You probably don't have the PATH variable set, so it doesn't know where to look for the "snort" command.

---

### Post by trobrock on 2009-11-04
I could not find anything in the logs that referred to the start up of snort during boot, also the path should be fine as I can run the snort command from and location on my machine and it works fine, just not from any of the startup scripts

---

### Post by cdenley on 2009-11-04
> **trobrock said:**
> I could not find anything in the logs that referred to the start up of snort during boot, also the path should be fine as I can run the snort command from and location on my machine and it works fine, just not from any of the startup scripts

Exactly. Startup scripts don't use the same PATH variable as your user's session. I know crontabs don't have PATH defined by default. I would assume rc.local is the same.

---

### Post by trobrock on 2009-11-04
Ahh that did it thanks

---


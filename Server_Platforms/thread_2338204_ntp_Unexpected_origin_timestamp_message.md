---
title: "ntp Unexpected origin timestamp message"
date: 2016-09-25
forum: Server Platforms
---

### Post by lister171254 on 2016-09-25
Running the latest server release and am getting these errors every hour
```
Sep 25 22:55:28 llmail ntpd[1457]: receive: Unexpected origin timestamp from 192.189.54.17
Sep 25 22:55:28 llmail systemd[1]: Time has been changed
Sep 25 22:55:28 llmail ntpd[1457]: receive: Unexpected origin timestamp from 27.124.125.250
Sep 25 22:55:28 llmail systemd[1]: apt-daily.timer: Adding 1h 1min 22.363836s random time.
```

ntp is configured as per [https://help.ubuntu.com/lts/serverguide/NTP.html](https://help.ubuntu.com/lts/serverguide/NTP.html)

Thanks

---

### Post by paulgear on 2016-12-08
At a guess, you have systemd-timesyncd and ntp enabled, and they're conflicting.  Run "systemctl status ntp" and "systemctl status systemd-timesyncd" to check, and if ntp is installed, run "systemctl disable systemd-timesyncd" to turn systemd-timesyncd.  It's an SNTP client which is installed by default, and not needed if you have ntp installed.

---


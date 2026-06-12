---
title: "Clamav: daemon does not start"
date: 2019-09-18
forum: Server Platforms
---

### Post by erotavlas on 2019-09-18
Hi,
I'm using ubuntu server 18.04.3 64 bit with lxde GUI. As usual, I installed clamav (0.100.3+dfsg-0ubuntu0.18.04.1) and clamtk (5.25-1), but the clamav daemon does not start.
```
sudo systemctl status clamav-daemon
&#9679; clamav-daemon.service - Clam AntiVirus userspace daemon
   Loaded: loaded (/lib/systemd/system/clamav-daemon.service; enabled; vendor preset: enabled)
  Drop-In: /etc/systemd/system/clamav-daemon.service.d
           &#9492;&#9472;extend.conf
   Active: inactive (dead)
Condition: start condition failed at Wed 2019-09-18 09:00:52 CEST; 24min ago
           &#9492;&#9472; ConditionPathExistsGlob=/var/lib/clamav/daily.{c[vl]d,inc} was not met
     Docs: man:clamd(8)
           man:clamd.conf(5)
           https://www.clamav.net/documents/
```

Log file is empty: ```
/var/log/clamav/clamav.log.
```
The folder ```
/var/lib/clamav
``` contains main.cvd file. I know that I need to run freshclam before to start the daemon. However, it fails to download daily or main files.
```
Wed Sep 18 09:38:57 2019 -> ClamAV update process started at Wed Sep 18 09:38:57 2019
Wed Sep 18 09:38:57 2019 -> ^Your ClamAV installation is OUTDATED!
Wed Sep 18 09:38:57 2019 -> ^Local version: 0.100.3 Recommended version: 0.101.4
Wed Sep 18 09:38:57 2019 -> DON'T PANIC! Read https://www.clamav.net/documents/upgrading-clamav
Wed Sep 18 09:38:57 2019 -> main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
Wed Sep 18 09:38:57 2019 -> !Can't download daily.cvd from database.clamav.net
Wed Sep 18 09:38:57 2019 -> Giving up on database.clamav.net...
Wed Sep 18 09:38:57 2019 -> Update failed. Your network may be down or none of the mirrors listed in /etc/clamav/freshclam.conf is working. Check https://www.clamav.net/documents/official-mirror-faq for possible reasons.
```
Any idea how to fix it?
Thank you in advance

---

### Post by erotavlas on 2019-09-18
I solved by myself. The issue was related to missing files (daily.cvd, main.cvd) into the folder /var/lib/clamav. I downloaded them via wget and now the clamav daemon works properly.

---

### Post by slickymaster on 2019-09-18
*Thread moved to **Server Platforms**.*

---


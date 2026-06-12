---
title: "The dante service can not be started"
date: 2017-02-01
forum: Ubuntu/Debian BASED
---

### Post by vickers2 on 2017-02-01
I would like to use Raspberry to do a socks5 proxy server, the system is raspbian. :( But can not start the service after installing dante. I need help, thanks!Now I posted some debug.
```
pi@raspberrypi:/lib/systemd/system $ sudo /etc/init.d/danted start [....] Starting danted (via systemctl): danted.serviceJob for danted.service failed. See 'systemctl status danted.service' and 'journalctl -xn' for details.
 failed!





```
```
pi@raspberrypi:/lib/systemd/system $ sudo /etc/init.d/danted start [....] Starting danted (via systemctl): danted.serviceJob for danted.service failed. See 'systemctl status danted.service' and 'journalctl -xn' for details.
 failed!
pi@raspberrypi:/lib/systemd/system $ systemctl status danted.service
&#9679; danted.service - SOCKS (v4 and v5) proxy daemon (danted)
   Loaded: loaded (/lib/systemd/system/danted.service; disabled)
   Active: failed (Result: exit-code) since Wed 2017-02-01 07:06:30 UTC; 44min ago
     Docs: man:danted(8)
           man:danted.conf(5)
  Process: 2821 ExecStart=/usr/sbin/danted -D (code=exited, status=1/FAILURE)
  Process: 2814 ExecStartPre=/bin/sh -c       uid=`sed -n -e "s/[[:space:]]//g" -e "s/#.*//" -e "/^user\.privileged/{s/[^:]*://p;q;}" /etc/danted.conf`;      if [ -n "$uid" ]; then          touch /var/run/danted.pid;          chown $uid /var/run/danted.pid;      fi       (code=exited, status=0/SUCCESS)





```
```
pi@raspberrypi:/lib/systemd/system $ sudo journalctl -xn-- Logs begin at Wed 2017-02-01 06:29:40 UTC, end at Wed 2017-02-01 07:51:50 UTC. --
Feb 01 07:51:45 raspberrypi sudo[3003]: pam_unix(sudo:session): session closed for user root
Feb 01 07:51:48 raspberrypi sudo[3012]: pi : TTY=pts/0 ; PWD=/lib/systemd/system ; USER=root ; COMMAND=/etc/in
Feb 01 07:51:48 raspberrypi sudo[3012]: pam_unix(sudo:session): session opened for user root by pi(uid=0)
Feb 01 07:51:48 raspberrypi systemd[1]: Starting SOCKS (v4 and v5) proxy daemon (danted)...
-- Subject: Unit danted.service has begun with start-up
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit danted.service has begun starting up.
Feb 01 07:51:48 raspberrypi systemd[1]: danted.service: control process exited, code=exited status=1
Feb 01 07:51:48 raspberrypi systemd[1]: Failed to start SOCKS (v4 and v5) proxy daemon (danted).
-- Subject: Unit danted.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit danted.service has failed.
-- 
-- The result is failed.





```
The contents of the configuration file is no problem.

---

### Post by howefield on 2017-02-01
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---


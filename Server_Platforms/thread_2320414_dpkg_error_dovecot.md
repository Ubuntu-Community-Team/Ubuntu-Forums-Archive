---
title: "dpkg error dovecot"
date: 2016-04-13
forum: Server Platforms
---

### Post by Timobrunn on 2016-04-13
I purged dovecot.
Then i wanted to reinstall it but im stuck at this error
```
Job for dovecot.service failed. See "systemctl status dovecot.service" and "journalctl -xe" for details.invoke-rc.d: initscript dovecot, action "restart" failed.
dpkg: error processing package dovecot-core (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 dovecot-core
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

When i try to reconfigure it im getting this

```
Setting up dovecot-core (1:2.2.9-1ubuntu5) ...You already have ssl certs for dovecot.
Job for dovecot.service failed. See "systemctl status dovecot.service" and "journalctl -xe" for details.
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error processing package dovecot-core (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 dovecot-core



```

when im running systemctl status dovecot.service this happens:

```
root@Braver-Scanlation:/etc/rc2.d# systemctl status dovecot.service
&#9679; dovecot.service - LSB: Dovecot init script
   Loaded: loaded (/etc/init.d/dovecot)
   Active: failed (Result: exit-code) since Wed 2016-04-13 17:44:33 EDT; 7min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 11936 ExecStart=/etc/init.d/dovecot start (code=exited, status=1/FAILURE)
   CGroup: /system.slice/dovecot.service
           &#9500;&#9472;20855 /usr/sbin/dovecot -c /etc/dovecot/dovecot.conf
           &#9500;&#9472;20872 dovecot/anvil
           &#9500;&#9472;20873 dovecot/log
           &#9492;&#9472;20876 dovecot/config


Apr 13 17:44:33 Braver-Scanlation dovecot[11941]: master: Error: service(imap-login): listen(*, 993) failed: Address already in use
Apr 13 17:44:33 Braver-Scanlation dovecot[11936]: Error: service(imap-login): listen(::, 993) failed: Address already in use
Apr 13 17:44:33 Braver-Scanlation dovecot[11941]: master: Error: service(imap-login): listen(::, 993) failed: Address already in use
Apr 13 17:44:33 Braver-Scanlation dovecot[11936]: Fatal: Failed to start listeners
Apr 13 17:44:33 Braver-Scanlation dovecot[11941]: master: Fatal: Failed to start listeners
Apr 13 17:44:33 Braver-Scanlation systemd[1]: dovecot.service: control process exited, code=exited status=1
Apr 13 17:44:33 Braver-Scanlation systemd[1]: Failed to start LSB: Dovecot init script.
Apr 13 17:44:33 Braver-Scanlation systemd[1]: Unit dovecot.service entered failed state.
Apr 13 17:44:33 Braver-Scanlation systemd[1]: dovecot.service failed.
Apr 13 17:44:33 Braver-Scanlation dovecot[11936]: ...fail!

```

Im running Ubuntu 15.04 vivid

Hope someone can help me with this

---

### Post by Timobrunn on 2016-04-13
Ok, i restarted the server and now its working :)

---

### Post by astarmathsandphysics on 2017-01-03
Thanks for that. Says running now but have errors because I have not yet configured. That I know how to do. Thanks

---


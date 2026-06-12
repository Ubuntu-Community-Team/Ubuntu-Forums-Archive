---
title: "Smbd service and winbind service won't start"
date: 2019-10-27
forum: Server Platforms
---

### Post by toidi357 on 2019-10-27
Hello I am using Ubuntu Server 18.04.3 and recently I haven't been able to start up Samba and winbind service. It was working before, but now it isn't.

systemctl status winbind.service shows:

inbind.service - Samba Winbind Daemon
   Loaded: loaded (/lib/systemd/system/winbind.service; disabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2019-10-27 18:42:36 PDT; 44s ago
     Docs: man:winbindd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 3255 ExecStart=/usr/sbin/winbindd --foreground --no-process-group $WINBINDOPTIONS (code=exited, status=1/FAIL Main PID: 3255 (code=exited, status=1/FAILURE)


Oct 27 18:42:36 ubuntuserverish systemd[1]: Starting Samba Winbind Daemon...
Oct 27 18:42:36 ubuntuserverish systemd[1]: winbind.service: Main process exited, code=exited, status=1/FAILURE
Oct 27 18:42:36 ubuntuserverish systemd[1]: winbind.service: Failed with result 'exit-code'.
Oct 27 18:42:36 ubuntuserverish systemd[1]: Failed to start Samba Winbind Daemon.

journalctl -xe shows:

The start-up result is RESULT.
Oct 27 18:42:25 ubuntuserverish sudo[2854]:  mubaili : TTY=pts/0 ; PWD=/home/mubaili ; USER=root ; COMMAND=/usr/bin/apt-Oct 27 18:42:25 ubuntuserverish sudo[2854]: pam_unix(sudo:session): session opened for user root by mubaili(uid=0)
Oct 27 18:42:28 ubuntuserverish sudo[2854]: pam_unix(sudo:session): session closed for user root
Oct 27 18:42:30 ubuntuserverish sudo[3124]:  mubaili : TTY=pts/0 ; PWD=/home/mubaili ; USER=root ; COMMAND=/usr/bin/apt-Oct 27 18:42:30 ubuntuserverish sudo[3124]: pam_unix(sudo:session): session opened for user root by mubaili(uid=0)
Oct 27 18:42:35 ubuntuserverish systemd[1]: Reloading.
Oct 27 18:42:36 ubuntuserverish systemd[1]: Reloading.
Oct 27 18:42:36 ubuntuserverish systemd[1]: Starting Samba Winbind Daemon...
-- Subject: Unit winbind.service has begun start-up
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
--
-- Unit winbind.service has begun starting up.
Oct 27 18:42:36 ubuntuserverish systemd[1]: winbind.service: Main process exited, code=exited, status=1/FAILURE
Oct 27 18:42:36 ubuntuserverish systemd[1]: winbind.service: Failed with result 'exit-code'.
Oct 27 18:42:36 ubuntuserverish systemd[1]: Failed to start Samba Winbind Daemon.
-- Subject: Unit winbind.service has failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
--
-- Unit winbind.service has failed.
--
-- The result is RESULT.
Oct 27 18:42:38 ubuntuserverish sudo[3124]: pam_unix(sudo:session): session closed for user root




Any help would be appreciated thanks

---

### Post by wildmanne39 on 2019-10-27
Hello and welcome to the forum.

*Thread moved to **Server Platforms a more appropriate sub-forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---


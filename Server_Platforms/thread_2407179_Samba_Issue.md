---
title: "Samba Issue"
date: 2018-11-30
forum: Server Platforms
---

### Post by zathrusuk on 2018-11-30
Hi I have had Samba working as an ADC for months under 18.04.01, the latest atp update appears to have broken something, (extract below), has anyone got any ideas at a little bit of a loss here

0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.5) ...
Job for smbd.service failed because the control process exited with error code.
See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "restart" failed.
&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2018-11-30 21:43:41 GMT; 14ms ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 1050 ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOPTIONS (code=exited, status=1/FAILURE)
 Main PID: 1050 (code=exited, status=1/FAILURE)

Nov 30 21:43:41 Andromeda systemd[1]: Starting Samba SMB Daemon...
Nov 30 21:43:41 Andromeda smbd[1050]: [2018/11/30 21:43:41.802334,  0] ../source3/smbd/server.c:1815(main)
Nov 30 21:43:41 Andromeda smbd[1050]:   server role = 'active directory domain controller' not compatible with running smbd standalone.
Nov 30 21:43:41 Andromeda smbd[1050]:   You should start 'samba' instead, and it will control starting smbd if required
Nov 30 21:43:41 Andromeda systemd[1]: smbd.service: Main process exited, code=exited, status=1/FAILURE
Nov 30 21:43:41 Andromeda systemd[1]: smbd.service: Failed with result 'exit-code'.
Nov 30 21:43:41 Andromeda systemd[1]: Failed to start Samba SMB Daemon.
dpkg: error processing package samba (--configure):
 installed samba package post-installation script subprocess returned error exit status 1
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by merlinus on 2018-12-05
This happened to me even before the latest updates, and so far have not found a solution.  I have uninstalled, deleted config files, reinstalled, etc. to no avail.  It make take a fresh re-install of 18.04.1 to solve the issue, but I am not ready to do that just yet, especially since it may not solve the problem.

---

### Post by heath-c on 2019-01-25
I found this thread looking for a solution to the same problem, and have since found a fix.

You need to mask and/or disable the non-AD samba services if you are using samba-ad-dc.

```
sudo systemctl mask smbd nmbd winbind

```

---


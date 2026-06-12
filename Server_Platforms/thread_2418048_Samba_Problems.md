---
title: "Samba Problems"
date: 2019-04-30
forum: Server Platforms
---

### Post by wolfzrat on 2019-04-30
nmbd.service - Samba NMB Daemon
   Loaded: loaded (/lib/systemd/system/nmbd.service; enabled; vendor preset: enabled)
   Active: failed (Result: timeout) since Mon 2019-04-29 18:30:23 EDT; 11ms ago
     Docs: man:nmbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 1572 ExecStart=/usr/sbin/nmbd --foreground --no-process-group $NMBDOPTIONS (code=killed, signal=TERM)
 Main PID: 1572 (code=killed, signal=TERM)
   Status: "nmbd: No local IPv4 non-loopback interfaces available, waiting for interface ..."

Apr 29 18:28:53 gameserver systemd[1]: Starting Samba NMB Daemon...
Apr 29 18:28:53 gameserver nmbd[1572]: [2019/04/29 18:28:53.331345,  0] ../lib/util/become_daemon.c:135(daemon_status)
Apr 29 18:28:53 gameserver nmbd[1572]:   STATUS=daemon 'nmbd' : No local IPv4 non-loopback interfaces available, waiting for interface ...NOTE: NetBIOS name resolution is not supported for Internet Protocol Version 6 (IPv6).
Apr 29 18:30:23 gameserver systemd[1]: nmbd.service: Start operation timed out. Terminating.
Apr 29 18:30:23 gameserver systemd[1]: nmbd.service: Failed with result 'timeout'.
Apr 29 18:30:23 gameserver systemd[1]: Failed to start Samba NMB Daemon.
dpkg: error processing package samba (--configure):
 installed samba package post-installation script subprocess returned error exit status 1
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)



This is my problem folks and need help fixing, please advice

Thanks

---

### Post by wolfzrat on 2019-04-30
Nevermind I fixed it! I changed 

this:

interfaces = 127.0.0.0/8 eth0


to this

interfaces = 127.0.0.0/8 eno1

and restarted nmbd & smbd

and it works for me thanks again!

---


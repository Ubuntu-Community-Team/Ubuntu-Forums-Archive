---
title: "Ubuntu: Samba Daemon not starting on bootup"
date: 2018-02-08
forum: Server Platforms
---

### Post by zukran on 2018-02-08
Samba Version: Version 4.3.11-Ubuntu
Ubuntu: 16.04.3 LTS (Desktop)


We installed samba, setup the configs. Tested with testparm everything checks out.
```
[global]        workgroup = workgroup
        server string = Library
        server role = standalone server
        create mask = 0777
        force create mode = 0777
        directory mask = 0777
        force directory mode = 0777
        security = user
        map to guest = bad user
        guest account = libraryuser
        log level = 2
        log file = /var/log/samba/smbd.log.%m
        max log size = 1000
        timestamp logs = yes


[uploads]
        path = /library/pending_uploads
        guest ok = yes
        guest only = yes
        writable = yes


[libraryclient]
        path = /library/client
        guest ok = yes
        guest only = yes
        writable = no



```
 
We checked the log and have the following:

```
[2018/02/08 15:02:43.775938,  1] ../source3/profile/profile_dummy.c:30(set_profile_level)  INFO: Profiling support unavailable in this build.
[2018/02/08 15:02:44.017417,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'smbd' finished starting up and ready to serve connections
[2018/02/08 15:02:44.019606,  1] ../source3/printing/printer_list.c:234(printer_list_get_last_refresh)
  Failed to fetch record!
[2018/02/08 15:02:44.019763,  2] ../source3/smbd/server.c:1009(smbd_parent_loop)
  waiting for connections

```

We look around the web those dont seem to be particularly harmful to the service. How ever when we try to start smbd. With 

```
sudo service smbd start
```

And then when we check the status

```

smbd.service - Samba SMB Daemon
   Loaded: loaded (/etc/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: inactive (dead) since Thu 2018-02-08 15:02:44 PST; 6min ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 1537 ExecStart=/usr/sbin/smbd $SMBDOPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 1537 (code=exited, status=0/SUCCESS)


Feb 08 15:02:43 library_server systemd[1]: Starting Samba SMB Daemon...
Feb 08 15:02:44 library_server smbd[1539]: [2018/02/08 15:02:44.017417,  0] ../lib/util/become_daemon.c:124(daemon_ready)
Feb 08 15:02:44 library_server smbd[1539]:   STATUS=daemon 'smbd' finished starting up and ready to serve connections
Feb 08 15:02:44 library_server systemd[1]: Started Samba SMB Daemon.

```

We can't access it via windows.  If we just enter 
```
sudo smbd

```

It appears to work as normal however we need to initialize it on bootup. 
Anybody have any ideas?

---

### Post by zukran on 2018-02-08
This ended up being an override to the smbd.service found at /etc/systemd/system/smbd.service. Removing the service file(which was customized for 17.04) resolved the issue.

---


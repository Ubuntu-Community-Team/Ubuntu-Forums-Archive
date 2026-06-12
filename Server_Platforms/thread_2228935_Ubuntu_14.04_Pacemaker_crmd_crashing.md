---
title: "Ubuntu 14.04 Pacemaker crmd crashing"
date: 2014-06-10
forum: Server Platforms
---

### Post by babueter on 2014-06-10
I'm just trying to stand up the simplest of clusters and pacemaker is crashing constantly.  Here is my config:

/etc/ha.d/ha.cf
```

autojoin none
use_logd off
logfile /var/log/ha.log
debug 3
bcast eth0
warntime 5
deadtime 15
initdead 60
keepalive 2
node local1
node local2
pacemaker respawn

```

crm configure show xml
```

<?xml version="1.0" ?>
<cib num_updates="0" update-origin="local1" validate-with="pacemaker-1.2" update-client="crmd" epoch="1" admin_epoch="0" cib-last-written="Tue Jun 10 11:40:03 2014">
  <configuration>
    <crm_config/>
    <nodes>
      <node id="b54b998d-88cf-44d0-90db-f3dcdfc330ea" uname="local2"/>
      <node id="7747fedd-a825-4d35-bacc-b45c753f1c02" uname="local1"/>
    </nodes>
    <resources/>
    <constraints/>
  </configuration>
</cib>

```



crm_mon -1
```
Last updated: Tue Jun 10 12:10:23 2014
Last change: Tue Jun 10 11:40:03 2014 via crmd on local1
Current DC: NONE
2 Nodes configured
0 Resources configured




Node local1 (7747fedd-a825-4d35-bacc-b45c753f1c02): UNCLEAN (offline)
Node local2 (b54b998d-88cf-44d0-90db-f3dcdfc330ea): UNCLEAN (offline)

```

The recycling errors in /var/log/ha.log:
```
Jun 10 12:10:10 local1 heartbeat: [1134]: ERROR: Client /usr/lib/heartbeat/crmd (pid=1494) killed by signal 11.
Jun 10 12:10:10 local1 heartbeat: [1134]: ERROR: Respawning client "/usr/lib/heartbeat/crmd":
Jun 10 12:10:10 local1 heartbeat: [1134]: info: Starting child client "/usr/lib/heartbeat/crmd" (107,114)
Jun 10 12:10:10 local1 heartbeat: [1502]: info: Starting "/usr/lib/heartbeat/crmd" as uid 107  gid 114 (pid 1502)
Jun 10 12:10:11 local1 heartbeat: [1134]: info: the send queue length from heartbeat to client crmd is set to 1024
Jun 10 12:10:16 local1 heartbeat: [1134]: WARN: 1 lost packet(s) for [local2] [614:616]
Jun 10 12:10:16 local1 heartbeat: [1134]: info: No pkts missing from local2!
Jun 10 12:11:01 local1 ccm: [1174]: info: client (pid=1502) removed from ccm
Jun 10 12:11:01 local1 heartbeat: [1134]: WARN: Managed /usr/lib/heartbeat/crmd process 1502 killed by signal 11 [SIGSEGV - Segmentation violation].
Jun 10 12:11:01 local1 heartbeat: [1134]: ERROR: Client /usr/lib/heartbeat/crmd (pid=1502) killed by signal 11.
Jun 10 12:11:01 local1 heartbeat: [1134]: ERROR: Respawning client "/usr/lib/heartbeat/crmd":
Jun 10 12:11:01 local1 heartbeat: [1134]: info: Starting child client "/usr/lib/heartbeat/crmd" (107,114)
Jun 10 12:11:01 local1 heartbeat: [1511]: info: Starting "/usr/lib/heartbeat/crmd" as uid 107  gid 114 (pid 1511)
Jun 10 12:11:02 local1 heartbeat: [1134]: info: the send queue length from heartbeat to client crmd is set to 1024

```



Any help would be appreciated.

---

### Post by babueter on 2014-06-23
So the solution was to convert to corosync.  There is probably a bug that should be reported, but at least anyone else having this issue will now know to drop heartbeat and convert now.

---


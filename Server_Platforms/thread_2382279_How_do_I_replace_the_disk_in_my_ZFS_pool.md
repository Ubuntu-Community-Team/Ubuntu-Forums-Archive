---
title: "How do I replace the disk in my ZFS pool?"
date: 2018-01-11
forum: Server Platforms
---

### Post by meulie on 2018-01-11
Hi all,

Current status of my pool:
```
  pool: datastore state: DEGRADED
status: One or more devices could not be used because the label is missing or
        invalid.  Sufficient replicas exist for the pool to continue
        functioning in a degraded state.
action: Replace the device using 'zpool replace'.
   see: http://zfsonlinux.org/msg/ZFS-8000-4J
  scan: scrub repaired 0B in 31h22m with 0 errors on Mon Jan  8 14:09:36 2018
config:


        NAME                      STATE     READ WRITE CKSUM
        datastore                 DEGRADED     0     0     0
          raidz2-0                DEGRADED     0     0     0
            sdc                   ONLINE       0     0     0
            13247575545404309743  FAULTED      0     0     0  was /dev/sdd1
            sdd                   ONLINE       0     0     0
            sde                   ONLINE       0     0     0
            sdf                   ONLINE       0     0     0
        logs
          sdb1                    ONLINE       0     0     0



```

The faulted disk is now identified by the system as sdg. What would be the correct command to replace disk '13247575545404309743' with sdg?

Regards,
  Evert

---

### Post by darkod on 2018-01-11
Are you asking to replace the name that it reports, or replace a faulty disk with a new one?

---

### Post by meulie on 2018-01-11
I want to replace the faulty disk with a new one  :)

I've read the page mentioned, but am not sure whether to use:
[LIST=1]
[*]zpool replace datastore sdd
[*]zpool replace datastore sdg
[*][something else]
[/LIST]

---

### Post by Max303 on 2018-01-11
[COLOR=#000000][FONT=&amp][SIZE=2][FONT=arial]If you are replacing the damaged device with different device, use syntax similar to the following:

[COLOR=#222222]# [/COLOR]**zpool replace datastore sdd sdg**[/FONT][/SIZE][/FONT][/COLOR]
[SIZE=2][FONT=arial]
This command migrates data to the new device from the damaged device or from other devices in the pool if it is in a redundant configuration.

When the command is finished, it detaches the damaged device from the configuration, at which point the device can be removed from the system.

If you have already removed the device and replaced it with a _new device in the same location_, use the single device form of the command. For example:

[/FONT][/SIZE][SIZE=2][FONT=arial]# [B]zpool replace datastore sdd

[/B][/FONT][/SIZE][COLOR=#000000][FONT=&amp][SIZE=2][FONT=arial]This command takes an unformatted disk, formats it appropriately, and then resilvers data from the rest of the configuration.[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by meulie on 2018-01-11
Thanks, that did the trick!  :)

---


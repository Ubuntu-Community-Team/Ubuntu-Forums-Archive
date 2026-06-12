---
title: "Landscape periodic CPU spikes"
date: 2017-05-15
forum: Ubuntu Cloud and Juju
---

### Post by armegeden on 2017-05-15
Hello:

TL;DR:  Running local Landscape server.  CPU spikes to 90-100% every 5 minutes.  This lasts only a few seconds.  Is this working as intended, is there something wrong, or can I adjust the timers?

Detail:
Running a Landscape VM on Ubuntu Server 16.04 on VMWare ESXi 6.5.  Landscape is managing five other Ubuntu Server VMs, all local to the same physical host.

I'm not a nix guru, so I've had to fumble my way around to figure out what could be causing the spike.  I ran across a forum post here that mentioned "dstat -ta --top-cpu" which helped narrow it down:

```
partial output:  dstat -ta --top-cpu
----system---- ----total-cpu-usage---- -dsk/total- -net/total- ---paging-- ---system-- -most-expensive-
     time     |usr sys idl wai hiq siq| read  writ| recv  send|  in   out | int   csw |  cpu process
15-05 14:15:25| 90  10   0   0   0   0|   0    64k|  60B  540B|   0     0 | 603   805 |landscape-pac 97
15-05 14:15:26| 92   8   0   0   0   0|   0    12k| 186B  540B|   0     0 | 607   805 |landscape-pac 98
15-05 14:15:27| 75  25   0   0   0   0|   0     0 |  60B 1460B|   0     0 | 609   787 |landscape-pac 99

```

"htop" helped find this as the probable process:

```
python /opt/canonical/landscape/package-upload --rundir=/opt/canonical/landscape --pidfile=/var/run/landscape/landscape-package-upload-1.pid
```

From here I'm not sure where to go.  I don't know if the clients are set to report in every 5 minutes, or if the server itself it checking for updates, db maintenance, etc.  

Is this normal?  Can I alter the 5 minute timer?  Suggestions?

Thanks for any help

---

### Post by armegeden on 2017-05-16
This is a screenshot of the consistency from an ESXi performance chart perspective.  The blue spikes are the Landscape server.

[IMG]http://www.synthetiq.net/images/landscape_spike.png[/IMG]

---

### Post by armegeden on 2017-05-16
Ended up finding the scheduled task for Landscape in /etc/cron.d/landscape-server

```
# Update Alerts*/5 * * * * landscape ( /opt/canonical/landscape/scripts/update_alerts.sh; /opt/canonical/landscape/scripts/landscape_profiles.sh; /opt/canonical/landscape/scripts/process_alerts.sh )
```

Changed it to every hour, which is fine for my use.

---


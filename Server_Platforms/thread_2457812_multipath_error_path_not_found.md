---
title: "multipath error path not found"
date: 2021-02-10
forum: Server Platforms
---

### Post by pacome.heuze on 2021-02-10
Hi every one !

I installed Ubuntu server 20.04 on a compaq presario CQ60 on a local network, no internet.
I installed shinobi as well.

Because it was overheating I decided to check the server log.
I Found these **multipath error**.

syslog :
```
Jun  6 00:03:43 shinobiserver rsyslogd: [origin software="rsyslogd" swVersion="8.2001.0" x-pid="598" x-info="https://www.rsyslog.com"] rsyslogd was HUPed
Jun  6 00:03:45 shinobiserver systemd[1]: man-db.service: Succeeded.
Jun  6 00:03:45 shinobiserver systemd[1]: Finished Daily man-db regeneration.
Jun  6 00:04:09 shinobiserver multipath: sda: can't store path info
Jun  6 00:04:09 shinobiserver multipath: sda: can't store path info
Jun  6 00:04:09 shinobiserver multipathd[533]: sda: spurious uevent, path not found
Jun  6 00:04:09 shinobiserver multipathd[533]: uevent trigger error
Jun  6 00:04:10 shinobiserver multipathd[533]: sda: spurious uevent, path not found
Jun  6 00:04:10 shinobiserver multipathd[533]: uevent trigger error
Jun  6 00:04:41 shinobiserver systemd-resolved[564]: Using degraded feature set (TCP) for DNS server 192.168.1.1.
Jun  6 00:04:51 shinobiserver systemd-resolved[564]: Using degraded feature set (UDP) for DNS server 192.168.1.1.
Jun  6 00:04:56 shinobiserver systemd-resolved[564]: Using degraded feature set (TCP) for DNS server 192.168.1.1.
Jun  6 00:05:01 shinobiserver multipath: sda: can't store path info
Jun  6 00:05:01 shinobiserver multipathd[533]: sda: spurious uevent, path not found
Jun  6 00:05:01 shinobiserver multipathd[533]: uevent trigger error
Jun  6 00:05:01 shinobiserver multipath: sda: can't store path info
Jun  6 00:05:01 shinobiserver systemd-resolved[564]: Using degraded feature set (UDP) for DNS server 192.168.1.1.
```

Which leads to overheating :
```
Jun  6 00:17:51 shinobiserver kernel: [49884.951600] nouveau 0000:02:00.0: therm: temperature (96 C) hit the 'downclock' threshold
Jun  6 00:17:54 shinobiserver kernel: [49888.269352] nouveau 0000:02:00.0: therm: temperature (92 C) went below the 'downclock' threshold
Jun  6 00:18:02 shinobiserver systemd-resolved[564]: Using degraded feature set (TCP) for DNS server 192.168.1.1.
```

I searched on internet I found this :

[URL="https://access.redhat.com/solutions/2651581"]https://access.redhat.com/solutions/2651581

[/URL]I don't know what to do with this.

Does anybody has a solution ?

Thank you

---

### Post by ameinild on 2021-02-10
I would suggest you edit the file [FONT=courier new]/etc/multipath.conf[/FONT] like this:

```
defaults {
    user_friendly_names yes
} 
blacklist {
    devnode "^(ram|raw|loop|fd|md|dm-|sr|scd|st|sd|mmc|nvme)[a-z0-9]*"
}
```

For me this stopped multipath from monitoring the disks and spamming the syslog.

---


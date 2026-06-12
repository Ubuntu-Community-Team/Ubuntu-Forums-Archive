---
title: "RAID5 access delay after idle"
date: 2023-03-27
forum: Server Platforms
---

### Post by apollo-node on 2023-03-27
I'm currently running Ubuntu Server 22.04.2 LTS and I have a RAID5 array (XFS filesystem, originally created on CentOS using 5 x Seagate IronWolf HDDs).
After not using the server for around 30 mins or more, attempting to read or write files causes a brief lag or soft lockup. 

It's as if the HDDs were parked and are spinning back up. It also doesn't look like any power saving features are on.


This tends to last 10 - 20 seconds after which I can read and write files normally again. Smartctl doesn't seem to indicate anything out of the ordinary that I can see and Cockpit reports all HDDs as OK.


Is there something else I should be checking for or tests I should be running that could indicate a potential bad drive? I don't recall experiencing this when running under CentOS.

---

### Post by MAFoElffen on 2023-03-27
The only things I can think of is if either mdcheck_start.timer or mdcheck_continue.timer are running... Then there might be a lag from those jobs running. 

Before systemd, they used to be cron jobs, but now with systemd, they run as services.

But if that is running, you would see something in the syslog like this:
```

[12294.966072] md: data-check of RAID array md127
[12294.966074] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[12294.966075] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for data-check.
[12294.966077] md: using 128k window, over a total of 2095040k.
[12305.660042] md: md127: data-check done.

```
If not, then I'm out of guesses. LOL

---

### Post by apollo-node on 2023-03-30
Thanks for the suggestion!
I went down the rabbit hole with systemctl to check the mdcheck services and timers and it seems they're all inactive. I very likely killed those some time ago when moving to Ubuntu.

Edit: If anybody else runs into this same issue, I was able to resolve it by using openSeaChest tools from Seagate's Github. It contains a program that specifically controls various power, standby and idle functions that hdparm was unable to change.

---


---
title: "chrony config - samba time synchronization"
date: 2018-06-03
forum: Server Platforms
---

### Post by alexroz on 2018-06-03
I'm running samba 4.7.6 on ubuntu 18.04 as domain controller that joined to an Existing Active Directory (Windows 2012R2 server).
There is an article about [time synchronization]("https://wiki.samba.org/index.php/Time_Synchronisation") at samba wiki. But it isn't describes chrony configuration.
And since chrony become Ubuntu's default NTP server I need some help with chrony v3.2 configuration, in order to provide time sync between:
[LIST]
[*]main Windows DC and Samba DC
[*]Samba DC and windows clients in case then Windows DC is unavailable
[/LIST]

---

### Post by LHammonds on 2018-06-04
chronyd is not installed as default on my 18.04 LTS server which was installed using the "alternative" ISO image.

Make sure your timezone is correct:
```
timedatectl
```

```
# timedatectl
                      Local time: Mon 2018-06-04 09:04:58 CDT
                  Universal time: Mon 2018-06-04 14:04:58 UTC
                        RTC time: Mon 2018-06-04 14:04:59
                       Time zone: America/Chicago (CDT, -0500)
       System clock synchronized: yes
systemd-timesyncd.service active: yes
                 RTC in local TZ: no

```

If the zone is not correct, you will need to find the correct timezone value:
```
timedatectl list-timezones
```

To set the correct timezone, stop the sync, set the time, then re-enable sync:
```
timedatectl set-ntp off
timedatectl set-timezone America/Chicago
timedatectl set-ntp on
```

LHammonds

---


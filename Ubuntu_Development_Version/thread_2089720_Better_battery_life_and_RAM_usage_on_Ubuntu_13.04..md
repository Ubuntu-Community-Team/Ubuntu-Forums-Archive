---
title: "Better battery life and RAM usage on Ubuntu 13.04."
date: 2012-11-30
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2012-11-30
Fingers crossed...[-o<

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-reduced-power-ram](https://blueprints.launchpad.net/ubuntu/+spec/desktop-r-reduced-power-ram)

---

### Post by thotz on 2012-11-30
I'm quite sure this will happen and in this cycle it will be just the beginning. Looking forward to Ubuntu 14.04 LTS :)

---

### Post by ELD on 2012-11-30
If they can do this performance should go up rather a lot :D, will be keeping an eye on it, hopefully at least some will change to DONE from TODO over this cycle.

---

### Post by serdotlinecho on 2012-11-30
Work items: 
TODO :D

```
[mterry] look at why lightdm is using 30MB: TODO
[canonical-desktop-team] go through the long running processes and run valgrind on them to assure we don't have obvious leaks: TODO
[seb128] look if gnome-keyring needs to be running all the time: TODO
look if polkit-gnome-authentication needs to be running all the time: TODO
[mhr3] make zg-fts expire datas after some time to reduce the size of the db: TODO
[charles] valgrind the indicators stack: TODO
look at making notify-osd exit on idle: TODO
[didrocks] talk to desrt and others about a "libidle" to use for "exit after idle": TODO
[ken-vandine] check with online team if signond needs to be running all the time: TODO
[ken-vandine] investigate long running telepathy-indicator/mission-control: TODO
[ken-vandine] investigate long running geoclue/geoip services: TODO
[charles] look at moving the eds/geoclue use in indicator-datetime from startup to about-to-show: TODO
[seb128] talk to U1 guys about memory usage and disk wakes: TODO
[seb128] look at what is making goa run for some users: TODO
[seb128] look at the dbus traffic and work to reduce it: TODO
[seb128] provide a list/documentation for python processes that could be ported to C/vala/...: TODO
[mhall119] engage with the community for the python->c/vala porting effort: TODO
[ogra] seed zram-conf: DONE
[seb128] talk to the QA team about daily measurement: TODO
[seb128] look at the wakeups list and set work items for the main offenders: TODO
[ogra] set up follow-up meetings about the topics we didn't cover during the session: TODO
```

---

### Post by screaminj3sus on 2012-12-01
> **serdotlinecho said:**
> Work items: 
TODO :D

```
[mterry] look at why lightdm is using 30MB: TODO
[canonical-desktop-team] go through the long running processes and run valgrind on them to assure we don't have obvious leaks: TODO
[seb128] look if gnome-keyring needs to be running all the time: TODO
look if polkit-gnome-authentication needs to be running all the time: TODO
[mhr3] make zg-fts expire datas after some time to reduce the size of the db: TODO
[charles] valgrind the indicators stack: TODO
look at making notify-osd exit on idle: TODO
[didrocks] talk to desrt and others about a "libidle" to use for "exit after idle": TODO
[ken-vandine] check with online team if signond needs to be running all the time: TODO
[ken-vandine] investigate long running telepathy-indicator/mission-control: TODO
[ken-vandine] investigate long running geoclue/geoip services: TODO
[charles] look at moving the eds/geoclue use in indicator-datetime from startup to about-to-show: TODO
[seb128] talk to U1 guys about memory usage and disk wakes: TODO
[seb128] look at what is making goa run for some users: TODO
[seb128] look at the dbus traffic and work to reduce it: TODO
[seb128] provide a list/documentation for python processes that could be ported to C/vala/...: TODO
[mhall119] engage with the community for the python->c/vala porting effort: TODO
[ogra] seed zram-conf: DONE
[seb128] talk to the QA team about daily measurement: TODO
[seb128] look at the wakeups list and set work items for the main offenders: TODO
[ogra] set up follow-up meetings about the topics we didn't cover during the session: TODO
```

Lots of good stuff, can't wait to see the fruits of these blueprints.

---


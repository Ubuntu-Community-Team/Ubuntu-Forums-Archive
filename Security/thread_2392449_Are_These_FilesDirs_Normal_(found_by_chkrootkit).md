---
title: "Are These Files/Dirs Normal (found by chkrootkit)"
date: 2018-05-21
forum: Security
---

### Post by Rick St. George on 2018-05-21
Running chkrootkit, I have these results. Are these "suspicious files and dirs" normal ?  Seems so to me, but if not - why are they being reported?

```

Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  

/usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit /usr/lib/debug/.build-id /usr/lib/jvm/java-8-oracle/lib/visualvm/visualvm/.lastModified /usr/lib/jvm/java-8-oracle/lib/visualvm/platform/.lastModified /usr/lib/jvm/java-8-oracle/lib/visualvm/profiler/.lastModified /usr/lib/jvm/java-8-oracle/lib/missioncontrol/.eclipseproduct /usr/lib/jvm/java-8-oracle/lib/missioncontrol/p2/org.eclipse.equinox.p2.engine/profileRegistry/JMC.profile/.lock /usr/lib/jvm/java-8-oracle/lib/missioncontrol/p2/org.eclipse.equinox.p2.engine/profileRegistry/JMC.profile/.data /usr/lib/jvm/java-8-oracle/lib/missioncontrol/p2/org.eclipse.equinox.p2.engine/.settings /usr/lib/jvm/.java-8-oracle.jinfo /usr/lib/jvm/.java-1.8.0-openjdk-amd64.jinfo /usr/lib/pymodules/python2.7/.path /lib/modules/4.4.0-122-lowlatency/vdso/.build-id /lib/modules/4.4.0-124-lowlatency/vdso/.build-id /usr/lib/debug/.build-id /usr/lib/jvm/java-8-oracle/lib/missioncontrol/p2/org.eclipse.equinox.p2.engine/profileRegistry/JMC.profile/.data /usr/lib/jvm/java-8-oracle/lib/missioncontrol/p2/org.eclipse.equinox.p2.engine/.settings /lib/modules/4.4.0-122-lowlatency/vdso/.build-id /lib/modules/4.4.0-124-lowlatency/vdso/.build-id


```

Any ideas? suggestions?

Thanks!
:confused:

---

### Post by TheFu on 2018-05-21
chkrootkit is full of false positives.  There is a way to add those to the ignore list, but every new package install seems to add more things to be added/ignored.  Eventually, I got tired of dealing with it and removed the tool.  Versioned backups are my #1 security tool.

---

### Post by Rick St. George on 2018-05-22
Thanks FU ... I'm saying Good Riddance too!

---


---
title: "System crashes?"
date: 2012-07-04
forum: System76 Support
---

### Post by mgolden on 2012-07-04
Twice in the past two days I have seen machine crashes.  What I saw this afternoon was rather odd.  It looked as though the machine was running off battery (i.e. the indicator didn't show that it was plugged in, even though it was).  I checked that the plug on the back was properly seated, and shortly thereafter it crashed.

I am wondering if this is caused by a recent kernel or x server update (one came in yesterday, I believe).  Below is what I see in the syslog from today.

Is anyone else seeing this?  Could it be a hardware problem?  (I have a gazelle that I bought in September.)

[HTML]
<pre>
Jul  4 17:07:14 gazelle anacron[25534]: Anacron 2.3 started on 2012-07-04
Jul  4 17:07:14 gazelle anacron[25534]: Normal exit (0 jobs run)
Jul  4 17:07:14 gazelle org.kde.powerdevil.backlighthelper: QDBusConnection: system D-Bus connection created before QCoreApplication. Application may misbehave.
Jul  4 17:07:14 gazelle dbus[929]: [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'
Jul  4 17:07:25 gazelle dbus[929]: [system] Activating service name='org.kde.powerdevil.backlighthelper' (using servicehelper)
Jul  4 17:07:25 gazelle org.kde.powerdevil.backlighthelper: QDBusConnection: system D-Bus connection created before QCoreApplication. Application may misbehave.
Jul  4 17:07:25 gazelle dbus[929]: [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'
Jul  4 17:08:54 gazelle dbus[929]: [system] Activating service name='org.kde.powerdevil.backlighthelper' (using servicehelper)
Jul  4 17:08:54 gazelle anacron[25885]: Anacron 2.3 started on 2012-07-04
Jul  4 17:08:54 gazelle anacron[25885]: Normal exit (0 jobs run)
Jul  4 17:08:54 gazelle org.kde.powerdevil.backlighthelper: QDBusConnection: system D-Bus connection created before QCoreApplication. Application may misbehave.
Jul  4 17:08:54 gazelle dbus[929]: [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'
Jul  4 17:17:01 gazelle CRON[26636]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  4 17:19:23 gazelle kernel: [16204.245272] ACPI: EC: input buffer is not empty, aborting transaction
Jul  4 17:19:24 gazelle kernel: [16204.744565] ACPI: EC: input buffer is not empty, aborting transaction
Jul  4 17:19:24 gazelle kernel: [16204.744586] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20110623/evregion-478)
Jul  4 17:19:24 gazelle kernel: [16204.744616] ACPI Error: Method parse/execution failed [\_TZ_.THM0._TMP] (Node ffff880414c6b2a8), AE_TIME (20110623/psparse-536)
Jul  4 17:19:24 gazelle kernel: [16204.744660] Thermal: failed to read out thermal zone 0
Jul  4 17:19:24 gazelle kernel: [16205.243793] ACPI: EC: input buffer is not empty, aborting transaction
Jul  4 17:19:24 gazelle kernel: [16205.243798] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20110623/evregion-478)
Jul  4 17:19:24 gazelle kernel: [16205.243807] ACPI Error: Method parse/execution failed [\_SB_.BAT0._STA] (Node ffff880414c523c0), AE_TIME (20110623/psparse-536)
Jul  4 17:19:24 gazelle kernel: [16205.243819] ACPI Exception: AE_ERROR, Evaluating _STA (20110623/battery-396)
Jul  4 17:19:25 gazelle kernel: [16205.743136] ACPI: EC: input buffer is not empty, aborting transaction
Jul  4 17:19:25 gazelle kernel: [16205.743152] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20110623/evregion-478)
Jul  4 17:19:25 gazelle kernel: [16205.743176] ACPI Error: Method parse/execution failed [\_SB_.BAT0._STA] (Node ffff880414c523c0), AE_TIME (20110623/psparse-536)
Jul  4 17:19:25 gazelle kernel: [16205.743212] ACPI Exception: AE_ERROR, Evaluating _STA (20110623/battery-396)
Jul  4 17:19:25 gazelle kernel: [16206.242324] ACPI: EC: input buffer is not empty, aborting transaction
Jul  4 17:19:26 gazelle kernel: [16206.741634] ACPI: EC: input buffer is not empty, aborting transaction
Jul  4 17:19:26 gazelle kernel: [16207.240941] ACPI: EC: input buffer is not empty, aborting transaction
Jul  4 17:19:26 gazelle kernel: [16207.240960] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20110623/evregion-478)
Jul  4 17:19:26 gazelle kernel: [16207.240985] ACPI Error: Method parse/execution failed [\_TZ_.THM0._TMP] (Node ffff880414c6b2a8), AE_TIME (20110623/psparse-536)
Jul  4 17:19:27 gazelle kernel: [16207.740094] ACPI: EC: input buffer is not empty, aborting transaction
Jul  4 17:19:27 gazelle kernel: [16208.239411] ACPI: EC: input buffer is not empty, aborting transaction
Jul  4 17:19:28 gazelle kernel: [16208.738708] ACPI: EC: input buffer is not empty, aborting transaction
Jul  4 17:19:28 gazelle kernel: [16208.738726] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20110623/evregion-478)
Jul  4 17:19:28 gazelle kernel: [16208.738752] ACPI Error: Method parse/execution failed [\_TZ_.THM0._TMP] (Node ffff880414c6b2a8), AE_TIME (20110623/psparse-536)
Jul  4 17:19:28 gazelle kernel: [16209.241905] ACPI: EC: input buffer is not empty, aborting transaction
Jul  4 17:19:28 gazelle kernel: [16209.241924] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20110623/evregion-478)
Jul  4 17:19:28 gazelle kernel: [16209.241949] ACPI Error: Method parse/execution failed [\_SB_.BAT0._STA] (Node ffff880414c523c0), AE_TIME (20110623/psparse-536)
Jul  4 17:19:28 gazelle kernel: [16209.241984] ACPI Exception: AE_ERROR, Evaluating _STA (20110623/battery-396)
Jul  4 17:19:29 gazelle kernel: [16209.741218] ACPI: EC: input buffer is not empty, aborting transaction
Jul  4 1Jul  4 17:20:03 gazelle kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jul  4 17:20:03 gazelle rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="885" x-info="http://www.rsyslog.com"] start
Jul  4 17:20:03 gazelle rsyslogd: rsyslogd's groupid changed to 103
Jul  4 17:20:03 gazelle rsyslogd: rsyslogd's userid changed to 101
Jul  4 17:20:03 gazelle rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul  4 17:20:03 gazelle kernel: [    0.000000] Initializing cgroup subsys cpuset
</pre>
[/HTML]

---


---
title: "cgroup2 cpu.max limits are periodically reset via unknown reason"
date: 2022-01-27
forum: Server Platforms
---

### Post by daubsi on 2022-01-27
I am using Ubuntu-20.04.3 LTS, systemd 245.5

The system hardware is rather old and uses software RAID1 (md) with old spinning disks. Overall, the I/O performance is nothing really great, but for a home server system using it for all kind of things it is good enough.

Last week I wanted to compile tensorflow from source, which are over 35k files. I noticed that during the compile the "wa" (wait I/O) in top rose up to 80-100 for each core and my system load went through the ceiling as well (80-100 on a 4 core system!). This is all fine as long as it doesn't take long, but 35k files take some hours to compile of course. Due to the high load all services on my server became unresponsive: DNS, DHCP, Squid, postfix, ... none of those reacted anymore, ssh login into the server took between 5 and 10 minutes.... 

The reason for this, shall not matter right now (apparently the disks are just very bad and I need to shop some more modern stuff). It is what it is, but I read about cgroups and whether they could help me. 
Turned out they could! I switched my system to use cgroup2 exclusively and everything worked fine after a reboot. 

Then I created a new cgroup "adhoc.slice" under /sys/fs/cgroup where I wanted to set limits for CPU usage and IO in order to limit those processes leading to such a high system load. I activated the IO and CPU subtree controllers and set

```
root@bigigloo:/sys/fs/cgroup# cat cgroup.controllerscpuset cpu io memory hugetlb pids rdma
root@bigigloo:/sys/fs/cgroup# cat cgroup.subtree_control
cpuset cpu io memory hugetlb pids rdma
root@bigigloo:/sys/fs/cgroup# cat adhoc.slice/cgroup.controllers
cpuset cpu io memory hugetlb pids rdma
root@bigigloo:/sys/fs/cgroup# cat adhoc.slice/cgroup.subtree_control
root@bigigloo:/sys/fs/cgroup# cat adhoc.slice/cpu.max
100000 1000000
root@bigigloo:/sys/fs/cgroup# cat adhoc.slice/io.max
9:1 rbps=max wbps=524288 riops=max wiops=50
9:0 rbps=max wbps=524288 riops=max wiops=50

```

Then I opened a new shall and ran:

```

systemd-run --uid myid --shell --slice=adhoc

```

This created me a subdirectory at /sys/fs/cgroup/adhoc.slice/run-u266.service

Then I started the compile job and yes, everything worked like a charm. The CPU usage was very very limited and IO was kept in tight limits and my system stayed stable. I tweaked some settings to see how far I could get my writing new values to cpu.max and io.max to play around until I found the sweet spot. It compiled very slowly but that's ok because it was just running in the background. 

However, the compile job ran in total for > 4 days and every day and every day I noticed that the system became unstable. When I checked "top" I saw, that my compile processes suddenly ran again at full speed, taking >95% CPU and were responsible for an incredible high system load, basically trashing my whole system.

Wondering how that could be I noticed that cpu.max no longer contained my "100000 1000000" or "300000 1000000" or whatever it was set at that point in time, but suddenly cpu.max just contained "max 1000000", basically freeing the processes again from their jail. Writing "100000 1000000" back to cpu.max immediately limited the processes and my system returned to normal behavior.... until it was again reset hours later again to "max 1000000". The io.max was not touched, just cpu.max changed without my intervention.

I tried to pinpoint WHAT was responsible for resetting the values by monitoring /var/log/syslog but I could not find anything suspicious. I can limit the point in time very closely up to the minute when it happens.

I found some references to systemd in the logs so I suspect it has something to do with it.

```

Jan 27 06:45:35 bigigloo systemd[1]: We couldn't coldplug run-u266.service, proceeding anyway: Connection timed out
...
Jan 27 11:43:01 bigigloo CRON[1459177]: (root) CMD (/root/record_cpu_max.sh)
Jan 27 11:43:01 bigigloo APCUPS: Current power consumptions: WATTS=124
Jan 27 11:43:04 bigigloo dbus-daemon[1494]: [system] Activating via systemd: service name='org.freedesktop.PackageKit' unit='packagekit.service' requested by ':1.2360' (uid=0 pid=1460475 comm="/usr/bin/gdbus call --system --dest org.freedeskto" label="unconfined")
Jan 27 11:43:04 bigigloo systemd[1]: Starting PackageKit Daemon...
Jan 27 11:43:05 bigigloo PackageKit: daemon start
Jan 27 11:43:05 bigigloo dbus-daemon[1494]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jan 27 11:43:05 bigigloo systemd[1]: Started PackageKit Daemon.
Jan 27 11:43:30 bigigloo dockerd[8421]: time="2022-01-27T11:43:30.701133580+01:00" level=error msg="stream copy error: reading from a closed fifo"
Jan 27 11:43:30 bigigloo dockerd[8421]: time="2022-01-27T11:43:30.701179185+01:00" level=error msg="stream copy error: reading from a closed fifo"
Jan 27 11:43:30 bigigloo dockerd[8421]: time="2022-01-27T11:43:30.706447662+01:00" level=warning msg="Health check for container b105fe964a83aa8782b9063eff4906ced57705361fae084922a9cc856ca4da40 error: context deadline exceeded"
Jan 27 11:43:36 bigigloo systemd[1]: apt-daily.service: Succeeded.
Jan 27 11:43:36 bigigloo systemd[1]: Finished Daily apt download activities.
Jan 27 11:43:36 bigigloo systemd[1]: apt-daily.service: Consumed 30.344s CPU time.

```

My monitoring script also showed, that eventually the set limits seem to be restored as well? (05:44 - 05:48)

```

...
...
Wed 26 Jan 2022 05:41:01 PM CET 100000 1000000 17:41:01 up 4 days, 7:05, 5 users, load average: 2.58, 2.50, 2.34
Wed 26 Jan 2022 05:42:01 PM CET 100000 1000000 17:42:01 up 4 days, 7:06, 5 users, load average: 1.73, 2.29, 2.28
Wed 26 Jan 2022 05:43:01 PM CET 100000 1000000 17:43:01 up 4 days, 7:07, 5 users, load average: 2.29, 2.31, 2.28   <----
Wed 26 Jan 2022 05:44:01 PM CET max 100000 17:44:01 up 4 days, 7:08, 5 users, load average: 5.97, 3.38, 2.65
Wed 26 Jan 2022 05:45:01 PM CET max 100000 17:45:01 up 4 days, 7:09, 5 users, load average: 6.61, 4.06, 2.94
Wed 26 Jan 2022 05:46:01 PM CET max 100000 17:46:01 up 4 days, 7:10, 5 users, load average: 7.41, 4.76, 3.25
Wed 26 Jan 2022 05:47:01 PM CET max 100000 17:47:01 up 4 days, 7:11, 5 users, load average: 7.21, 5.14, 3.47
Wed 26 Jan 2022 05:48:01 PM CET max 100000 17:48:01 up 4 days, 7:12, 5 users, load average: 7.07, 5.49, 3.70
Wed 26 Jan 2022 05:49:01 PM CET max 100000 17:49:01 up 4 days, 7:13, 5 users, load average: 6.80, 5.69, 3.89
Wed 26 Jan 2022 05:50:01 PM CET max 100000 17:50:01 up 4 days, 7:14, 5 users, load average: 6.93, 6.05, 4.13
Wed 26 Jan 2022 05:51:01 PM CET max 100000 17:51:01 up 4 days, 7:15, 5 users, load average: 8.21, 6.71, 4.49
Wed 26 Jan 2022 05:52:01 PM CET max 100000 17:52:01 up 4 days, 7:16, 5 users, load average: 7.67, 6.90, 4.70
Wed 26 Jan 2022 05:53:01 PM CET max 100000 17:53:01 up 4 days, 7:17, 5 users, load average: 6.57, 6.72, 4.77
Wed 26 Jan 2022 05:54:01 PM CET max 100000 17:54:01 up 4 days, 7:18, 5 users, load average: 6.33, 6.62, 4.86
Wed 26 Jan 2022 05:55:01 PM CET max 100000 17:55:01 up 4 days, 7:19, 5 users, load average: 7.21, 6.85, 5.05
Wed 26 Jan 2022 05:56:01 PM CET max 100000 17:56:01 up 4 days, 7:20, 5 users, load average: 7.04, 6.89, 5.18
Wed 26 Jan 2022 05:57:01 PM CET max 100000 17:57:01 up 4 days, 7:21, 5 users, load average: 6.73, 6.84, 5.27
Wed 26 Jan 2022 05:58:01 PM CET 100000 1000000 17:58:01 up 4 days, 7:22, 5 users, load average: 4.53, 6.22, 5.16  <---
Wed 26 Jan 2022 05:59:01 PM CET 100000 1000000 17:59:01 up 4 days, 7:23, 5 users, load average: 3.10, 5.48, 4.97
....
Thu 27 Jan 2022 06:43:01 AM CET 500000 1000000 06:43:01 up 4 days, 20:07, 4 users, load average: 2.20, 2.15, 2.17
Thu 27 Jan 2022 06:44:01 AM CET 500000 1000000 06:44:01 up 4 days, 20:08, 4 users, load average: 5.43, 3.04, 2.48
Thu 27 Jan 2022 06:45:01 AM CET 500000 1000000 06:45:01 up 4 days, 20:09, 4 users, load average: 6.05, 3.66, 2.73
Thu 27 Jan 2022 06:46:01 AM CET max 100000 06:46:01 up 4 days, 20:10, 4 users, load average: 9.96, 5.07, 3.27  <---
Thu 27 Jan 2022 06:47:01 AM CET max 100000 06:47:01 up 4 days, 20:11, 4 users, load average: 11.39, 6.46, 3.86
Thu 27 Jan 2022 06:48:01 AM CET max 100000 06:48:01 up 4 days, 20:12, 4 users, load average: 9.57, 6.93, 4.20
Thu 27 Jan 2022 06:51:20 AM CET max 100000 06:51:20 up 4 days, 20:16, 4 users, load average: 93.83, 39.11, 16.50
Thu 27 Jan 2022 06:51:21 AM CET max 100000 06:51:21 up 4 days, 20:16, 4 users, load average: 93.83, 39.11, 16.50
Thu 27 Jan 2022 06:51:21 AM CET max 100000 06:51:21 up 4 days, 20:16, 4 users, load average: 93.83, 39.11, 16.50
Thu 27 Jan 2022 07:16:42 AM CET max 100000 07:16:42 up 4 days, 20:41, 4 users, load average: 268.90, 251.10, 184.94
Thu 27 Jan 2022 07:16:42 AM CET max 100000 07:16:42 up 4 days, 20:41, 4 users, load average: 268.90, 251.10, 184.94
Thu 27 Jan 2022 07:16:42 AM CET max 100000 07:16:42 up 4 days, 20:41, 4 users, load average: 268.90, 251.10, 184.94
Thu 27 Jan 2022 07:16:42 AM CET max 100000 07:16:42 up 4 days, 20:41, 4 users, load average: 268.90, 251.10, 184.94
Thu 27 Jan 2022 07:16:42 AM CET max 100000 07:16:42 up 4 days, 20:41, 4 users, load average: 268.90, 251.10, 184.94
Thu 27 Jan 2022 07:16:42 AM CET max 100000 07:16:42 up 4 days, 20:41, 4 users, load average: 268.90, 251.10, 184.94
Thu 27 Jan 2022 07:16:42 AM CET max 100000 07:16:42 up 4 days, 20:41, 4 users, load average: 268.90, 251.10, 184.94
Thu 27 Jan 2022 07:16:42 AM CET max 100000 07:16:42 up 4 days, 20:41, 4 users, load average: 268.90, 251.10, 184.94
Thu 27 Jan 2022 07:16:42 AM CET max 100000 07:16:42 up 4 days, 20:41, 4 users, load average: 268.90, 251.10, 184.94 
...
...


```

As you can see this morning at 6:46 hell broke loose. 

I already checked systemctl list-timers, crontabs etc. whats going on but couldn't find any job that runs at those times, however something is somewhat scheduled at that time due to the fact its always around :44 or :45 at those hours. 

(systemd related lines during that time only)
```

...
...
Jan 27 06:44:44 bigigloo systemd[1]: nut-monitor.service: Supervising process 3523 which is not our child. We'll most likely not notice when it exits.
Jan 27 06:44:48 bigigloo systemd[50947]: run-docker-runtime\x2drunc-moby-b105fe964a83aa8782b9063eff4906ced57705361fae084922a9cc856ca4da40-runc.kMjIbm.mount: Succeeded.
Jan 27 06:45:10 bigigloo systemd[1]: We couldn't coldplug machine-qemu\x2d1\x2dWin2016DC.scope, proceeding anyway: Connection timed out
Jan 27 06:45:19 bigigloo systemd[50947]: run-docker-runtime\x2drunc-moby-b105fe964a83aa8782b9063eff4906ced57705361fae084922a9cc856ca4da40-runc.wPvQMM.mount: Succeeded.
Jan 27 06:45:35 bigigloo systemd[1]: We couldn't coldplug run-u266.service, proceeding anyway: Connection timed out                                 
Jan 27 06:45:35 bigigloo systemd[1]: udisks2.service: Unexpected error response from GetNameOwner(): Connection terminated               
Jan 27 06:45:35 bigigloo systemd[1]: accounts-daemon.service: Unexpected error response from GetNameOwner(): Connection terminated
Jan 27 06:45:35 bigigloo systemd[1]: wpa_supplicant.service: Unexpected error response from GetNameOwner(): Connection terminated
Jan 27 06:45:36 bigigloo systemd[1]: tuned.service: Unexpected error response from GetNameOwner(): Connection terminated
Jan 27 06:45:36 bigigloo systemd[1]: polkit.service: Unexpected error response from GetNameOwner(): Connection terminated
Jan 27 06:45:36 bigigloo systemd[1]: systemd-logind.service: Unexpected error response from GetNameOwner(): Connection terminated
Jan 27 06:45:36 bigigloo systemd[1]: systemd-machined.service: Unexpected error response from GetNameOwner(): Connection terminated
Jan 27 06:45:36 bigigloo systemd[1]: avahi-daemon.service: Unexpected error response from GetNameOwner(): Connection terminated
Jan 27 06:45:36 bigigloo systemd[1]: ModemManager.service: Unexpected error response from GetNameOwner(): Connection terminated
Jan 27 06:45:36 bigigloo systemd[1]: rtkit-daemon.service: Unexpected error response from GetNameOwner(): Connection terminated
Jan 27 06:45:36 bigigloo systemd[1]: colord.service: Unexpected error response from GetNameOwner(): Connection terminated
Jan 27 06:45:37 bigigloo systemd[1]: polkit.service: Succeeded.
Jan 27 06:45:37 bigigloo systemd[1]: polkit.service: Consumed 2.111s CPU time.
Jan 27 06:45:37 bigigloo systemd[1]: colord.service: Succeeded.
Jan 27 06:45:37 bigigloo systemd[1]: rtkit-daemon.service: Succeeded.
Jan 27 06:45:38 bigigloo systemd[1]: rtkit-daemon.service: Consumed 4.836s CPU time.
Jan 27 06:45:38 bigigloo systemd[1]: Starting Message of the Day...
Jan 27 06:45:38 bigigloo systemd[1]: run-docker-runtime\x2drunc-moby-2d5e52ed7054726cd5d8d186e1cc2b68fd2d8b37428c8338c63c061a38b4ca4b-runc.cKAvBW.mount: Succeeded.
Jan 27 06:45:38 bigigloo systemd[50947]: run-docker-runtime\x2drunc-moby-2d5e52ed7054726cd5d8d186e1cc2b68fd2d8b37428c8338c63c061a38b4ca4b-runc.cKAvBW.mount: Succeeded.
Jan 27 06:45:39 bigigloo systemd[1]: motd-news.service: Succeeded.
Jan 27 06:45:39 bigigloo systemd[1]: Finished Message of the Day.
Jan 27 06:45:40 bigigloo systemd[1]: avahi-daemon.service: Succeeded.
Jan 27 06:45:40 bigigloo systemd[1]: avahi-daemon.service: Consumed 1min 55.626s CPU time.
Jan 27 06:45:40 bigigloo systemd[1]: accounts-daemon.service: Succeeded.
Jan 27 06:45:40 bigigloo systemd[1]: accounts-daemon.service: Consumed 29.454s CPU time.
Jan 27 06:45:41 bigigloo systemd[1]: systemd-logind.service: Succeeded.
Jan 27 06:45:41 bigigloo systemd[1]: systemd-logind.service: Succeeded.
Jan 27 06:45:41 bigigloo systemd[1]: systemd-logind.service: Consumed 1min 2.461s CPU time.
Jan 27 06:45:41 bigigloo systemd[1]: systemd-logind.service: Scheduled restart job, restart counter is at 1.
Jan 27 06:45:41 bigigloo systemd[1]: Stopped Login Service.
Jan 27 06:45:41 bigigloo systemd[1]: systemd-logind.service: Consumed 1min 2.461s CPU time.
Jan 27 06:45:41 bigigloo systemd[1]: Condition check resulted in Load Kernel Module drm being skipped.
Jan 27 06:45:41 bigigloo systemd[1]: Starting Login Service...
Jan 27 06:45:41 bigigloo systemd[1]: systemd-machined.service: Succeeded.
Jan 27 06:45:41 bigigloo systemd[1]: systemd-machined.service: Consumed 52.956s CPU time.
Jan 27 06:45:42 bigigloo dbus-daemon[1494]: [system] Reloaded configuration
Jan 27 06:45:43 bigigloo dbus-daemon[1494]: [system] Reloaded configuration
Jan 27 06:45:43 bigigloo dbus-daemon[1494]: [system] Activating via systemd: service name='org.freedesktop.Avahi' unit='dbus-org.freedesktop.Avahi.service' requested by ':1.2220' (uid=0 pid=1073551 comm="/usr/sbin/cupsd -l " label="/usr/sbin/cupsd
(enforce)")
Jan 27 06:45:43 bigigloo systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Jan 27 06:45:43 bigigloo systemd[1]: wpa_supplicant.service: Succeeded.
Jan 27 06:45:43 bigigloo systemd[1]: wpa_supplicant.service: Consumed 1.775s CPU time.
Jan 27 06:45:44 bigigloo dbus-daemon[1494]: [system] Successfully activated service 'org.freedesktop.Avahi'
Jan 27 06:45:44 bigigloo systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Jan 27 06:45:45 bigigloo systemd[1]: Started Login Service.
Jan 27 06:45:50 bigigloo dbus-daemon[1494]: [system] Activating via systemd: service name='org.freedesktop.ColorManager' unit='colord.service' requested by ':1.2099' (uid=0 pid=1073551 comm="/usr/sbin/cupsd -l " label="/usr/sbin/cupsd (enforce)")
Jan 27 06:45:50 bigigloo systemd[1]: Starting Manage, Install and Generate Color Profiles...
Jan 27 06:45:52 bigigloo dbus-daemon[1494]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jan 27 06:45:52 bigigloo systemd[1]: Started Manage, Install and Generate Color Profiles.
Jan 27 06:45:53 bigigloo systemd[1]: udisks2.service: Succeeded.
Jan 27 06:45:53 bigigloo systemd[1]: udisks2.service: Consumed 6min 4.145s CPU time.
Jan 27 06:45:54 bigigloo systemd[1]: ModemManager.service: Succeeded.
Jan 27 06:45:58 bigigloo systemd[1]: Reloading.
Jan 27 06:45:58 bigigloo systemd[1]: nut-monitor.service: Supervising process 3523 which is not our child. We'll most likely not notice when it exits.
Jan 27 06:46:09 bigigloo systemd[1]: Stopping User Manager for UID 1000...
Jan 27 06:46:11 bigigloo systemd[50947]: Stopped target Main User Target.
Jan 27 06:46:12 bigigloo systemd[50947]: Stopping D-Bus User Message Bus...
Jan 27 06:46:13 bigigloo systemd[50947]: dbus.service: Succeeded.
Jan 27 06:46:13 bigigloo systemd[50947]: Stopped D-Bus User Message Bus.
Jan 27 06:46:13 bigigloo systemd[50947]: Stopped target Basic System.
Jan 27 06:46:14 bigigloo systemd[50947]: Stopped target Paths.
Jan 27 06:46:14 bigigloo systemd[50947]: Stopped target Sockets.
Jan 27 06:46:14 bigigloo systemd[50947]: Stopped target Timers.
Jan 27 06:46:14 bigigloo systemd[50947]: dbus.socket: Succeeded.
Jan 27 06:46:14 bigigloo systemd[50947]: Closed D-Bus User Message Bus Socket.
Jan 27 06:46:14 bigigloo systemd[50947]: dirmngr.socket: Succeeded.
Jan 27 06:46:15 bigigloo systemd[50947]: Closed GnuPG network certificate management daemon.
Jan 27 06:46:15 bigigloo systemd[50947]: gpg-agent-browser.socket: Succeeded.
...
...

```

What's going on here? Why is the cpu.max reset? It seems as if systemd performs some kind of general reset, reload or refresh or something?

Did I wrongly setup my cgroup? What I wanted to evaluate is if I encounter a performance hog or other problem on my system I'd like to have the change to just throw it into a limiting cgroup to make the system responsive again at the cost of prolonged runtime for that bad process. So I don't know upfront whether something will put a high load but I want to be able to manage this at runtime and then just handle it manually.

---


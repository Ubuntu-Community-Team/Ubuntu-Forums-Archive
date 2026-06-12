---
title: "What happened to daemon.log?"
date: 2012-07-31
forum: Server Platforms
---

### Post by jdmcmillian on 2012-07-31
Ideally I want to be able to track when any daemon or upstart job is started, stopped or any other event occurs to the processes.

If what I've read is correct this use to be recorded in daemon.log but I cant find daemon.log anywhere.  so... assuming its been merged into syslog, where would I insert this line in order to record these events?

echo "`date` `hostname` $0 : $1" >> /var/log/serviceevents.log

where $0 is the name of the service and $1 is the action  This was modeled after the generic upstart script /lib/init/upstart-job but it doesnt seem to capture the boot time and shutdown time events.

Thanks,
JD

---


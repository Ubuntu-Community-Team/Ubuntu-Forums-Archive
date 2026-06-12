---
title: "RAID Monitoring for Unatended Server (7.10)"
date: 2008-01-13
forum: Server Platforms
---

### Post by GMU_ninja on 2008-01-13
I have seen a couple old threads with people asking about RAID monitoring, but no answers.

I have a x86 (64-bit) Ubuntu Server (7.10) with a 4 disk RAID5.  I designed it as a Backup/File server.  In normal situations, I will not be using the system directly, and thus will have no idea if a disk goes bad.

I need a way to be notified if something goes wrong with the RAID array, so that I can replace the disk and rebuild the data before I loose another disk.  Email notification would be great, but any kind of notification would be good.

Any Ideas?

---

### Post by jlintz on 2008-01-13
Are you using software or hardware RAID?

If you are using software.  You can use mdadm to configure a monitor to email you in the event of a failure. See [http://unthought.net/Software-RAID.HOWTO/Software-RAID.HOWTO.html#toc6.5](http://unthought.net/Software-RAID.HOWTO/Software-RAID.HOWTO.html#toc6.5)

---

### Post by foxylad on 2008-01-13
I include the following snippet in a script run daily by cron:

```
if [ `grep -c [UU] /proc/mdstat` == 3 ]
then
        echo "============ Raid OK ============="
else
        echo "!!!!!!!!!! RAID FAILED !!!!!!!!!!!"
fi
```

Cron is set to send any output from the script to the root user, so I get an email each day confirming raid is OK.

---

### Post by robert_pectol on 2008-01-16
Here's what I use on my server:
```

#!/bin/bash
#
#       Called by cron every hour to monitor
#       my raid array
#
#########################################

# send mail to this address on raid device failure
ADMIN="my_address@my_domain.com"

# other variables
HOSTNAME=`/bin/hostname`
MAIL=`which mail`
 
if egrep "\[.*_.*\]" /proc/mdstat  > /dev/null; then
        logger -p daemon.error "raidmonitor.sh: Failure of one or more software RAID devices"
        echo "Failure of one or more software RAID devices on ${HOSTNAME}" | $MAIL -s  \
        "$0: Software RAID device failure on ${HOSTNAME}" ${ADMIN}
        exit 1
else
        logger -p daemon.error "raidmonitor.sh: Raid array is healthy"
        echo "raidmonitor.sh: Raid array is healthy"
fi
exit 0

```
Simply put in your e-mail address and save it, make it executable, and then call it from cron as often as you want your raid array checked.  I have cron call it every hour.

---


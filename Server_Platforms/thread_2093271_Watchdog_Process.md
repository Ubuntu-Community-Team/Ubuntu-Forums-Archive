---
title: "Watchdog Process"
date: 2012-12-10
forum: Server Platforms
---

### Post by sandyd on 2012-12-10
How can I setup a watchdog for a service (say mysql) that will check periodically if it is still running?

I would probably have to set a number of conditions, i.e.
-No MySQL processes running
-MySQL socket missing
.etc .etc

---

### Post by SeijiSensei on 2012-12-10
I run the following script from /etc/crontab every fifteen minutes.  This is written for CentOS machines so you might need to fiddle with the syntax a bit:

```

#!/bin/sh

LOG=/var/log/daemon-check.log

PROGS="sshd crond rsyslog httpd named ntpd openvpn postgres squid c-icap"

for prog in $PROGS
do
   progtest=`ps aux --width=256 | grep $prog | grep -v grep`
   #echo $progtest  ### debug
   if [ "$progtest" != "" ]
   then
      echo -n `date` >> $LOG
      echo " $prog running" >> $LOG
   else
      /sbin/service $prog restart  >> $LOG 2>&1
      echo -n `date` >> $LOG
      echo " $prog *** RESTARTED ***" >> $LOG
   fi
done
 
exit 0

```

---

### Post by sandyd on 2012-12-10
> **SeijiSensei said:**
> I run the following script from /etc/crontab every fifteen minutes.  This is written for CentOS machines so you might need to fiddle with the syntax a bit:

```

#!/bin/sh

LOG=/var/log/daemon-check.log

PROGS="sshd crond rsyslog httpd named ntpd openvpn postgres squid c-icap"

for prog in $PROGS
do
   progtest=`ps aux --width=256 | grep $prog | grep -v grep`
   #echo $progtest  ### debug
   if [ "$progtest" != "" ]
   then
      echo -n `date` >> $LOG
      echo " $prog running" >> $LOG
   else
      /sbin/service $prog restart  >> $LOG 2>&1
      echo -n `date` >> $LOG
      echo " $prog *** RESTARTED ***" >> $LOG
   fi
done
 
exit 0

```

works nicely with tweaking. thanks!

---


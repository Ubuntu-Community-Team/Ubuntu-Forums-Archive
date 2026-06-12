---
title: "crontab logs"
date: 2009-06-29
forum: Server Platforms
---

### Post by salim.madni on 2009-06-29
dear gurus,

can you read this file and advise me what could be wrong the jobs has not run properly.

we have disaster of our raid 10 failed on SAN drive all 4 disks offline and finaly we have to re-build the raid drives,volume groups that were attached to our linux production live machine.

now we cant find out what time exactly problems comes, why the backup could not transfer from crontab jobs runs daily 2am to our windows machine using samba shares

Jun 24 16:05:01 hacjed7 crond[13387]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 16:10:01 hacjed7 crond[13394]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 16:10:01 hacjed7 crond[13395]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 16:15:01 hacjed7 crond[13400]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 16:20:01 hacjed7 crond[13405]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 16:20:01 hacjed7 crond[13406]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 16:25:01 hacjed7 crond[13413]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 16:30:01 hacjed7 crond[13422]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 16:30:01 hacjed7 crond[13423]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 16:35:01 hacjed7 crond[13436]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 16:40:01 hacjed7 crond[13445]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 16:40:01 hacjed7 crond[13446]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 16:45:01 hacjed7 crond[13455]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 16:50:01 hacjed7 crond[13462]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 16:50:01 hacjed7 crond[13463]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 16:55:01 hacjed7 crond[13468]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 17:00:01 hacjed7 crond[13472]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 17:00:01 hacjed7 crond[13474]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 17:01:01 hacjed7 crond[13481]: (root) CMD (run-parts /etc/cron.hourly)
Jun 24 17:05:01 hacjed7 crond[13494]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 17:05:01 hacjed7 crond[13495]: (root) CMD (/root/shutdown.sh)
Jun 24 17:10:01 hacjed7 crond[14011]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 17:10:01 hacjed7 crond[14012]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 17:15:01 hacjed7 crond[14019]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 17:20:01 hacjed7 crond[14022]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 17:20:01 hacjed7 crond[14023]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 17:25:01 hacjed7 crond[14032]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 17:30:01 hacjed7 crond[14036]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 17:30:01 hacjed7 crond[14038]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 17:35:01 hacjed7 crond[14043]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 17:40:01 hacjed7 crond[14050]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 17:40:01 hacjed7 crond[14051]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 17:45:01 hacjed7 crond[14056]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 17:50:01 hacjed7 crond[14061]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 17:50:01 hacjed7 crond[14062]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 17:55:01 hacjed7 crond[14067]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 18:00:01 hacjed7 crond[14074]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 18:00:01 hacjed7 crond[14075]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 18:01:01 hacjed7 crond[14082]: (root) CMD (run-parts /etc/cron.hourly)
Jun 24 18:05:01 hacjed7 crond[14094]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 18:10:01 hacjed7 crond[14100]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 18:10:01 hacjed7 crond[14101]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 18:15:01 hacjed7 crond[14106]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 18:20:01 hacjed7 crond[14114]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 18:20:01 hacjed7 crond[14115]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 18:25:01 hacjed7 crond[14120]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 18:30:01 hacjed7 crond[14127]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 18:30:01 hacjed7 crond[14128]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 18:35:01 hacjed7 crond[14133]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 18:40:01 hacjed7 crond[14138]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 18:40:01 hacjed7 crond[14139]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 18:45:01 hacjed7 crond[14144]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 18:50:01 hacjed7 crond[14149]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 18:50:01 hacjed7 crond[14150]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 18:55:50 hacjed7 crond[3201]: (CRON) STARTUP (V5.0)
Jun 24 18:55:53 hacjed7 anacron[3264]: Anacron 2.3 started on 2009-06-24
Jun 24 18:55:53 hacjed7 anacron[3264]: Normal exit (0 jobs run)
Jun 24 19:00:01 hacjed7 crond[4405]: (root) CMD (/usr/lib64/sa/sa1 1 1)
Jun 24 19:00:01 hacjed7 crond[4406]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)
Jun 24 19:01:01 hacjed7 crond[4409]: (root) CMD (run-parts /etc/cron.hourly)
Jun 24 19:05:01 hacjed7 crond[4421]: (root) CMD (/usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok)

regards
salim

---

### Post by jhannah on 2009-06-30
Unfortunately the information you are looking for just isn't in the log file. It simply shows it running MRTG's cronjob along with one for '/usr/lib64/sa/sa1'. Generally you would want to redirect the output of any critical commands you run to a logrotated file so you can review them in situations like this. From what I see, it does look like someone rebooted the machine around 18:55 since the PIDs for the cron processes are an order of magnatude less (generally they get larger as the machine has been up for some time). You might want to look in the output of some of the other logs to see if the backup process or some other daemon logged anything that you can use to reconstruct exactly what happened.

---


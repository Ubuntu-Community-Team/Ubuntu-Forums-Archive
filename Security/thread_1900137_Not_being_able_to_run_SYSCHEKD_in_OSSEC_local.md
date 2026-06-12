---
title: "Not being able to run SYSCHEKD in OSSEC local"
date: 2011-12-25
forum: Security
---

### Post by metalaarif on 2011-12-25
I am newbee to OSSEC. My objective is to install OSSEC in a ubuntu 10.04 server, configure it and then install rootkits, tamper files and then scan for possible notification and alerts.
BUT I tired and then changed few setting in ossec.conf but its nearly similar to default setting.

After successful installation for local 
I thought of modifying below commands before really installing rootkits and detecting it.
#touch /bin/ls
#touch /bin/ps
then i performed
#/var/ossec/bin/ossec-syscheckd start
then, i went to see the log file
#tail /var/ossec/logs/ossec.log
then i saw that it was scanning. I could see it in log file that it was monitoring directories and then
started syscheck database and then started syscheck rootcheck scan

The thing I don't understand is Unlike Aide and Samhain why am i not being able to perform scan and then get notifications of changes that i had done.
I didn't even get any log message in alerts.log.

:KS
I am confused. I just want to test if OSSEC can successfully detect rootkits, file tampering and then report or notify when i perform scan.
I would really appreciate if anyone could help me.

---


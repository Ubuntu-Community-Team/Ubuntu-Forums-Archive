---
title: "Ubuntu 16.04 has hung middle of application and login GUI loops and hung for ever"
date: 2016-11-21
forum: Server Platforms
---

### Post by bmvsprasad on 2016-11-21
Hello All Good Afternoon

        I am new to this forum. I am glad finding  a venue where people can discuss and find solutions. Thanks to all who are making this forum successful.
        

Coming to the issue. We have RH2288 x86_64 servers in our lab. We run HiBench 5( Hadoop bench marking tool)  on the servers.
One of the servers is dual booted with Ubuntu 15.04 and 16.04. On Ubuntu 15.04 the execution of HiBench 5 is perfect and no problem.


But on Ubuntu 16.04 HiBench execution is having problem . When the HiBench tool is run , it executes jobs on Hadoop environment.

The Hadoop jobs run for a while then suddenly the system hangs - means screen become black. When i disturb mouse the login prompt comes up.
After i enter details , it will login . Then the shell executing the program is not there. Again the system goes screen balck. When mouse disturbed the login prompt comes up.
When logged in  nothing is there . After few seconds the system goes screen black. This loop continues. The system Hangs for ever. At this time Hard reboot brings system back.

When the system rebooted there is no error information in logs. At least much i could not understand. The issue is always reproducible. 

Can any one help , this is critical for my work 

                     Thanks in Avance

---

### Post by howefield on 2016-11-21
Welcome to the forums, I've moved your thread to the "*Server Platforms*" forum where it is more likely to be seen by the experts who might understand the issue.

---

### Post by bmvsprasad on 2016-11-21
Thanks a lot

---

### Post by bmvsprasad on 2016-11-22
Hello All

    Even i can add more information if some body needs to analyse.

---

### Post by bmvsprasad on 2016-12-06
I found the reason Ubuntu 16.04 kill command  has bug . Hadoop yarn will create and kill containers . Yarn will kill Containers using command like 
yarn kill -15 processID    . But Kill command in Ubuntu 16.04 has bug such that when kill -15 -1xxx is given . It kills all the process whose groupID is 1.

Such that all the process ssh,cron jobs. systemd everything is killed. Thats why login shell is launched again.  

procps-3.3.10 has the buggy code. Downaload the procps-3.3.12.tar.xz source and make ,compile and install. The issue will be resolved.

---


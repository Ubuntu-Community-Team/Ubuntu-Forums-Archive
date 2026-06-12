---
title: "Server freezes"
date: 2013-07-04
forum: Server Platforms
---

### Post by torsson on 2013-07-04
Hello i have 3 servers 2 is identical Dell poweredge and 3d is Amd 3700+ and i have amlost the same setup on all 3, Postfix, lighttpd, mysql etc.

The problem is that all 3 servers freezes from time to time, nothing works http, mail ssh etc and the loggs dosen't say anything about what happends, i did a crontab every minute that logs free, netstat, ps top and w and i can't se what could be the problem.

i'll add some logs if anyone can help me with this problem.

[ATTACH]244389[/ATTACH][ATTACH]244390[/ATTACH][ATTACH]244391[/ATTACH][ATTACH]244392[/ATTACH][ATTACH]244393[/ATTACH]

---

### Post by DJ_Max on 2013-07-04
What logs did you check?

---

### Post by torsson on 2013-07-04
i checked syslog, kern.log dmesg lighttpd/error.log mail.log mysql.err

---

### Post by DJ_Max on 2013-07-04
So when it freezes, you can't connect to any port? Can you post the logs around the time it freezes. Is this a DHCP setup or static?

---

### Post by tgalati4 on 2013-07-04
Could be a router issue.  Run *iperf* against all three machines.  Check your cabling for stress or interference.

---

### Post by torsson on 2013-07-04
Ops, i posted the wrong ps, netstat, top, free, w files. here is the last of them. 

[ATTACH]244396[/ATTACH] [ATTACH]244397[/ATTACH] [ATTACH]244398[/ATTACH] [ATTACH]244399[/ATTACH] [ATTACH]244400[/ATTACH]

What logs do you want?. 

the only thing syslog says is 
```
Jul  4 05:39:01 gaslampa CRON[23745]: (root) CMD (/home/check.sh)Jul  4 05:40:01 gaslampa CRON[23755]: (root) CMD (/home/check.sh)
Jul  4 05:41:01 gaslampa CRON[23765]: (root) CMD (/home/check.sh)
Jul  4 05:42:01 gaslampa CRON[23775]: (root) CMD (/home/check.sh)
Jul  4 05:43:01 gaslampa CRON[23785]: (root) CMD (/home/check.sh)
Jul  4 05:44:01 gaslampa CRON[23795]: (root) CMD (/home/check.sh)
Jul  4 05:45:01 gaslampa CRON[23805]: (root) CMD (/home/check.sh)
Jul  4 05:46:01 gaslampa CRON[23815]: (root) CMD (/home/check.sh)
Jul  4 05:47:02 gaslampa CRON[23825]: (root) CMD (/home/check.sh)
Jul  4 05:48:01 gaslampa CRON[23835]: (root) CMD (/home/check.sh)
Jul  4 05:49:01 gaslampa CRON[23845]: (root) CMD (/home/check.sh)
Jul  4 05:50:01 gaslampa CRON[23855]: (root) CMD (/home/check.sh)
Jul  4 05:51:01 gaslampa CRON[23865]: (root) CMD (/home/check.sh)
Jul  4 05:52:01 gaslampa CRON[23875]: (root) CMD (/home/check.sh)
Jul  4 05:53:01 gaslampa CRON[23885]: (root) CMD (/home/check.sh)
Jul  4 05:54:01 gaslampa CRON[23895]: (root) CMD (/home/check.sh)
Jul  4 05:55:01 gaslampa CRON[23905]: (root) CMD (/home/check.sh)
Jul  4 05:56:01 gaslampa CRON[23915]: (root) CMD (/home/check.sh)
Jul  4 05:57:01 gaslampa CRON[23925]: (root) CMD (/home/check.sh)
Jul  4 05:58:01 gaslampa CRON[23935]: (root) CMD (/home/check.sh)
Jul  4 05:59:01 gaslampa CRON[23945]: (root) CMD (/home/check.sh)
Jul  4 06:00:01 gaslampa CRON[23955]: (root) CMD (/home/check.sh)
```

check.sh contains 
```


#!/bin/sh


mkdir -p /var/log/ssmonitor
date=`date +%H_%M`


top -b -n 1 > /var/log/ssmonitor/top_$date
netstat -anp > /var/log/ssmonitor/netstat_$date
ps -efww > /var/log/ssmonitor/ps_$date
free > /var/log/ssmonitor/free_$date
w > /var/log/ssmonitor/w_$date

```

and i added that to crontab after i noticed that the server die's

sorry for my bad english

---

### Post by torsson on 2013-07-04
Its a static ip, And 2 of the servers is in stockholm sweden and the 3d is in germany on a whole other isp.

---

### Post by DJ_Max on 2013-07-04
I assumed it was locally. How do you fix the freezing? Are you sure it's not a connectivity issue?

---

### Post by torsson on 2013-07-04
On the 2 servers in sweden i need to call the data center and ask them to reboot the servers and in germany i can reboot it from the web. the only thing the swedish and the german server is that i had the same domain connected to it, exept i got the german server 4 days ago and and installed postfix/clamvd mysql lighttpd. and pointed the domain to the german server

---

### Post by torsson on 2013-07-04
When the server/s fails i try ssh from my home computer, my phone and from my work computer (from work). a strange thing is that sins i pointed the domain to the german server i havent had the problem on the swedish servers

---

### Post by DJ_Max on 2013-07-04
When you tried to connect, did you try via the IP address?
Track the time(s) your server freezes, and look at the logs around that time.

Start from the first software packages you installed and work your way to the last checking that your configurations are correct.

---


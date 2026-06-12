---
title: "Crontab disabling internet from 7pm to 7am"
date: 2010-04-11
forum: Security
---

### Post by playcat on 2010-04-11
Hello,

I administer a desktop computer with ubuntu 8.04 in an university library. Since it works almost all night, to enable students to study, after some time I noticed some misuses of the computer during the evening, when there isn't many students. 

My goal was to disable users from accessing internet from 7pm to 7am, but also enable it if certain user was logged in (I use that user for torrent, and I seed on that computers from time to time).

So I created a script that's being called by root's crontab, and here is the script's code:

```
#!/bin/bash
NUM=`who|grep myuser|wc -l`
#echo $NUM
if [ $NUM -le 0 ]; then
        /sbin/ifconfig eth0 down
else
        /sbin/ifconfig eth0 up
fi

```

Since I created the script, I actually never seeded anything, so I'm wondering now if that's going to work at all, and (also) is there a better solution for this.

Thanks,
Dan

---

### Post by karthick87 on 2010-04-11
> **playcat said:**
> Hello,

I administer a desktop computer with ubuntu 8.04 in an university library. Since it works almost all night, to enable students to study, after some time I noticed some misuses of the computer during the evening, when there isn't many students. 

My goal was to disable users from accessing internet from 7pm to 7am, but also enable it if certain user was logged in (I use that user for torrent, and I seed on that computers from time to time).

So I created a script that's being called by root's crontab, and here is the script's code:

```
#!/bin/bash
NUM=`who|grep myuser|wc -l`
#echo $NUM
if [ $NUM -le 0 ]; then
        /sbin/ifconfig eth0 down
else
        /sbin/ifconfig eth0 up
fi

```Since I created the script, I actually never seeded anything, so I'm wondering now if that's going to work at all, and (also) is there a better solution for this.

Thanks,
Dan


Try using a proxy server,that will be better..!and it can set to block the usage on particular time..

---

### Post by playcat on 2010-04-11
> **getyourkarthick said:**
> Try using a proxy server,that will be better..!and it can set to block the usage on particular time..

Thank you for your answer ... Any particular proxy in mind?

---

### Post by HermanAB on 2010-04-11
Squid-cache.

Otherwise, look at PAM-time.

---

### Post by Agent ME on 2010-04-11
I think configuring iptables would be the best bet. With iptables you can control the connections of certain users (or groups) differently, and you could use root's crontab to change the settings as needed.

---

### Post by bodhi.zazen on 2010-04-12
> **HermanAB said:**
> Squid-cache.

Otherwise, look at PAM-time.

> **Agent ME said:**
> I think configuring iptables would be the best bet. With iptables you can control the connections of certain users (or groups) differently, and you could use root's crontab to change the settings as needed.

IMO, for a single desktop computer, use iptables. For a large LAN with multiple clients use squid.

iptables : [http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html](http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html)

squid : [http://www.deckle.co.za/squid-users-guide/Access_Control_and_Access_Control_Operators#Current_day.2Ftime](http://www.deckle.co.za/squid-users-guide/Access_Control_and_Access_Control_Operators#Current_day.2Ftime)

---


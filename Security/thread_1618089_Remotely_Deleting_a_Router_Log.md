---
title: "Remotely Deleting a Router Log"
date: 2010-11-10
forum: Security
---

### Post by cisforcojo on 2010-11-10
Hi All,

I have recently been the victim of identify theft and have coincidentally noticed that my router has been under attack for the past few days. I've been monitoring the log on my router (a D-Link DI-624+A) and suddenly while I was on Skype, my wireless connection was lost. I reconnected and found that the router's log had been erased. It appears from the log that the hacker has so far been unsuccessful but any advice on what I should do is greatly appreciated. I have already done a 'whois' on several of the IPs this hacker has been using and have notified the respective ISPs.

Is it possible to remotely delete a router log? 

Here's an example of my log before and after the delete:
```

Wed Nov 10 18:00:24 2010 Unrecognized attempt blocked from 221.136.83.1:40245 to xxx.xxx.xxx.xxx TCP:8080

Wed Nov 10 18:08:24 2010 Unrecognized attempt blocked from 60.173.26.168:6000 to xxx.xxx.xxx.xxx TCP:9415

Wed Nov 10 18:08:53 2010 Syn time: Wed Nov 10 18:08:53 2010

Wed Nov 10 18:08:55 2010 Unrecognized attempt blocked from 77.85.139.169:10865 to xxx.xxx.xxx.xxx UDP:13393

Wed Nov 10 18:10:02 2010 Unrecognized attempt blocked from 113.106.194.236:2769 to xxx.xxx.xxx.xxx UDP:47522

Wed Nov 10 18:12:49 2010 Unrecognized attempt blocked from 58.94.106.115:7403 to xxx.xxx.xxx.xxx UDP:13393

Wed Nov 10 18:28:35 2010 Unrecognized attempt blocked from 77.85.139.169:10865 to xxx.xxx.xxx.xxx UDP:13393

```

After delete:
```

-------------------------------------------------

              System Logs

-------------------------------------------------

Wed Nov 10 19:28:13 2010 Associated:  00-21-6A-96-CE-9E st=0

Wed Nov 10 19:28:15 2010 DOD:triggered internally

Wed Nov 10 19:28:15 2010 DHCP:discover()

Wed Nov 10 19:28:15 2010 DHCP:offer(116.88.192.1)

Wed Nov 10 19:28:15 2010 DHCP:request(xxx.xxx.xxx.xxx)

Wed Nov 10 19:28:15 2010 DHCP:ack(DOL=14400,T1=7200,T2=12600)

Wed Nov 10 19:28:18 2010 Unrecognized attempt blocked from 130.232.144.36:59951 to xxx.xxx.xxx.xxx UDP:48684

Wed Nov 10 19:28:23 2010 Unrecognized attempt blocked from 130.232.144.36:59951 to xxx.xxx.xxx.xxx UDP:48684

Wed Nov 10 19:28:25 2010 ICMP: type 3 code 1 from 90.215.132.35

Wed Nov 10 19:28:25 2010 ICMP: type 3 code 1 from 90.215.132.35

Wed Nov 10 19:28:25 2010 Unrecognized attempt blocked from 130.232.144.36:59951 to xxx.xxx.xxx.xxx UDP:48684

Wed Nov 10 19:28:29 2010 Unrecognized attempt blocked from 130.232.144.36:59951 to xxx.xxx.xxx.xxx UDP:48684

Wed Nov 10 19:28:31 2010 ICMP: type 3 code 1 from 90.215.132.35

Wed Nov 10 19:28:42 2010 Syn time: Wed Nov 10 19:28:42 2010

Wed Nov 10 19:28:50 2010 Unrecognized attempt blocked from 77.85.139.169:10865 to xxx.xxx.xxx.xxx UDP:13393

Wed Nov 10 19:30:08 2010 Unrecognized attempt blocked from 193.120.212.15:48692 to xxx.xxx.xxx.xxx UDP:48684

Wed Nov 10 19:30:10 2010 Unrecognized attempt blocked from 193.120.212.15:48692 to xxx.xxx.xxx.xxx UDP:48684

Wed Nov 10 19:31:13 2010 TX TCP reset for 192.168.0.161(63979) -> 192.168.0.1(63979)

Wed Nov 10 19:31:13 2010 TX TCP reset for 192.168.0.161(64235) -> 192.168.0.1(64235)

Wed Nov 10 19:31:13 2010 TX TCP reset for 192.168.0.161(64491) -> 192.168.0.1(64491)

Wed Nov 10 19:31:13 2010 TX TCP reset for 192.168.0.161(64747) -> 192.168.0.1(64747)

Wed Nov 10 19:31:13 2010 TX TCP reset for 192.168.0.161(65003) -> 192.168.0.1(65003)

Wed Nov 10 19:32:05 2010 Unrecognized attempt blocked from 193.120.212.15:48692 to xxx.xxx.xxx.xxx UDP:48684

Wed Nov 10 19:32:07 2010 Unrecognized attempt blocked from 193.120.212.15:48692 to xxx.xxx.xxx.xxx UDP:48684


```

Thanks for any advice you can give!

---

### Post by CharlesA on 2010-11-10
Unless you have the router set to be administered remotely, it shouldn't be possible to mess with anything on the router from the internet side.

It's more then likely that the log reached the maximum size and was purged.

---


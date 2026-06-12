---
title: "Appache and ssh stop working periodically until reboot while the server is alive"
date: 2018-11-24
forum: Server Platforms
---

### Post by elnaw on 2018-11-24
Hi guys!
I am wondering what might cause this. While I was working on the server 16.04 remotely  suddenly it ssh and appache2 stopped working for no reason I know. I can ping the machine and there is a reply but Apache gives the following error:
[h=1]This site can’t be reached[/h][COLOR=#646464][FONT=&quot]**xx.xxx.xxx.xxx** refused to connect.
ERR_CONNECTION_REFUSED

anD THE SSH GIVES THE FOLLOWING ERROR:
[/FONT][/COLOR]
ssh: connect to host **xx.xxx.xxx.xxx** port 22: Connection refused.
I suspected to be a CRON job or something to do with UFW but I didn't do any CRON job nor changed something in the firewall.
If any one came through a such problem please hep.
Thank you.


[COLOR=#646464][FONT=&quot]
[/FONT][/COLOR]

---

### Post by TheFu on 2018-11-24
I would connect through a remote console connection and check the log files.

---

### Post by charlesssmith6 on 2018-11-29
How can we make it to run normally. I was unable to managing it. Any suggestions guyz

---


---
title: "firewall logs"
date: 2010-02-16
forum: Security
---

### Post by andremta on 2010-02-16
Hi guys!

I have ufw and fwlogwatch installed on a 9.10 server.

How can I view the firewall logs on a specific port? Example: ssh 22 port.

---

### Post by yogesh.girikumar on 2010-02-18
Hi,
       You can do this to find activity related to port 22. You can replace 22 with other port numbers. But not all traffic is logged with port numbers.
   ```
$ cat /var/log/messages | grep UFW | grep "DPT=22" 
```      Also try the log files:
       /var/log/rsyslog or syslog
/var/log/kern.log


       DPT stands for > Destination Port.
SPT > Source port


   You can do 
```
$ cat /var/log/messages | grep "UFW" | more
```      to view and get a basic idea of the format of the logs.
   Please make sure that logging is "turned on" for ufw.
```
$ sudo ufw loggin on
```Also make sure that the logging is set to the appropriate level as per your requirements. See the man page for more info .

```
$ man ufw
```     To find out where the various levels of logs are maintained, you can open the /etc/rsyslog.d/50-default.conf file
       

Hope this is helpful..

---


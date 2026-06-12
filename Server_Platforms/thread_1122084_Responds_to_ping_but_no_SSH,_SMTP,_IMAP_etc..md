---
title: "Responds to ping but no SSH, SMTP, IMAP etc."
date: 2009-04-10
forum: Server Platforms
---

### Post by DannyW on 2009-04-10
Hello

I have a server with some hosting company and have been using it as an email server and webserver for some time.

I use it for IMAP, SMTP, HTTP, SSH, DNS.


All was fine for around 95 days and then today I was unable to access email or http server. I tried to ssh to the server but it would not connect. However, I **could** still ping it.

To resolve the problem I rebooted the server, but it happened again later that day. The only thing that has changed is I added 3 more email accounts to the server (there are a total of 5 now, over 4 domanis) a few days ago, but I'm not sure if/how this could cause problems.

I don't expect someone to fix this for me, and understand it could be one of many things. But I'm no expert. If someone could tell me how to debug the problem or what log files to check, I would be very grateful.



Thanks in advance,
Danny

---

### Post by zaicic on 2009-04-11
Check your logs, maybe some process has started to use so much memory, and the kernel started to kill other processes to free memory.

There are thousands of things that may broke and cause your problem, check the logs first and see if you find anything suspicious.

---

### Post by DannyW on 2009-04-11
> **zaicic said:**
> Check your logs, maybe some process has started to use so much memory, and the kernel started to kill other processes to free memory.

There are thousands of things that may broke and cause your problem, check the logs first and see if you find anything suspicious.


Thanks for your response. It has happened 3 times over the past 2 days and I've been trying to find something suspicious in the logs but I'm afraid I've found nothing.

/var/log/syslog has lots of cron and postfix messages, nothing unusual and then nothing between 1:30am and 9:30am (when I rebooted).

I'm not sure where any messages about processes being killed would go.

/var/log/kern.log and /var/log/dmesg only have lines from when the server was booting up. No later messages from the kernel. Am I looking in the right place?



Thanks, and I look forward to any more help anyone can give me.

---

### Post by zaicic on 2009-04-11
The kernel logs should be in /var/log/dmesg and if you say that you don't spot any weird lines there that means it's not that problem.

I don't know what's the problem, but you may create a script that minutely gets the system information and stores on the local drive. You should store information about memory stats, running applications, and network (routes, iptables, etc), etc


Take a look here [1] to see how to create loop with bash. With "sleep 1m" you may delay the script for one minute.


Ex. 
"route -n > "/root/logs/route_`date`""


Success!

):P

[1] [http://www.cyberciti.biz/faq/bash-while-loop/](http://www.cyberciti.biz/faq/bash-while-loop/)

---


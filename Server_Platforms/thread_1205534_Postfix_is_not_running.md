---
title: "Postfix is not running"
date: 2009-07-06
forum: Server Platforms
---

### Post by xiaomahe on 2009-07-06
Hi, i have been trying to install postfix on my ubuntu 8.10

i have setup bind9 so that secure.sec is working on my localhost address

after that, i used dig secure.sec and this is the result

; <<>> DiG 9.5.0-P2 <<>> secure.sec
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32863
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;secure.sec.			IN	A

;; ANSWER SECTION:
secure.sec.		86400	IN	A	127.0.0.1

;; AUTHORITY SECTION:
secure.sec.		86400	IN	NS	secure.sec.

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Jul  6 16:59:51 2009
;; MSG SIZE  rcvd: 58

now when it comes to Postfix installation, i followed this guide  [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

and so my configuration is:

General type of mail configuration: Internet Site
NONE doesn't appear to be requested in current config
System mail name: mail.secure.sec
Root and postmaster mail recipient: Dave
Other destinations for mail: mail.secure.sec, ming-laptop, localhost.localdomain, localhost
Force synchronous updates on mail queue?: No
Local networks: 127.0.0.0/8
Yes doesn't appear to be requested in current config
Mialbox size limit (bytes): 0
Local address extension character: +
Internet protocols to use: all

i tried to telnet localhost 25
and it seems that the port is closed because it says "unable to connect to remote host: connection refused"

and so i check using nmap localhost and i cant see my port 25 is open.

I tried to see if postfix already running or not by using sudo service --status-all

And the result is  
* PCMCIA bridge driver already present in kernel
Usage:  {start|stop|restart|force-reload}
 * postfix is not running
 * Usage: /etc/init.d/powernowd {start|stop|restart|force-reload}
 * Usage: /etc/init.d/powernowd {start|stop|restart|force-reload}

it seems that postfix is not running, hence port 25 is closed because no application is listen to that port, am i right? correct me if i am wrong.

and here is my mail.info logs
Jul  6 14:54:46 ming-laptop postfix/master[5490]: fatal: open lock file /var/lib/postfix/master.lock: cannot open file: Permission denied
Jul  6 15:01:01 ming-laptop authdaemond: stopping authdaemond children
Jul  6 16:10:11 ming-laptop postfix/master[7993]: fatal: open lock file /var/lib/postfix/master.lock: cannot open file: Permission denied
Jul  6 16:29:44 ming-laptop postfix/master[9533]: fatal: open lock file /var/lib/postfix/master.lock: cannot open file: Permission denied
Jul  6 16:36:09 ming-laptop postfix/master[10147]: fatal: open lock file /var/lib/postfix/master.lock: cannot open file: Permission denied
Jul  6 16:45:47 ming-laptop postfix/master[12585]: fatal: open lock file /var/lib/postfix/master.lock: cannot open file: Permission denied
Jul  6 16:49:49 ming-laptop postfix/master[12872]: fatal: open lock file /var/lib/postfix/master.lock: cannot open file: Permission denied
Jul  6 17:03:27 ming-laptop postfix/master[13866]: fatal: open lock file /var/lib/postfix/master.lock: cannot open file: Permission denied
Jul  6 17:04:09 ming-laptop postfix/master[14166]: fatal: open lock file /var/lib/postfix/master.lock: cannot open file: Permission denied


can anyone help me to solve this?? i need to setup my mail server soon, because i need to test my webmail application, and without this mail server my application cant start sending and receiving message


Please help me

---


---
title: "connect to smtp.xxx.com[1.2.3.4]: Connection timed out (port 25)"
date: 2008-10-30
forum: Server Platforms
---

### Post by sahabcse on 2008-10-30
Dear Sir,

I have installed ubuntu 8.04 server edition and Zimbra Collaboration Suite for mail server. I have followed the instruction of ZCS and change the port of http 80 to 8000 for avoiding the port conflict. Now I can send and receive mail locally without any issue. Also I can able to send out side also like gmail.... But the issue whenever I try to send mail from external server (gmail to my domain) that time I am getting 
==================================================================
"connect to smtp.xxx.com[1.2.3.4]: Connection timed out (port 25)". 
==================================================================
My domain name is xxxxx.in. I have throughly check the DNS side here MX record has no problem. So I suspect to ask weather ISP block port 25, they also didn't block the port number 25. Then I can able to connect telnet localhost 25, But I can't able to connect telnet xxxxt.in 25. Then the nmap of xxxx.in shows 
============================================
PORT     STATE SERVICE

25/tcp   targeted  smtp
============================================
Then I tried to open the port 26 for smtp , that time I can able to connect telnet xxxx.in 26. But nmap result showing 
========================
26/tcp  open unknown
=======================
The error lg information from another server to xxxx.in is given below.

=============================================================
Oct 29 14:04:58 GIS postfix/smtp[16602]: connect to smtp.xxxxx.in[12.166.40.27]: Connection timed out (port 25)
Oct 29 14:04:58 GIS postfix/smtp[16602]: 8208FFFD9: to=<admin@xxxxx.in>, relay=none, delay=30, delays=0.07/0.01/30/0, dsn=4.4.1, status=deferred (connect to smtp.xxxx.in[12.166.40.27]: Connection timed out)
================================================================
I refer some forum and found that default some firewall (ufw) comes in ubuntu 8.04. I am facing this issue last two weeks of time. Kindly help me regarding this issue.

Thanks and regards
Sahab

---

### Post by Wayne_V on 2008-10-30
Not familiar with ZCS, but check the following:

# lsof -i :25
(should see sendmail listening on port 25 -- unless ZCS overrides)

# netstat -a | grep smtp
(should see sendmail again -- if it says localhost:smtp, see the next line)

# cd /etc/mail
# grep DAEMON_OPTIONS sendmail.mc

If it says Addr=127.0.0.1 then you are only listening on the loopback.  Modify either sendmail.mc or sendmail.cf to correct.

btw - I cannot telnet to smtp.rctjct.in port 25 -- appears to be blocked.

---

### Post by sahabcse on 2008-11-01
Thanks for your update. Now the Issue is my system smtp port is in filter state. When I am given namp localhost means it is in open sate. The details is given below.

===========================================
root@xxxx:~# nmap localhost

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-11-01 18:14 IST
Interesting ports on localhost.localdomain (127.0.0.1):
Not shown: 1698 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
110/tcp  open  pop3
139/tcp  open  netbios-ssn
143/tcp  open  imap
445/tcp  open  microsoft-ds
465/tcp  open  smtps
953/tcp  open  rndc
993/tcp  open  imaps
995/tcp  open  pop3s
2000/tcp open  callbook
3306/tcp open  mysql
5432/tcp open  postgres

Nmap done: 1 IP address (1 host up) scanned in 0.262 seconds
====================================================
====================================
[root@localhost ~]# nmap xxxx.in

Starting Nmap 4.11 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2008-11-01 17:09 IST
Interesting ports on 122.166.40.27:
Not shown: 1656 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
25/tcp   filtered smtp
26/tcp   open     unknown
53/tcp   open     domain
67/tcp   filtered dhcps
68/tcp   filtered dhcpc
80/tcp   open     http
110/tcp  open     pop3
135/tcp  filtered msrpc
136/tcp  filtered profile
137/tcp  filtered netbios-ns
138/tcp  filtered netbios-dgm
139/tcp  filtered netbios-ssn
143/tcp  open     imap
389/tcp  open     ldap
445/tcp  filtered microsoft-ds
465/tcp  open     smtps
993/tcp  open     imaps
995/tcp  open     pop3s
1080/tcp filtered socks
2000/tcp open     callbook
3128/tcp filtered squid-http
6588/tcp filtered analogx

Nmap finished: 1 IP address (1 host up) scanned in 48.984 seconds
================================================================

I have purge the UFW firewall. Then also same issue is occur. Kindly help me regarding this issue.

---

### Post by meso34 on 2009-01-11
Hi there,

i have the same issue. I installed Ubuntu Server 8.04 znd Zimbra 5.0.11.

Any progress about solving this???

---

### Post by sahabcse on 2009-03-30
Finally I have find out the error. The issue due to ISP blocked the smtp port 25.  Now they open the port and the issue is resolved.

---


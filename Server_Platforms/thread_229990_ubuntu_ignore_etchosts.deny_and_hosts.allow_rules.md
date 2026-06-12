---
title: "ubuntu ignore /etc/hosts.deny and hosts.allow rules"
date: 2006-08-05
forum: Server Platforms
---

### Post by Sir_Yaro on 2006-08-05
```
[yaro][~]$ cat /etc/hosts.deny|grep -v '#'

portmap: ALL
ALL: ALL
apache2: ALL
[yaro][~]$

``````
[yaro][~]$ cat /etc/hosts.allow|grep -v '#'
ALL: 127.0.0.1
[yaro][~]$   
```

result of scan on remote host outside my network
```
$  nmap -p 80,111,21 MY_ADDRESS

Starting nmap 3.93 ( http://www.insecure.org/nmap/ ) at 2006-08-05 13:54 CEST
Interesting ports on MY_ADDRESS:
PORT    STATE SERVICE
21/tcp  open  ftp
80/tcp  open  http
111/tcp open  rpcbind

Nmap finished: 1 IP address (1 host up) scanned in 0.533 seconds
$

```

in general doesn't matter what I write into both files. ubuntu seems to ignore those rules completely and it allows to connect anybody from anywhere...

Does enybody have a clue how to fix it ???](*,)

---

### Post by Randomskk on 2006-08-07
I believe hosts.allow seems to be read more than others - you can put DENY rules in there, such as:
ftp: ALL : DENY

Check out Bastille Linux too, it's a program that will lock down parts of your system and includes rules in hosts.allow and hosts.deny.

Also when you portscan yourself you're on a local interface, which may be inherently trusted (try scanning from another computer, if you're not already)

---

### Post by LordHunter317 on 2006-08-10
You don't understand how tcpd works.  If you're using libwrap, the server application must explcitly ask for a hosts.allow/hosts.deny check.  Many don't do it on the inital connect.

Besides, use of hosts.allow and hosts.deny is optional anyway.  Not all software supports it.

---


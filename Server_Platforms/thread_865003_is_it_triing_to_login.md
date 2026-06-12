---
title: "is it triing to login?"
date: 2008-07-20
forum: Server Platforms
---

### Post by q.dinar on 2008-07-20
in syslog:
Jul 20 16:10:48 qdb-desktop tcpspy[5489]: connect: user qdb, local 89.232.85.48:35615, remote 140.211.166.95:www
Jul 20 16:10:48 qdb-desktop tcpspy[5489]: connect: user qdb, local 89.232.85.48:35616, remote 140.211.166.95:www
Jul 20 16:10:48 qdb-desktop tcpspy[5489]: connect: user qdb, local 89.232.85.48:35617, remote 140.211.166.95:www
Jul 20 16:10:49 qdb-desktop tcpspy[5489]: disconnect: user qdb, local 89.232.85.48:35615, remote 140.211.166.95:www
Jul 20 16:10:49 qdb-desktop tcpspy[5489]: disconnect: user qdb, local 89.232.85.48:35616, remote 140.211.166.95:www
Jul 20 16:10:49 qdb-desktop tcpspy[5489]: disconnect: user qdb, local 89.232.85.48:35617, remote 140.211.166.95:www

in daemon.log:
Jul 20 16:12:20 qdb-desktop tcpspy[5489]: connect: user qdb, local 89.232.85.48:38274, remote 140.211.166.95:www
Jul 20 16:12:20 qdb-desktop tcpspy[5489]: connect: user qdb, local 89.232.85.48:38275, remote 140.211.166.95:www
Jul 20 16:12:20 qdb-desktop tcpspy[5489]: connect: user qdb, local 89.232.85.48:33637, remote 74.125.79.127:www
Jul 20 16:12:23 qdb-desktop tcpspy[5489]: disconnect: user qdb, local 89.232.85.48:38277, remote 140.211.166.95:www
Jul 20 16:12:23 qdb-desktop tcpspy[5489]: disconnect: user qdb, local 89.232.85.48:38276, remote 140.211.166.95:www
Jul 20 16:12:23 qdb-desktop tcpspy[5489]: disconnect: user qdb, local 89.232.85.48:38274, remote 140.211.166.95:www

i want to use [ code] tag  but there are no tooltips of buttons.

it is when "tcpspy" is installed.

also other type messages are there:
Jul 20 16:13:20 qdb-desktop portsentry[5809]: attackalert: Connect from host: 213.234.219.107/213.234.219.107 to TCP port: 1080
Jul 20 16:13:20 qdb-desktop portsentry[5809]: attackalert: Host: 213.234.219.107 is already blocked. Ignoring
Jul 20 16:13:20 qdb-desktop portsentry[5809]: attackalert: Connect from host: 213.234.219.107/213.234.219.107 to TCP port: 1080
Jul 20 16:13:20 qdb-desktop portsentry[5809]: attackalert: Host: 213.234.219.107 is already blocked. Ignoring
also in syslog and daemon.log.
this computer has external ip adress.

---

### Post by q.dinar on 2008-07-20
oh! i have knew out it is phpbb.com! also there are: 72.14.217.127, 74.125.79.190, 72.14.215.99, 74.125.79.91 - "google tatarca"(my language). not. it is because my browser's "accept language" i think. also 80.237.211.64 "www.ip-adress.com".
this is sites that i have just opened. may be this is not bruteforcing!

---

### Post by windependence on 2008-07-20
If you had a brute force attack you would certainly know. You shouldn't get upset if this is your log and your box has no hardware firewall in front of it. I run some production web sites and trust me, they try every day, all day to get in using automated bots and scripts. Don't worry about it. Just don't make your passowrds a dictionary word (use numbers, symbols, and mixed case) and the same with your user names. Don't hand it to them on a platter by giving them half of it by using a common user name. Be creative.

-Tim

---


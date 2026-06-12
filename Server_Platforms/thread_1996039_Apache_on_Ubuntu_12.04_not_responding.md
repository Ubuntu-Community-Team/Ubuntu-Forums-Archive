---
title: "Apache on Ubuntu 12.04 not responding"
date: 2012-06-03
forum: Server Platforms
---

### Post by seafowl on 2012-06-03
Hey guys.
This is what's going on:
The server was running really slow few months back, and as it's just a personal blog server I didn't pay much attention to it. However just for fun I upgraded it to 12.04 using do-release-upgrade. Problem then comes after the upgrade. Everything seems to work perfectly fine except apache.
I have OpenSSH enabled (lol of course), I also installed proftpd. The SSH and FTP work perfectly well but the apache is just not responding at all.
I have it behind a router. I've already set the router to route every port to my server. 
Please help.

Thanks very much.

---

### Post by nsnidanko on 2012-06-04
You start by looking at logs.
Do **sudo service apache restart**
and check files in /var/log/apache2 for some errors. also check access log to make sure it sees the request.

If nothing there and service starts ok check if you can telnet to port 80 (or whatever port your apache is listening to) from localhost -> fails check local iptables

Try to access from the same network where your server located -> fails check your iptables

try access from outside -> fails: check your router and make sure upstream provider doesn't block port 80

---

### Post by seafowl on 2012-06-05
> **nsnidanko said:**
> You start by looking at logs.
Do **sudo service apache restart**
and check files in /var/log/apache2 for some errors. also check access log to make sure it sees the request.

If nothing there and service starts ok check if you can telnet to port 80 (or whatever port your apache is listening to) from localhost -> fails check local iptables

Try to access from the same network where your server located -> fails check your iptables

try access from outside -> fails: check your router and make sure upstream provider doesn't block port 80

I did sudo service apache2 restart and same problem.
It's the same thing as /etc/init.d/apache2 restart isn't it?

I tried to telnet from localhost, no problem. It says
```

root@Web-Server:/home/steven# telnet localhost 80
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
exit

```

I tried to telnet from internet, it says 
```

Connecting to (my server address)... Could not open connection to the host, or port 80: Connect failed

```

I'm absolutely sure my ISP isn't blocking port 80 as I have an Array VPN server running on a different IP address, and it's running flawlessly.. well. almost :)

What component of the router should I check? The DMZ host settings?

---

### Post by maverickaddicted on 2012-06-05
Execute the following commands and paste the output of following commands to get more clear idea about the problem.

1) ```
sudo service apache2 restart
```

2) ```
sudo tail /var/log/apache2/error.log
```

---

### Post by seafowl on 2012-06-05
> **maverickaddicted said:**
> Execute the following commands and paste the output of following commands to get more clear idea about the problem.

1) ```
sudo service apache2 restart
```

2) ```
sudo tail /var/log/apache2/error.log
```

```

root@Web-Server:/home/steven# service apache2 restart
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]
root@Web-Server:/home/steven#

```

```
root@Web-Server:/home/steven# tail /var/log/apache2/error.log
[Mon Jun 04 08:37:44 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 04 08:38:56 2012] [notice] caught SIGTERM, shutting down
[Mon Jun 04 08:38:57 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 04 08:49:38 2012] [notice] caught SIGTERM, shutting down
[Mon Jun 04 08:49:40 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.1 with Suhosin-Patch configured -- resuming normal operations
[Tue Jun 05 14:10:37 2012] [notice] caught SIGTERM, shutting down
[Tue Jun 05 14:10:39 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.1 with Suhosin-Patch configured -- resuming normal operations
[Tue Jun 05 14:12:33 2012] [error] [client 127.0.0.1] Invalid method in request exit
[Tue Jun 05 16:04:03 2012] [notice] caught SIGTERM, shutting down
[Tue Jun 05 16:04:05 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.1 with Suhosin-Patch configured -- resuming normal operations
root@Web-Server:/home/steven#

```

---

### Post by nsnidanko on 2012-06-16
> **seafowl said:**
> I did sudo service apache2 restart and same problem.
It's the same thing as /etc/init.d/apache2 restart isn't it?

I tried to telnet from localhost, no problem. It says
```

root@Web-Server:/home/steven# telnet localhost 80
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
exit

```I tried to telnet from internet, it says 
```

Connecting to (my server address)... Could not open connection to the host, or port 80: Connect failed

```I'm absolutely sure my ISP isn't blocking port 80 as I have an Array VPN server running on a different IP address, and it's running flawlessly.. well. almost :)

What component of the router should I check? The DMZ host settings?

It has to be your router blocking something or if you have NAT than port forwarding is not configured properly. Can you, please advise how your server connects to the internet?

---


---
title: "Open ports"
date: 2007-01-12
forum: Server Platforms
---

### Post by aresgunther on 2007-01-12
Hello.  I just installed ubuntu about a month ago, and I just started worrying about security.  I tried a Nmap scan on my machine, and got this report:

```

<user>@daedalus:~$ sudo nmap -sS -sV localhost

Starting Nmap 4.20 ( http://insecure.org ) at 2007-01-12 20:29 MST
Interesting ports on localhost (127.0.0.1):
Not shown: 1693 closed ports
PORT      STATE SERVICE    VERSION
22/tcp    open  tcpwrapped
25/tcp    open  smtp       Exim smtpd 4.60
631/tcp   open  ipp        CUPS 1.2
10000/tcp open  http       Webmin httpd

Service detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap finished: 1 IP address (1 host up) scanned in 6.825 seconds

```

I do have firestarter, but I am not sure if these ports can be closed through it.  I really don't want *any* open ports.  I don't use smtp, ipp(I don't think, anyway), or the http server.  How can I configure these ports to close?


ares

---

### Post by gombadi on 2007-01-12
Some observations -

A default install of ubuntu does not install an email server and if it did it would be postfix and not exim. Same applies for Webmin.

When were these installed? 

The first rule of making a computer safe - If you are not using a service then remove it.

Another point - It looks like you did the nmap on localhost. Any open ports on this ip address are not open to the world but only the local machine. May pay to run the command again but use something like "sudo nmap -sS -sV 192.168.1.1" or what ever your ip address is.

Another useful command to run is "sudo netstat -plntu"
It will show what programs are listening on what ports and on what interfaces i.e.localhost or the world.

Don't use firestarter but it should be able to close any port.

Have fun,
Lyndsay.

---

### Post by aresgunther on 2007-01-13
Okay, I scanned my network address and got:

```

Starting Nmap 4.20 ( http://insecure.org ) at 2007-01-13 08:56 MST
Interesting ports on 192.168.0.17:
Not shown: 1695 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
10000/tcp open  snet-sensor-mgmt

```

I tried telnetting to the ports listed when I scanned localhost, but they are closed from the outside.  So as of now, I just have ports open, 22 and 10000.  I tried a ps -A and found the service the ssh daemon was running on, and killed it.  Next, I tried netstat -plntu :

```

<user>@daedalus:~$ sudo netstat -plntu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:49033         0.0.0.0:*               LISTEN     4588/hpiod
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     5411/perl
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5663/cupsd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     4895/exim4
tcp        0      0 127.0.0.1:48828         0.0.0.0:*               LISTEN     4593/python
udp        0      0 0.0.0.0:10000           0.0.0.0:*                          5411/perl
udp        0      0 0.0.0.0:68              0.0.0.0:*                          5431/dhclient3
udp        0      0 0.0.0.0:68              0.0.0.0:*                          3782/dhclient3

```

That showed that the other open port (10000) was perl running the process id 5411, so I killed that too.  Another nmap scan showed that I had no ports open. 

How can I have these processes not run on startup?


ares

---

### Post by gombadi on 2007-01-13
The first rule of making a computer safe - If you are not using a service then remove it.

If you are not using ssh to connect to the machine then use your favorite package management tool (apt-get, aptutude or synaptic) to remove it. I myself would use 
"apt-get remove --purge -s ssh" and if all looks good then run it again without the -s

As for webmin (port 10000) how did it get installed? I can not find it in the package management system. It may have an uninstall script of its own. Another option is to run "sudo update-rc.d webmin remove" which will remove the startup links so it does not start on system boot. The only problem is the program files are still on your disk. Someone else may have a better solution.

Have fun,
Lyndsay

---

### Post by aresgunther on 2007-01-13
Well, I found the webmin package and uninstalled it.  I must have different repositories than you.  Anyway, I decided to keep ssh and now that is the only port I have open.  

Thanks for the help.


ares

---


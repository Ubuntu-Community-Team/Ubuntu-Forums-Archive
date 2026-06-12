---
title: "Confused by UFW"
date: 2008-05-10
forum: Security
---

### Post by Vadi on 2008-05-10
Hi all,

I need to open the port 2078 on my laptop, because I want to use Nautilus to access my server's web disk. The link they say to paste in Nautilus location bar is "https://vadisystems.com:2078", but they also say "Note: Ports 2078 (SSL) or 2077 (non-SSL) will need to be allowed on your computer's firewall to use the Web Disk.". Nautilus atm can't access the web disk, it just times out.

So I tried adding two ufw rules from my computer to the server. I presume it's IP is "207.162.215.8", since that's what "ping vadisystems.com" says. So I added these two fules in ufw:

> vadi@ubuntu-laptop:~$ sudo ufw status
Firewall loaded

To                         Action  From
--                         ------  ----
207.162.215.8 2078:tcp     ALLOW   127.0.0.1 2078:tcp
207.162.215.8 2078:udp     ALLOW   127.0.0.1 2078:udp

vadi@ubuntu-laptop:~$

However Nautilus still cannot access it. I also tried doing "ping 207.162.215.8 2078" in the terminal, and no packets were getting through. 

Can anyone point out where did I mess up please?

---

### Post by Monicker on 2008-05-10
Are you trying to connect to 207.162.215.8 from a dfferent computer/ip address? I haven't really used ufw, but your rules look like they are only allowing connections from localhost to that port.

---

### Post by Vadi on 2008-05-10
Yeah, I'm doing this all on my computer.

---

### Post by Monicker on 2008-05-10
Hrmm. I would think the firewall rules would not be necessary then.

What happens if you run these commands?
```

nc localhost 2078

HEAD localhost 2078
```

Can you also temporarily turn off ufw and try them?

---

### Post by Vadi on 2008-05-10
Here you go:

> vadi@ubuntu-laptop:~$ nc localhost 2078
localhost [127.0.0.1] 2078 (?) : Connection refused
vadi@ubuntu-laptop:~$ HEAD localhost 2078
500 Can't connect to localhost:80 (connect: Connection refused)
Content-Type: text/plain
Client-Date: Sat, 10 May 2008 13:51:17 GMT
Client-Warning: Internal response

200 OK
Connection: Keep-Alive
Date: Sat, 10 May 2008 13:51:17 GMT
Server: Oversee Webserver v1.3.18
Content-Type: text/html
Client-Date: Sat, 10 May 2008 13:51:18 GMT
Client-Peer: 208.73.212.12:80
Client-Response-Num: 1
Keep-Alive: timeout=15, max=100
Set-Cookie: parkinglot=1; domain=.2078.com; path=/; expires=Sun, 11-May-2008 13:51:17 GMT

vadi@ubuntu-laptop:~$ ufw

Usage: ufw COMMAND

Commands:
  enable			Enables the firewall
  disable			Disables the firewall
  default ARG			set default policy to ALLOW or DENY
  logging ARG			set logging to ON or OFF
  allow|deny RULE		allow or deny RULE
  delete allow|deny RULE	delete the allow/deny RULE
  status			show firewall status
  version			display version information

vadi@ubuntu-laptop:~$ sudo ufw disable
[sudo] password for vadi: 
Firewall stopped and disabled on system startup
vadi@ubuntu-laptop:~$ nc localhost 2078
localhost [127.0.0.1] 2078 (?) : Connection refused
vadi@ubuntu-laptop:~$ HEAD localhost 2078
500 Can't connect to localhost:80 (connect: Connection refused)
Content-Type: text/plain
Client-Date: Sat, 10 May 2008 13:51:37 GMT
Client-Warning: Internal response

200 OK
Connection: Keep-Alive
Date: Sat, 10 May 2008 13:51:36 GMT
Server: Oversee Webserver v1.3.18
Content-Type: text/html
Client-Date: Sat, 10 May 2008 13:51:37 GMT
Client-Peer: 208.73.212.12:80
Client-Response-Num: 1
Keep-Alive: timeout=15, max=100
Set-Cookie: parkinglot=1; domain=.2078.com; path=/; expires=Sun, 11-May-2008 13:51:36 GMT

vadi@ubuntu-laptop:~$ 


---

### Post by Monicker on 2008-05-10
Oops on my part.  I guess you can't specify the port with HEAD.  But its interesting that netcat still got connection refused for port 2078 with ufw turned off.

Does "sudo netstat -anltp|grep 2078" show a process listening?

---

### Post by Vadi on 2008-05-10
No, it just returns the prompt again.

---

### Post by Monicker on 2008-05-10
Sounds like the web server needs to be started then.

If its apache - sudo /etc/init.d/apache2 start

---

### Post by Vadi on 2008-05-10
I can't do that, it's a shared account or whatever.

I can email them about it though, what should I ask?

---

### Post by Monicker on 2008-05-10
I'm confused about what you are doing now.  Are you connecting to a remote host, or your laptop?  If its your laptop, then you should know which application your are running that requires port 2078 to be open, and you should be able to start it.

Also, is the public ip of 207.162.215.8 actually used by your laptop?  What is the output of the ifconfig command?

---

### Post by Vadi on 2008-05-10
I'm trying to connect to my web server, "vadisystems.com".

---

### Post by Monicker on 2008-05-10
Well, that alone does not make it any clearer.  And you did not answer my other questions.

---

### Post by Vadi on 2008-05-10
Well, no, since you were way off and I thought that would do it.

Are you connecting to a remote host, or your laptop?
**Remote host.**

If its your laptop, then you should know which application your are running that requires port 2078 to be open, and you should be able to start it.
**Doesn't apply.**


Also, is the public ip of 207.162.215.8 actually used by your laptop?
**No, it's my websites ip.**

 What is the output of the ifconfig command?

> vadi@ubuntu-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:69:49:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:1b:38:69:49:d1  
          inet addr:169.254.7.0  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9894446 (9.4 MB)  TX bytes:9894446 (9.4 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:9b:ae:35  
          inet addr:192.168.2.204  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe9b:ae35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:341296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:386028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:209563201 (199.8 MB)  TX bytes:335660491 (320.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-9B-AE-35-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vadi@ubuntu-laptop:~$ 


wlan0 is what's being used for wireless I believe, I don't use any other.

---

### Post by Monicker on 2008-05-10
Okay.  My fault for assuming you were talking about your laptop instead of connecting to a remote site from it.

Call you hosting provider and tell them your site is not reachable on port 2078.  If you are sure about which ports you should be using, then its possible that someone at the isp inadvertently altered the configuration for your virtual host.

---


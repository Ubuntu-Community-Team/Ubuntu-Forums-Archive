---
title: "[SOLVED] A Question about Ports . . ."
date: 2008-11-01
forum: Security
---

### Post by philliptweedie on 2008-11-01
I'll quickly describe my home network.

1 Netgear Router - No ports being forwarded
1 Desktop w/ SSH Server
1 Eee PC w/ SSH Server

My questions is I recently installed GUFW on both computers. I then used each computer to scan their own ports. 

Both computers show the following ports as open.

22 - SSH
631 - IPP

Both alright except for the fact that I have GUFW set to Deny All and only specifically allowed Port 22. So why is 631 still showing up? Is this something to be concerned about?

Secondly each scan occasionally shows random ports open in the above 30000 range. What on earth are they? It's a different port each time. Any ideas?

E.G. I'll scan now. 

First Result : 22, 631 Open. 
Second Result : 22, 631, 35289 & 46941 Open
Third Result :22, 631, 35491 Open

All these scans were done less than 30 seconds apart.

Cheers for any help.

---

### Post by Kinstonian on 2008-11-01
Make sure your firewall is enabled, and also post the rules so we can see why it doesn't seem to be working properly.

Sometimes if a port scan is too fast the results aren't as accurate.  Try slowing it down and see if those high ports are still open.

---

### Post by philliptweedie on 2008-11-01
Firewalls definitely enabled.

Only port 22 is allowed for incoming and the random ports open is still happening even with a long gap between scans.

---

### Post by caljohnsmith on 2008-11-01
How about posting:
```
sudo netstat -tlpu  
sudo iptables -L
```
That might help shed some light on your port issue.

---

### Post by philliptweedie on 2008-11-01
These are the results from my Eee.

sudo netstat -tlpu

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:ssh                   *:*                     LISTEN      4677/sshd       
tcp        0      0 localhost:ipp           *:*                     LISTEN      4721/cupsd      
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      4677/sshd       
udp        0      0 *:bootpc                *:*                                 6202/dhclient   
udp        0      0 *:mdns                  *:*                                 4653/avahi-daemon: 
udp        0      0 *:55914                 *:*                                 4653/avahi-daemon: 

sudo iptables -L

Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK FORWARD]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK INPUT]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
DROP       all  --  anywhere             anywhere            ctstate INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK NOT-TO-ME]: ' 
DROP       all  --  anywhere             anywhere            

Chain ufw-user-forward (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT]: ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere

---

### Post by iwc5893 on 2008-11-01
Isn't port 631 used by CUPS/LPR for the printer, and isn't only accessible from the local host IP?

---

### Post by brian_p on 2008-11-01
> **philliptweedie said:**
> I'll quickly describe my home network.

1 Netgear Router - No ports being forwarded

So - no requests getting though to either machine! Which rather makes a firewall redundant.

> So why is 631 still showing up? Is this something to be concerned about?

ipp is the printing service. With the default setup the machine will only answer requests made by itself. Nothing to worry about.

> E.G. I'll scan now.

The actual command and output would be more useful.

---

### Post by philliptweedie on 2008-11-01
> **brian_p said:**
> So - no requests getting though to either machine! Which rather makes a firewall redundant.

The firewall was for the netbook as it goes out and about a lot. The only reason I mentioned the desktop was because I had used that to see if the random port issue happened on more than one computer, which it does.

The command was the port scanner which is part of the network tools program under administration. The first two results are always there and are expected.

Port	State	Service
22	open	ssh
631	open	ipp

Usually one or two other results will appear, in one case :

Port	State	Service
22	open	ssh
631	open	ipp
50964	open	unknown
57892	open	unknown

These other higher ports will always be different numbers in each scan. It just seemed very strange.

---

### Post by gaiterin on 2008-11-01
Hi. I tested it with vnc between 2 computers and it worked.
Can you try the vnc connect too?
Remember: The rules can be overwrite by the order in iptables :O Maybe you must clear the iptables too.
Best regards.

---

### Post by aquarianwolf on 2008-11-01
I have a quick question, I am new to Ubuntu having only downloaded it in September.

What I want to know is how to make sure all the ports are closed.

How do I this?

Aquarianwolf

---

### Post by lovinglinux on 2008-11-01
> **philliptweedie said:**
> These are the results from my Eee.

sudo netstat -tlpu

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:ssh                   *:*                     LISTEN      4677/sshd       
tcp        0      0 localhost:ipp           *:*                     LISTEN      4721/cupsd      
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      4677/sshd       
udp        0      0 *:bootpc                *:*                                 6202/dhclient   
udp        0      0 *:mdns                  *:*                                 4653/avahi-daemon: 
udp        0      0 *:55914                 *:*                                 4653/avahi-daemon: 


As far as I understand, these results doesn't mean that the traffic is passing through. They just show that there are services listen to those ports. If your firewall is configured to allow inbound traffic only on port 22, it will block traffic directed to the other ports. So there is nothing to worry about them if your firewall is properly configured. 

To make sure your firewall is working, forward those ports temporarily from your router to your machine and scan them using [[COLOR="DarkRed"]**PC FLank**[/COLOR]]("http://www.pcflank.com/scanner1.htm"). If your firewall is working, you will get "Stealth" as scan result on every port tested and connection attempts to those ports will be logged by ufw.

If you are still worried after testing your firewall you could disable avahi-daemon in Services if you don't use it. I'm not sure if it has something to do with ssh, but I guess it has something to do with Windows network.

---

### Post by brian_p on 2008-11-01
> **philliptweedie said:**
> The firewall was for the netbook as it goes out and about a lot.

It can do that safely without a firewall but I digress and you have a more pressing query.

> Usually one or two other results will appear, in one case :

Port	State	Service
22	open	ssh
631	open	ipp
50964	open	unknown
57892	open	unknown

These other higher ports will always be different numbers in each scan. It just seemed very strange.

You have the results from netstat -tulp, which are as expected. Try

```
netstat -tulpan
```

It displays ESTABLISHED connections. It could be that what you are observing are browser connections, which will tend to open different ports when they change.

---

### Post by brian_p on 2008-11-01
> **lovinglinux said:**
> 

If you are still worried after testing your firewall you could disable avahi-daemon in Services if you don't use it. I'm not sure if it has something to do with ssh, but I guess it has something to do with Windows network.

Avahi is unconnected with ssh and not particularily orientated towards Windows networks. It is for service discovery on a local network.

[http://avahi.org/](http://avahi.org/)

---

### Post by brian_p on 2008-11-01
> **aquarianwolf said:**
> 

What I want to know is how to make sure all the ports are closed.

How do I this?

Don't install and run any services.

---

### Post by aquarianwolf on 2008-11-01
> **brian_p said:**
> Don't install and run any services.

What about Pidgin as I installed this to talk to my friends?

I do have firestarter installed so does this offer me some protection?

---

### Post by gaiterin on 2008-11-02
> **aquarianwolf said:**
> I have a quick question, I am new to Ubuntu having only downloaded it in September.

What I want to know is how to make sure all the ports are closed.

How do I this?

Aquarianwolf


In terminal you can run this commands:
```
sudo ufw enable
sudo ufw default deny
```

But I think you have got a router with all ports closed ;)

---

### Post by philliptweedie on 2008-11-02
This is the result of netstat -tulpan with the results of a port scan at the same time.

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      4677/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      4721/cupsd      
tcp       38      0 192.168.0.4:39490       75.101.145.128:443      CLOSE_WAIT  11158/dropboxd  
tcp        0      0 192.168.0.4:51387       208.43.202.5:80         ESTABLISHED 11158/dropboxd  
**tcp        0      0 127.0.0.1:51586         127.0.0.1:51586         TIME_WAIT   -        **       
tcp       38      0 192.168.0.4:47928       67.228.78.117:443       CLOSE_WAIT  11158/dropboxd  
**tcp        0      0 127.0.0.1:36312         127.0.0.1:36312         TIME_WAIT   -               **
tcp       38      0 192.168.0.4:47930       67.228.78.117:443       CLOSE_WAIT  11158/dropboxd  
tcp       38      0 192.168.0.4:47929       67.228.78.117:443       CLOSE_WAIT  11158/dropboxd  
tcp        0      0 127.0.0.1:35074         127.0.0.1:631           TIME_WAIT   -               
tcp6       0      0 :::22                   :::*                    LISTEN      4677/sshd       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           11029/dhclient  
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           4653/avahi-daemon: 
udp        0      0 0.0.0.0:55914           0.0.0.0:*                           4653/avahi-daemon: 

Port	State	Service
22	open	ssh
631	open	ipp
[B]36312	open	unknown
51586	open	unknown[/B]

The port scan is being performed on 127.0.0.1, would that be causing the problem, i.e. could it be scanning it scanning itself?

I've tried scanning my internal network ip, which turns up my ssh server and the random ports. It however doesn't report the IPP.

---

### Post by brian_p on 2008-11-02
> **philliptweedie said:**
> 

**tcp        0      0 127.0.0.1:51586         127.0.0.1:51586         TIME_WAIT   -        **       
 
**tcp        0      0 127.0.0.1:36312         127.0.0.1:36312         TIME_WAIT   -               **


Port	State	Service
22	open	ssh
631	open	ipp
[B]36312	open	unknown
51586	open	unknown[/B]

The port scan is being performed on 127.0.0.1, would that be causing the problem, i.e. could it be scanning it scanning itself?

There is no problem. The machine is going about its normal business, opening and closing sockets. The TIME_WAIT state occurs when a process closes a socket but is waiting to make sure there are no more data on the network. Maybe it is dropbox. You could test this by stopping it. 

Please see the entry for TIME_WAIT in

```
man netstat
```

and test Google with 'TIME_WAIT process netstat'.

You could while away a few hours with

```
sudo netstat -tulpanc
```

> I've tried scanning my internal network ip, which turns up my ssh server and the random ports. It however doesn't report the IPP.

cupsd only listens on localhost (127.0.0.1).

---

### Post by philliptweedie on 2008-11-02
Thanks for all the help everybody.

Happy that theres nothing I need worry about!

Cheers

---

### Post by aquarianwolf on 2008-11-02
> **gaiterin said:**
> In terminal you can run this commands:
```
sudo ufw enable
sudo ufw default deny
```

But I think you have got a router with all ports closed ;)

Yeah I have a Thomson's Speedtouch ST585 v6 router.

I've not mucked about with it so I presume it's ports are set to closed unless I alter it.

---

### Post by cariboo on 2008-11-02
Just to add something to this topic. If you use the port scan tool at System-->Administration-->Network Tools-->Port Scan you will get different results every time you click the scan button. See this bug report:

[https://bugs.launchpad.net/gnome-nettool/+bug/257042](https://bugs.launchpad.net/gnome-nettool/+bug/257042)

It has been sent upstream so it will get fixed eventually. As a work around install nmap and zenwalk, both are available in the repositories.

Jim

---


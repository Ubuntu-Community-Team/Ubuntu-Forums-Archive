---
title: "webserver: can't access pages publicly"
date: 2009-09-03
forum: Server Platforms
---

### Post by Adam65 on 2009-09-03
Hi,

I am literally feeling sick in the stomach right now writing this. Sick with frustration and sick from reading post after post, tutorial after tutorial and finding no solution to, what seems on the surface to be, a very simple problem.

For an expert in Ubuntu, web servers, routers and the like this small problem may seem even to inconsequential to acknowledge. However, to me, it has recently become the greatest bane of my existence, the reason I can't sleep at night and why i now feel  nauseated when I even think about expending anymore thought or energy on what seems to be such a long and painful path toward the solution.

SO I am coming to this wise forum as a means to save my marriage, definitely my mind and probably what few years I have left to live.

Can someone please help me!

I have set up Ubuntu Server, apache, php, mysql
Everything went well. Everything seems to work: i.e.: I have imported databases into mysql, managed them through phpmyadmin, and when I type [http://localhost](http://localhost) into a browser I get the Apache confirmation page "It Works!" displayed.

However, when I try to access the site from a seperate internet computer I get nothing appearing when I type in my static IP. (I should get the same apache confirmation page).

Yes, I have port forwarded my router and configured it correctly according to the cisco guru's. (However, when I type my static IP into a browser on this server I get my router admin page).

My diagnosis has always been that somewhere I have entered a path in error or have some other aspect of my configuration slightly askew. 

so I will list all of the relevent info from Ubuntu:

host file:
121.223.214.219 [www.attackinfo.com.au]("http://www.attackinfo.com.au")
127.0.0.1       localhost

127.0.1.1       server
10.0.0.6        server
127.0.0.1       attackinfo
10.0.0.6        attackinfo.com.au [www.attackinfo.com.au]("http://www.attackinfo.com.au")

interface file:
#The loopback network interface
auto lo
iface lo inet loopback
#The primary network interface
auto eth0
iface eth0 inet static
address 10.0.0.6
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.111

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:06:5b:cf:45:67  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fecf:4567/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:7 txqueuelen:10 
          RX bytes:27011973 (27.0 MB)  TX bytes:997090 (997.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:349510 (349.5 KB)  TX bytes:349510 (349.5 KB)

netstat -tap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:mysql                 *:*                     LISTEN      9044/mysqld     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN      23378/smbd      
tcp        0      0 *:webmin                *:*                     LISTEN      3669/perl       
tcp        0      0 *:www                   *:*                     LISTEN      3566/apache2    
tcp        0      0 server:domain           *:*                     LISTEN      8562/named      
tcp        0      0 localhost:domain        *:*                     LISTEN      8562/named      
tcp        0      0 *:ssh                   *:*                     LISTEN      2653/sshd       
tcp        0      0 localhost:ipp           *:*                     LISTEN      3381/cupsd      
tcp        0      0 *:smtp                  *:*                     LISTEN      10538/master    
tcp        0      0 localhost:953           *:*                     LISTEN      8562/named      
tcp        0      0 *:microsoft-ds          *:*                     LISTEN      23378/smbd      
tcp6       0      0 [::]:domain             [::]:*                  LISTEN      8562/named      
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      2653/sshd       
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      3381/cupsd      
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN      10538/master    
tcp6       0      0 localhost:953           [::]:*                  LISTEN      8562/named

I really hope this is enough information for someone out there in this wise forum to help me solve this problem.

If not please ask for anything else and I will be happy to provide  it.


Thankyou

---

### Post by wojox on 2009-09-03
Ok, so when you enter:

```
121.223.214.219
```

into your browser you get the router login page?

What port is Apache2 open on?

---

### Post by cdenley on 2009-09-03
Unless you configured iptables (firewall) on your server, it must be a problem with your router's configuration.
```

sudo iptables -L -n

```
I have heard of routers giving the admin page for the WAN IP for requests coming from the LAN before. You probably will not be able to access your server via the routers WAN IP from inside your LAN, but it may still work from the internet. However, this does not seem to be the case, because I cannot connect to the IP you gave.

Either your router is not forwarding the connection, iptables is filtering inbound packets for unestablished connections, or your ISP is filtering it because they don't want you running servers.

---

### Post by fahadsadah on 2009-09-03
wojox: He indicated that it is running on port 80.

cdenley: If it was filtering at the ISP level, it would not be reaching the router.
iptables can be configured to forward incoming connections to a router, but it's not easy to do accidentally

---

### Post by cdenley on 2009-09-03
> **fahadsadah said:**
> 
cdenley: If it was filtering at the ISP level, it would not be reaching the router.
iptables can be configured to forward incoming connections to a router, but it's not easy to do accidentally
He said he was seeing the router admin page from the server. This would not go through his ISP, as the router would route the server's traffic back to itself, or in his case, accept the connection and return the admin page. This is unrelated to his apparent routing/filtering issue, since I cannot access his web server. Either that, or he no longer has his server running and there was no problem.

Some routers return the admin page for any LAN connection on TCP port 80, regardless if the destination IP was its WAN or LAN IP. This does not mean your admin page can be accessed over the internet, and it does not mean port forwarding won't work for internet users.

---

### Post by Adam65 on 2009-09-03
I thank you all for such knowledgeable responses.

I know that the ISP isnt the issue as I have had the webserver fully operational on a windows system. (although this was with a previous router/modem)

Yes, I guess the apache2 is configured for port 80.

I am hoping that it isnt a port forwarding issue (although it could be) as I have gone through cisco forums to get the cisco837 port forwarding correctly... i.e. I have followed all of the directions suggested for port forwarding.

the third suggestion: IP tables... I havent dealt with before so I am looking into how to do it. I have entered in the suggested command (sudo iptables -L -n) and here are the results.
(could someone let me know if I have seriously hampered my security by posting this:
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  61.9.194.49          0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  61.9.194.49          0.0.0.0/0           
ACCEPT     tcp  --  61.9.134.49          0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  61.9.134.49          0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
DROP       all  --  0.0.0.0/0            255.255.255.255     
DROP       all  --  0.0.0.0/0            10.0.0.255          
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
LSI        all  -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
INBOUND    all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  10.0.0.6             61.9.194.49         tcp dpt:53 
ACCEPT     udp  --  10.0.0.6             61.9.194.49         udp dpt:53 
ACCEPT     tcp  --  10.0.0.6             61.9.134.49         tcp dpt:53 
ACCEPT     udp  --  10.0.0.6             61.9.134.49         udp dpt:53 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     all  --  10.0.0.12            0.0.0.0/0           
ACCEPT     tcp  --  10.0.0.0             0.0.0.0/0           tcp dpts:137:139 
ACCEPT     udp  --  10.0.0.0             0.0.0.0/0           udp dpts:137:139 
ACCEPT     tcp  --  10.0.0.0             0.0.0.0/0           tcp dpt:445 
ACCEPT     udp  --  10.0.0.0             0.0.0.0/0           udp dpt:445 
LSI        all  --  0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (3 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
LSO        all  --  0.0.0.0/0            91.103.138.62       
LSO        tcp  --  91.103.138.62        0.0.0.0/0           tcp dpt:80 
LSO        udp  --  91.103.138.62        0.0.0.0/0           udp dpt:80 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

I hope this can be of further assistance in helping me find the solution.
Thank you all again SOOOO much for the assistance.

And I guess if you guys can't see any errors in this final post then I'm back to trying other configurations for my router. (although the cisco experts seem to think that I should be right to port forard through the router to my webserver with my current config.)

Also please let me know if I need to post my router config here.


Thankyou again.

---

### Post by Adam65 on 2009-09-03
I just wanted to add a couple more things:

Firstly to cdenley: the server has been on pretty much full time now for a few weeks while I try to get this problem solved. Thankyou for your help.

Secondly to wojox, thank you as well; I have added only one line to my apache2 conf file: NameVirtualHost 121.223.214.219:80 and this seems to be the only mention of a port for apache that I can locate in that file.  (mind you virtual hosts doesn't seem to be operating either or you should be expecting my almost completed webpage to appear when 121.223.214.219 or [http://www.attackinfo.com.au](http://www.attackinfo.com.au) is accessed (instead of [http://www.attackinfo.com.au/one/](http://www.attackinfo.com.au/one/) where I access it locally on ther webserver here.)


Thanks again everyone.

At this stage I am at a standstill and am awaiting any further advice.

---

### Post by cariboo on 2009-09-03
I would check [canyouseeme]("http://www.canyouseeme.org/") just to make sure it isn't a port forwarding issue,

---

### Post by Vegan on 2009-09-03
I would also suggest checking ports on any network gear in use. Ubuntu does not use uPnP like Windows does that I have noticed.

---

### Post by Adam65 on 2009-09-06
canyouseeme says it can't and assumes port forwarding error

ubuntu forum says 1. iptables; 2. ISP; 3. router not Port forwarding

it's not one or two....

oh well i guess the router config must be the cause I will head back to the cisco forums and let you know how I go. 

Thank you all and especially cdenley

---


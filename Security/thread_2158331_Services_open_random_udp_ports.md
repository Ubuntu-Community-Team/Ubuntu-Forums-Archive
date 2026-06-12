---
title: "Services open random udp ports"
date: 2013-06-28
forum: Security
---

### Post by stripecat on 2013-06-28
I have noticed a behaviour in Ubuntu Server x86_64 12.04, 12.10 and 13.04. Services such as Bind, Dhclient and Squid opens random udp-ports. I noticed this when I installed "Tiger". At first I thought it was some kind of 'false positive', but when I verified by running 'netstat -tupln', it showed that the service was indeed listening to an ephemeral UDP port. The ports stay up for a number of hours and then either close OR change to other ports. I replaced Bind with PowerDNS, but the behaviour is the same. I'm not sure I can see a pattern here.

I have failed to find *ANY* information in the documentation of Ubuntu.

Example of warnings (OLD means that it has ceased to listen to the port):

NEW: --WARN-- [lin003w] The process `pdns_server' is listening on socket 49074 (UDP on every interface) is run by pdns. 
OLD: --WARN-- [lin003w] The process `named' is listening on socket 49930 (UDP on every interface) is run by bind.  
NEW: --WARN-- [lin003w] The process `named' is listening on socket 49930 (UDP on every interface) is run by bind.

Is this a proper behaviour? Could it be a security compromise. Please advice.

---

### Post by Doug S on 2013-06-28
I have never seen the issue you mention. Here is the output from my main gateway server/router:```
doug@doug-64:~$ sudo netstat -tupln
[sudo] password for doug:
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1210/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1573/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1516/apache2
tcp        0      0 XXX.XXX.XX.X:53         0.0.0.0:*               LISTEN      5674/named
tcp        0      0 192.168.111.1:53        0.0.0.0:*               LISTEN      5674/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      5674/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1046/sshd
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      5674/named
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1424/master
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1573/smbd
udp        0      0 XXX.XXX.XX.X:53         0.0.0.0:*                           5674/named
udp        0      0 192.168.111.1:53        0.0.0.0:*                           5674/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           5674/named
udp        0      0 0.0.0.0:67              0.0.0.0:*                           1221/dhcpd
udp        0      0 0.0.0.0:68              0.0.0.0:*                           852/dhclient3
udp        0      0 192.168.111.255:137     0.0.0.0:*                           1082/nmbd
udp        0      0 192.168.111.1:137       0.0.0.0:*                           1082/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1082/nmbd
udp        0      0 192.168.111.255:138     0.0.0.0:*                           1082/nmbd
udp        0      0 192.168.111.1:138       0.0.0.0:*                           1082/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1082/nmbd
```

---

### Post by unspawn on 2013-07-02
> **stripecat said:**
> I have noticed a behaviour in Ubuntu Server x86_64 12.04, 12.10 and 13.04. Services such as Bind, Dhclient and Squid opens random udp-ports. (..) when I verified by running 'netstat -tupln', it showed that the service was indeed listening to an ephemeral UDP port. The ports stay up for a number of hours and then either close OR change to other ports. (..) Is this a proper behaviour?Opening an ephemeral port is regular behavior for when a server (say ISC BIND) needs to make a request. You should be able to determine that connection has a remote UDP/53 or TCP/53 as destination using your favorite tool 'lsof':```
lsof -Pwlni -a -p $(pgrep -d, named)
``` or else analyze traffic on the port with tcpdump or Wireshark.> **stripecat said:**
> I have failed to find *ANY* information in the documentation of Ubuntu.Thanks in advance for correcting? ;-p

---

### Post by Doug S on 2013-07-02
> **unspawn said:**
> Opening an ephemeral port is regular behavior for when a server (say ISC BIND) needs to make a request.Yes, but I do not think it would show using the command the OP listed, 'netstat -tupln'. I ran 'watch' that command for quite along time and never saw anything.
While it is hard to catch, as typically the sessions are very very short, it does show for these commands (one is what unspawn gave)(done under 'watch'):```
Every 2.0s: netstat --udp -n                           Tue Jul  2 15:52:33 2013

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
udp        0      0 [COLOR=#ff0000]XXX.XXX.XX.X:52839      96.17.144.40:53[/COLOR]         ESTABLISHED
``````
Every 2.0s: sudo lsof -Pwlni -a -p 5674                Tue Jul  2 16:08:11 2013

COMMAND  PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
named   5674      105   20u  IPv4  29541      0t0  TCP 127.0.0.1:53 (LISTEN)
named   5674      105   21u  IPv4  29543      0t0  TCP 192.168.111.1:53 (LISTEN)
named   5674      105   22u  IPv4  29545      0t0  TCP XXX.XXX.XX.X:53 (LISTEN)
named   5674      105   23u  IPv4  29548      0t0  TCP 127.0.0.1:953 (LISTEN)
named   5674      105  512u  IPv4  29540      0t0  UDP 127.0.0.1:53
named   5674      105  513u  IPv4  29542      0t0  UDP 192.168.111.1:53
named   5674      105  514u  IPv4  29544      0t0  UDP XXX.XXX.XX.X:53
named   5674      105  515u  IPv4 306205      0t0  UDP [COLOR=#ff0000]XXX.XXX.XX.X:60599->64.237.104.68:53[/COLOR]
named   5674      105  517u  IPv4 305801      0t0  UDP [COLOR=#ff0000]XXX.XXX.XX.X:34477->64.237.104.68:53[/COLOR]
```I had to wait quite awhile to catch the above examples, but my site is not that busy. Since the OP has said "The ports stay up for a number of hours and then either close OR change to other ports" I had assumed these quick forwarded lookups were not the issue.

---

### Post by stripecat on 2013-07-04
> You should be able to determine that connection has a remote UDP/53 or TCP/53 as destination using your favorite tool 'lsof':

Interestingly this is not the case. I have switched from Bind to PowerDNS, and running lsof gives me this:

```
lsof -Pwlni -a -p $(pgrep -d, pdns)
```

COMMAND    PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
pdns_serv 6809      111    5u  IPv4  27881      0t0  UDP *:53 
pdns_serv 6809      111    6u  IPv4  27882      0t0  TCP *:53 (LISTEN)
pdns_serv 6809      111    7u  IPv4  27887      0t0  TCP 127.0.0.1:8082 (LISTEN)
pdns_serv 6809      111    8u  IPv4  27888      0t0  UDP *:49074 
pdns_serv 6809      111    9u  IPv6  27889      0t0  UDP *:53307 

```
sudo netstat -tupn|grep 49074
```

udp        0      0 0.0.0.0:49074           0.0.0.0:*                           6809/pdns_server-in

As you can see, it's not a listening port and there's nothing "ESTABLISHED".

---

### Post by unspawn on 2013-07-05
> **stripecat said:**
> Interestingly this is not the case. (..) As you can see, it's not a listening port and there's nothing "ESTABLISHED".Force it to make a request or analyze any traffic on the port with tcpdump or Wireshark?

---

### Post by KenSharp on 2013-10-25
I've started to see this with Squid 3 on my server. I have no idea why.

```
# netstat -pWlutn | grep squid3
tcp6       0      0 :::3128                 :::*                    LISTEN      1360/squid3     
udp        0      0 0.0.0.0:50020           0.0.0.0:*                           1360/squid3     
udp6       0      0 :::3130                 :::*                                1360/squid3     
udp6       0      0 :::45795                :::*                                1360/squid3
```

Only tcp/3128 and udp/3130 should be open - they're the only ports mentioned in the config.

This is a concern as it is listening on all interfaces. I'm sure this never used to happen but I have no idea when this could have started.

---

### Post by Ilya_Kisleyko on 2014-09-28
Squid opens random UDP port due udp_incoming_address parameter in config file:

```
#  TAG: udp_incoming_address
#       udp_incoming_address    is used for UDP packets received from other
#                               caches.
#       The default behavior is to not bind to any specific address.
#
#       Instead it will use the same socket as udp_incoming_address.
#       Only change this if you want to have UDP queries sent using another
#       address than where this Squid listens for UDP queries from other
#       caches.
#
#       NOTE: udp_outgoing_address is used by the ICP, HTCP, and DNS
#       modules. Altering it will affect all of them in the same manner.
#
#       see also; udp_incoming_address
#
#       NOTE, udp_incoming_address and udp_outgoing_address can not
#       have the same value since they both use the same port.
#Default:
 # Accept packets from all machine interfaces.
``` 

try to set
```
udp_incoming_address 192.168.0.1
```
where 192.168.0.1 - address of Squid computer
to isolate that feature within local network

Note : DNS-answers will be received from DNS-server on that address
So if you use DNS-server outside your local network, changing udp_incoming_address from default will break your Squid-server

[source]("http://linuxplayer.org/2012/02/why-squid-listen-on-high-udp-port-number")

---


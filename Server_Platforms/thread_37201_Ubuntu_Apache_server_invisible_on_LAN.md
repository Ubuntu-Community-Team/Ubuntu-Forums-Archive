---
title: "Ubuntu Apache server invisible on LAN"
date: 2005-05-26
forum: Server Platforms
---

### Post by agiledata on 2005-05-26
Moving from Windows to Ubuntu, I want to serve web pages with Apache. I get the default page when browsing from the server, with no problem, but can't browse to the server from another PC on the same LAN, or access it from the world. 

Apache's ports.conf has a line 
```
Listen 80
``` 
/etc/default/portmap has the line commented out as required:
```
# By default, listen only on the loopback interface
# Next line must be commented out to allow ubuntu to act as web server--I think
# ARGS="-i 127.0.0.1"
```
I'm inside the router firewall, so configuring that made no difference to LAN access! Is there some automatic firewall in Ubuntu that isn't mentioned anywhere. I've searched the newsgroups for hours, but to no avail. It's presumably very simple???

Rob

---

### Post by LordHunter317 on 2005-05-26
Portmap doesn't do anything with Apache, so I don't know why you changed that.

How are you trying to connect?  Is Apache running?

Does it work if you connect by IP address?

---

### Post by agiledata on 2005-05-26
[QUOTE=LordHunter317]Portmap doesn't do anything with Apache, so I don't know why you changed that.[/QUOTE]
I was getting a bit desperate, looking for anything that might open up ports.

[QUOTE=LordHunter317]How are you trying to connect?  Is Apache running?

Does it work if you connect by IP address?[/QUOTE]
Apache is running, because it will serve pages if I browse with Firefox on the server.
I've tried connecting by domain name, but even local IP address doesn't work (e.g. [http://192.168.0.32](http://192.168.0.32) or [http://192.168.0.32:80](http://192.168.0.32:80) in Firefox from elsewhere on the LAN.)

---

### Post by jdonnell on 2005-05-26
How is your lan setup? Is there only one router? Are both computers connected to the same router? Is it at home or an office? Basically, we need more info to help you out.

---

### Post by Xed on 2005-05-26
To check for firewall settings on your Apache server:
```

$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
                                                                                                                             
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
                                                                                                                             
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```


Can you telnet to the Apache server? try:
```

$ telnet apache 80
GETHTTP

```

---

### Post by s0c0 on 2005-05-26
1.  Can you ping the web server from other boxes on your LAN?

2.  What error are you getting when you try viewing the webpages being served?

3.  Did you make sure proper viewing permissions are set for the /var/www?  Do an "ls- l /var" to find out.

4.  Also make sure your /etc/hosts has been configured.  I know this throws errors on freebsd systems attempting to serve pages if this file has not been setup properly.  

I have never really had problems with Apache on Ubuntu though.  I assume you are using Apache 2.0 for this, try using Apache 1.3 I have found it to be more stable and easier to use than Apache 2.0.  Especially since this is just serving pages for a local LAN then there should be no need for the bells and whistles that Apache2.0 provides.  Good luck.

---

### Post by agiledata on 2005-05-26
[QUOTE=jdonnell]How is your lan setup? Is there only one router? Are both computers connected to the same router? Is it at home or an office? Basically, we need more info to help you out.[/QUOTE]
Ok. This is a home network. I have one Draytek wireless router, connected via ADSL to an ISP. I have three PCs wired into the 4-port hub which is part of the router (Windows XP, Windows NT4, and Ubuntu) and a wireless-connected XP laptop. All PCs can happily connect to the Internet, and the Windows PC can ping each other.

However, the Ubuntu PC can neither send/receive local PC pings. Ubuntu can ping the router, and google.co.uk. It's as if there was a firewall I don't know about. On a Windows PC, I'd disable Sygate or ZoneAlarm, and I'd be able to ping.

Is there any other background that would be useful?

Rob

---

### Post by agiledata on 2005-05-26
[QUOTE=Xed]To check for firewall settings on your Apache server:
```

$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
                                                                                                                             
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
                                                                                                                             
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```
[/QUOTE]
I got precisely that output as above.
> 
Can you telnet to the Apache server? try:
```

$ telnet apache 80
GETHTTP

```
No. I get
```
telnet: could not resolve apache/80: Name or service not known
```
Also with ```
$ telnet apache2 80
```
But System Monitor shows 5 apache services running, started with ```
/usr/sbin/apache2/ -k start -DSSL
``` and apache is still serving pages on the server. Do I have to publish/register apache as running somwhere?

Rob

---

### Post by LordHunter317 on 2005-05-26
No, you don't need to publish it anywhere.

Post your /etc/apache2/ports.conf.  I doubt it's this; I think you have a network configuration issue somewhere.

Post the output of /sbin/ifconfig while you're at it.

---

### Post by jdonnell on 2005-05-26
What is the ip address of your ubuntu box and what is the ip address of the win box your using to test?

Try to run a traceroute from windows to the ubuntu box.

---

### Post by agiledata on 2005-05-26
> Post your /etc/apache2/ports.conf.
```

Listen 80
Listen 8001

```

> Post the output of /sbin/ifconfig while you're at it.
```
eth0      Link encap:Ethernet  HWaddr 00:09:6B:94:E5:A4
          inet addr:192.168.0.32  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::209:6bff:fe94:e5a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11651 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6986648 (6.6 MiB)  TX bytes:1152069 (1.0 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2267424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2267424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:263217057 (251.0 MiB)  TX bytes:263217057 (251.0 MiB)
```

> What is the ip address of your ubuntu box and what is the ip address of the win box your using to test?
```
Ubuntu PC: 192.168.0.32
Windows NT4:     192.168.0.21
Windows XP:      192.168.0.73
Draytek router:  192.168.0.2
```
> Try to run a traceroute from windows to the ubuntu box.
Message:  Cannot reach 192.168.0.32, then Windows offers to dial a number to find it.
> 1. Can you ping the web server from other boxes on your LAN?
No. Can't ping in or out.
> 2. What error are you getting when you try viewing the webpages being served?
Message: The operation timed out when attempting to contact 192.168.0.3
> 3. Did you make sure proper viewing permissions are set for the /var/www? Do an "ls- l /var" to find out.
```
drwxr-xr-x   4 root root   1024 2005-05-23 20:53 www
```
What should the permissions be?

> 4. Also make sure your /etc/hosts has been configured. I know this throws errors on freebsd systems attempting to serve pages if this file has not been setup properly.
```
127.0.0.1 localhost.localdomain localhost brigid
192.168.0.32 brigid
192.168.0.73 melrose

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet ip6-localnet
ff00::0 ip6-mcastprefix ip6-mcastprefix
ff02::1 ip6-allnodes ip6-allnodes
ff02::2 ip6-allrouters ip6-allrouters
ff02::3 ip6-allhosts ip6-allhosts

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

192.168.0.69 aidan
```

Thanks for all your help so far. I'm feeling a little bit more hopeful with the support, and I really do want to make ubuntu work.

Rob

---

### Post by jdonnell on 2005-05-26
[QUOTE=agiledata]
> Try to run a traceroute from windows to the ubuntu box.
Message:  Cannot reach 192.168.0.32, then Windows offers to dial a number to find it.
[/QUOTE]

This makes me think the problem is your router or your windows box. I believe you should see it hit the router and then fail trying to reach the ubuntu box if the problem were the ubuntu box. Try to run a traceroute to one of your other win boxes and you should see it hit the router then then win box. 

Are you using plain dhcp on the router?

---

### Post by LordHunter317 on 2005-05-26
[QUOTE=jdonnell]This makes me think the problem is your router or your windows box. I believe you should see it hit the router and then fail trying to reach the ubuntu box if the problem were the ubuntu box.[/quote]Nope.

It's on the local subnet.  Traceroute should't show anything.  Not having at least one router in between defeats the way traceroute works.

> Try to run a traceroute to one of your other win boxes and you should see it hit the router then then win box. If you're ever seeing traffic going through a router on the **local** subnet then something is seriously wrong.

To the OP:
Post the output of:```
sudo netstat -pln --inet
sudo netstat -pln --inet6
```
And the output of 'ipconfig /all' on your Windows boxes.

---

### Post by agiledata on 2005-05-26
[QUOTE=jdonnell]This makes me think the problem is your router or your windows box. I believe you should see it hit the router and then fail trying to reach the ubuntu box if the problem were the ubuntu box. Try to run a traceroute to one of your other win boxes and you should see it hit the router then then win box. [/QUOTE]
tracert from windows to windows or router gets there in one step. It seems to be configured as a basic 4-port hub, with the router on a fifth port, i.e. direction connection as far as tracert is concerned.
> Are you using plain dhcp on the router?
The router is currently set with DHCP disabled: I've set everything as a fixed IP address, so I can track them easily.

Two other settings on the same router page, that might be useful:
IP Routing Usage is disabled
RIP Protocol Control is disabled

---

### Post by agiledata on 2005-05-26
[QUOTE=LordHunter317]Post the output of:```
sudo netstat -pln --inet
sudo netstat -pln --inet6
```[/QUOTE]
```
 sudo netstat -pln --inet
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     7531/vino-server
tcp        0      0 0.0.0.0:6000            0.0.0.0:*               LISTEN     6303/X
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     7882/cupsd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     7068/master
udp        0      0 0.0.0.0:177             0.0.0.0:*                          6243/gdm
udp        0      0 192.168.0.32:123        0.0.0.0:*                          7250/ntpd
udp        0      0 127.0.0.1:123           0.0.0.0:*                          7250/ntpd
udp        0      0 0.0.0.0:123             0.0.0.0:*                          7250/ntpd

 sudo netstat -pln --inet6
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp6       0      0 :::8001                 :::*                    LISTEN     7301/apache2
tcp6       0      0 :::80                   :::*                    LISTEN     7301/apache2
tcp6       0      0 :::6000                 :::*                    LISTEN     6303/X
tcp6       0      0 :::22                   :::*                    LISTEN     7236/sshd
tcp6       0      0 ::1:25                  :::*                    LISTEN     7068/master
udp6       0      0 :::123                  :::*                               7250/ntpd


```
> And the output of 'ipconfig /all' on your Windows boxes.
I'll have to post that from Windows, since I haven't yet got samba working, and the floppy disk I copied them to, says it's a different format!

---

### Post by agiledata on 2005-05-26
[QUOTE=LordHunter317]
And the output of 'ipconfig /all' on your Windows boxes.[/QUOTE]
```
Windows NT IP Configuration
	Host Name . . . . . . . . . : aps
	DNS Servers . . . . . . . . : 212.159.13.49
	                              212.159.13.49
	Node Type . . . . . . . . . : Broadcast
	NetBIOS Scope ID. . . . . . : 
	IP Routing Enabled. . . . . : No
	WINS Proxy Enabled. . . . . : No
	NetBIOS Resolution Uses DNS : No

Ethernet adapter Elnk31:
	Description . . . . . . . . : ELNK3 Ethernet Adapter.
	Physical Address. . . . . . : 00-50-04-30-C2-6C
	DHCP Enabled. . . . . . . . : No
	IP Address. . . . . . . . . : 192.168.0.21
	Subnet Mask . . . . . . . . : 255.255.255.0
	Default Gateway . . . . . . : 192.168.0.2

PPP adapter NdisWan5:
	Description . . . . . . . . : NdisWan Adapter
	Physical Address. . . . . . : 00-00-00-00-00-00
	DHCP Enabled. . . . . . . . : No
	IP Address. . . . . . . . . : 0.0.0.0
	Subnet Mask . . . . . . . . : 0.0.0.0
	Default Gateway . . . . . . : 

PPP adapter NdisWan4:
	Description . . . . . . . . : NdisWan Adapter
	Physical Address. . . . . . : 00-00-00-00-00-00
	DHCP Enabled. . . . . . . . : No
	IP Address. . . . . . . . . : 0.0.0.0
	Subnet Mask . . . . . . . . : 0.0.0.0
	Default Gateway . . . . . . : 

=====================XP:
Windows IP Configuration
        Host Name . . . . . . . . . . . . : melrose
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : Yes

Ethernet adapter Local Area Connection 2:
        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Bluetooth LAN Access Server Driver
        Physical Address. . . . . . . . . : 00-10-60-A3-B0-6D

Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-50-2C-04-A9-1D
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.0.73
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.2
        DNS Servers . . . . . . . . . . . : 212.159.13.49
                                            212.159.13.50
```

---

### Post by LordHunter317 on 2005-05-26
Hrm, I'm slightly perplexed here.

Your server is on 192.168.0.32, so if you connect there by IP, it ought to work fine.

This suggest to me an issue with a firewall on the Windows machines.  The network configuration otherwise looks ok.

Make sure if you changed any network related settings on the Linux box, you restarted Apache afterwards.

Try by IP first.  You said they couldn't ping before?  You need to get that working first.  Then try web.

---

### Post by agiledata on 2005-05-27
[QUOTE=LordHunter317]This suggest to me an issue with a firewall on the Windows machines.[/QUOTE]
I turned off the Windows firewalls, to make sure they could ping each other.

---

### Post by jdonnell on 2005-05-27
[QUOTE=LordHunter317]Nope.

It's on the local subnet.  Traceroute should't show anything.  Not having at least one router in between defeats the way traceroute works.

If you're ever seeing traffic going through a router on the **local** subnet then something is seriously wrong.
[/QUOTE]


Oops, you are correct. I should stick to programming :)

---

### Post by LordHunter317 on 2005-05-27
Well, I slightly misspoke.  You should see one hop at most: the server itself.  I don't see any here because most of boxes don't respond to pings at all, due to slightly lazy firewall polices.

---

### Post by jdonnell on 2005-05-27
My network skills are lacking a bit. Why do you see hops thru internet routers but not local lan routers?

---

### Post by agiledata on 2005-05-27
Problem solved!

I should stick to programming (Python) as well. I find networks an obscure art that nobody notices until they don't work. I had assumed there was a problem with my Ubuntu installation because (a) I couldn't serve a web page to the outside, and (b) I couldn't ping within the LAN. 

I tried booting Ubuntu box from the live CD. It's very useful to be able to go back as if doing a fresh install. Same problem. So it wasn't my settings of Ubuntu.

Next I tried a crossover cable from Ubuntu to Windows XP laptop, and everything worked. Thus it must be the network. Two different problems: (a) the Draytek router software has a known fault, that you can't connect back to a server on the LAN, when going out throught the router, and (b) the router has a VLAN, splitting the 4 ports into two distinct networks. I had plugged my Ubuntu cable into the wrong socket, separating it from the Windows PCs.

Many thanks for your helpful suggestions.

Rob  ;-)

---

### Post by LordHunter317 on 2005-05-27
[QUOTE=jdonnell]My network skills are lacking a bit. Why do you see hops thru internet routers but not local lan routers?[/QUOTE]Because traffic on the local subnet doesn't go through a router.

On an IP network (like the Internet and the ones in our homes) it's assumed everyone on the same IP subnet is part of the same physical network.  As such, when I go to talk to someone on my subnet, I don't need a router.   Your computer (basically) assumes it can put the data out on the wire and it'll automatically arrive

A router is only needed when you want to talk between two networks, e.g., your home and the Internet.

In fact, if you didn't have an Internet connection, you wouldn't need a router at all, just a switch or hub to create your physical network.

---

### Post by LordHunter317 on 2005-05-27
What I forgot to mention and should have said is that the OP's problem is a perfect example of this.

He had mistakenly seperated his server on to a seoperate physical network (VLANs are a way to have multiple physical networks on the same HW switch).  As such, the assumptions that the server and clients were making about their connectivity were incorrect.

---


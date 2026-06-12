---
title: "About iptables rule"
date: 2008-02-21
forum: Server Platforms
---

### Post by satimis on 2008-02-21
Hi folks,


WAN

Ubuntu 7.04 server amd64
iptables 1.3.6
port 22 forwarded to server router addr (router_ip)
Server_router_ip = 192.168.0.51
Public_IP_1

Archlinux 86-64 2007-08-2 (workstation)
Workstation_router_ip = 192.168.0.11
Public_IP_2


I'm trying to set rules on Server to only allow the  workstation which is running
Public_IP_2 and router_ip=192.168.0.11 to ssh_connect the Server.  Please shed me some light how to
start.  TIA


B.R.
satimis

---

### Post by The Cog on 2008-02-21
Some commands something like this should do the trick:
```
iptables -P INPUT DROP
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -s 192.168.0.51 -p tcp -m tcp --dport 22 -j ACCEPT
```
You need to put ths in a script somewhere so it happens at system bootup.
I find that without the lo line, local services like printing stop working.

---

### Post by satimis on 2008-02-21
> **The Cog said:**
> Some commands something like this should do the trick:
```
iptables -P INPUT DROP
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -s 192.168.0.51 -p tcp -m tcp --dport 22 -j ACCEPT
```
You need to put ths in a script somewhere so it happens at system bootup.
I find that without the lo line, local services like printing stop working.
Thanks for your advice.

Following rules works here but port 22 has to be forwarded on server router```


# INPUT
#

# allow all incoming traffic from the management interface NIC
# as long as it is a part of an established connection
iptables -I INPUT 1 -j ACCEPT -d server_public_ip -m state --state RELATED,ESTABLISHED

# allow all VMware MUI HTTP traffic to the management interface NIC
iptables -I INPUT 2 -j ACCEPT -p TCP -d server_public_ip --destination-port 8222

# allow all VMware MUI HTTPS traffic to the management interface NIC
iptables -I INPUT 3 -j ACCEPT -p TCP -d server_public_ip --destination-port 8333

# allow all VMware Authorization Daemon traffic to the management interface NIC
iptables -I INPUT 4 -j ACCEPT -p TCP -d server_public_ip --destination-port 902

# reject all other traffic to the management interface NIC
iptables -I INPUT 5 -j REJECT -d server_public_ip --reject-with icmp-port-unreachable


#
# OUTPUT
#

# allow all outgoing traffic from the management interface NIC
# if it is a part of an established connection
iptables -I OUTPUT 1 -j ACCEPT -s server_public_ip -m state --state RELATED,ESTABLISHD

# allow all DNS queries from the management interface NIC
iptables -I OUTPUT 2 -j ACCEPT -s server_public_ip -p UDP --destination-port 53

# reject all other traffic from localhost
#iptables -I OUTPUT 3 -j REJECT -s 127.0.0.1 --reject-with icmp-port-unreachable

# reject all other traffic from the management interface NIC
iptables -I OUTPUT 3 -j REJECT -s server_public_ip --reject-with icmp-port-unreachable

```

Adding your suggestion and indexing them as 2, 3and 4 makes no difference (other index also changed according. "-j" has to be added before DROP)

"A" has to be changed as "I". Otherwise it complains


satimis

---

### Post by The Cog on 2008-02-21
I clearly didn't understand what your setup and requirements are. Can you explain again (for dummies like me) what the network arrangement is, and what it is you want to block/allow?

---

### Post by satimis on 2008-02-21
> **The Cog said:**
> I clearly didn't understand what your setup and requirements are. Can you explain again (for dummies like me) what the network arrangement is, and what it is you want to block/allow?
Oh, sorry for not clearly explaining my test before.


I'm prepared to have the server co-located where a new public IP will be provided.  It'll be infeasible to have onsite upgrade/maintenance nor conveient taking the server home for service.  Therefore I'll perform remote administration on a workstation here with another public IP which is behind a router.  I have no idea whether on co-location the server will be behind a router or just connected to DSL-modem.

However before taking the server co-located I must test it at home.  That is the whole story.  Also it is my planning test here.

Thanks


B.R.
satimis

---

### Post by The Cog on 2008-02-22
So you want the server to accept SSH calls from two different IP addresses:
* Your private address 192.168.0.11 for when the server is at home, and 
* from your home public address Public_IP_2 for when the server has been colocated.
I hope I've got that right.

One possibility is to configure SSH for X509 certificated access only, in which case you could allow SSH from anywhere. But I'll ignore that option for now.

Questions you will need to ask your CoLo company are:
* your server IP address and subnet mask
* your server's default gateway address
* The IP address of one or two domain name servers.
These will all need configuring into your server before shipping.

Are the rules you posted intended to go on the server? If so, I have a few comments to make (I'm assuning the server will only have one NIC):

In the INPUT chain, checking for the destination address is not needed - packets won't reach the INPUT chain unless they are addressed to the server anyway. So it would be good to remove the -d clause which simplifies the config and allows you to change the servers address without having to reconfigure all the iptables rules.

Nothing in the rules prevents anyone in the world connecting to port 902. I'm not familiar with that protocol so I don't know whether you want it open to the world or not.

Your last rule in the chain (reject everything not already dealt with) is unusual. It is more common to use the command:
**iptables -P INPUT DROP**
which sets a default policy to drop input packets not expressly allowed. This does the same as your rule, but without having to add a specigic drop rule. Now you can add further rules without worrying about them ending up after the drop rule. Same applies to the output chain of course.

In the OUTPUT chain, there is no point in filtering on the source address (unless you have 2 NICs) because packets will inevitably have that source address anyway.

There is no point trying to reject packets from localhost - the server will never use that address to talk to other devices - IP doesn't allow it.

I have discovered that it helps tp allow the server to talk to itself, otherwise things like print spooling may not work. You can do this by allowing packets from localhost to localhost, or allowing input packets from interface lo.

Adding the requirement to allow SSH in from your workstation (2 addresses), I would suggest a rule set a bit like this:
```

# Clear out any old rules before we start
/sbin/iptables -F
/sbin/iptables -X


## INPUT chain ##

# Set the default policy to drop
/sbin/iptables -P INPUT DROP

# Allow existing connections to continue
/sbin/iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
/sbin/iptables -A INPUT -i lo -j ACCEPT

# allow all VMware MUI HTTP connections in from anywhere
/sbin/iptables -A INPUT -p tcp --dport 8222 -j ACCEPT

# allow all VMware MUI HTTPS connections in from anywhere
/sbin/iptables -A INPUT -p tcp --dport 8333 -j ACCEPT

# allow all VMware Authorization Daemon connections in from anywhere
/sbin/iptables -A INPUT -p tcp --dport 8333 -j ACCEPT

# Allow ssh from workstation local IP
/sbin/iptables -A INPUT -s 192.168.0.11 -p tcp --dport 22 -j ACCEPT

# Allow ssh from workstation public IP
/sbin/iptables -A INPUT -s workstation-public-IP -p tcp --dport 22 -j ACCEPT






## OUTPUT chain ##

# Set the default policy to drop
/sbin/iptables -P OUTPUT DROP

# Allow existing connections to continue
/sbin/iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
/sbin/iptables -A OUTPUT -d 127.0.0.1 -j ACCEPT

# Allow DNS requests out
/sbin/iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT


```

Notice that it's normal to use -A when adding rules rather than -I. This is because reordering them or inserting a new rule later if you want is easier - you don't have to re-edit every line.

I hven't tried these rules, but I hope I'm at least pointing you in the right direction.

---

### Post by satimis on 2008-02-22
> **The Cog said:**
> So you want the server to accept SSH calls from two different IP addresses:
* Your private address 192.168.0.11 for when the server is at home, and 
* from your home public address Public_IP_2 for when the server has been colocated.
I hope I've got that right.

Yes, correct.


> 
One possibility is to configure SSH for X509 certificated access only, in which case you could allow SSH from anywhere. But I'll ignore that option for now.

Noted.


> 
Questions you will need to ask your CoLo company are:
* your server IP address and subnet mask
* your server's default gateway address
* The IP address of one or two domain name servers.
These will all need configuring into your server before shipping.

Co-lo company will provide those info after contract signed.


> 
Are the rules you posted intended to go on the server? If so, I have a few comments to make (I'm assuning the server will only have one NIC):

Yes, that are correct.


> 
In the INPUT chain, checking for the destination address is not needed - packets won't reach the INPUT chain unless they are addressed to the server anyway. So it would be good to remove the -d clause which simplifies the config and allows you to change the servers address without having to reconfigure all the iptables rules.

Noted and thanks.


> 
Nothing in the rules prevents anyone in the world connecting to port 902. I'm not familiar with that protocol so I don't know whether you want it open to the world or not.

Port 902 is for VMWare server.  I don't need it at the beginning on co-lo.  I need it at home for testing this virtual machine.


> 
Adding the requirement to allow SSH in from your workstation (2 addresses), I would suggest a rule set a bit like this:
```

# Clear out any old rules before we start
/sbin/iptables -F
/sbin/iptables -X


## INPUT chain ##

# Set the default policy to drop
/sbin/iptables -P INPUT DROP

# Allow existing connections to continue
/sbin/iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
/sbin/iptables -A INPUT -i lo -j ACCEPT

# allow all VMware MUI HTTP connections in from anywhere
/sbin/iptables -A INPUT -p tcp --dport 8222 -j ACCEPT

# allow all VMware MUI HTTPS connections in from anywhere
/sbin/iptables -A INPUT -p tcp --dport 8333 -j ACCEPT

# allow all VMware Authorization Daemon connections in from anywhere
/sbin/iptables -A INPUT -p tcp --dport 8333 -j ACCEPT

# Allow ssh from workstation local IP
/sbin/iptables -A INPUT -s 192.168.0.11 -p tcp --dport 22 -j ACCEPT

# Allow ssh from workstation public IP
/sbin/iptables -A INPUT -s workstation-public-IP -p tcp --dport 22 -j ACCEPT


## OUTPUT chain ##

# Set the default policy to drop
/sbin/iptables -P OUTPUT DROP

# Allow existing connections to continue
/sbin/iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
/sbin/iptables -A OUTPUT -d 127.0.0.1 -j ACCEPT

# Allow DNS requests out
/sbin/iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT


```

Notice that it's normal to use -A when adding rules rather than -I. This is because reordering them or inserting a new rule later if you want is easier - you don't have to re-edit every line.

I hven't tried these rules, but I hope I'm at least pointing you in the right direction.
Tested the above rules. ISP server can't be connected.

I have to run```

iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

```
to stop iptables before ISP can be connected.

I comment out this line;```

/sbin/iptables -A INPUT -s workstation-public-IP -p tcp --dport 22 -j ACCEPT

```
Because I have only one public_IP.  I also tested it putting the public_IP there but still fail.  Network not rechargeable.


Others noted with thanks


Edit:
(Correction)
Warning;
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
...


B.R.
satimis

---

### Post by The Cog on 2008-02-22
I wasn't aware you were doing any NAT or mangling.

You didn't specify you wanted to allow pings. This line should allow them in:
/sbin/iptables -A INPUT -p icmp --icmp-type echo-request
/sbin/iptables -A OUTPUT -p icmp --icmp-type echo-request

The command iptables -L -nv
will show you the rules and how many packets/bytes are matching each rule, which may help fault-finding. Also you can add a line
iptables -A INPUT -j LOG
which if at the end of the chain will log packets that are about to receive the default policy (which is to drop).

---

### Post by satimis on 2008-02-22
> **The Cog said:**
> I wasn't aware you were doing any NAT or mangling.

You didn't specify you wanted to allow pings. This line should allow them in:
/sbin/iptables -A INPUT -p icmp --icmp-type echo-request
/sbin/iptables -A OUTPUT -p icmp --icmp-type echo-request
Performed another test;

Put the rules on /etc/rc.local

$ cat /etc/rc.local```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#exit 0


# INPUT

# Set the default policy to drop
iptables -P INPUT DROP

# Allow existing connections to continue
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A INPUT -i lo -j ACCEPT

# allow all VMware MUI HTTP connections in from anywhere
iptables -A INPUT -p tcp --dport 8222 -j ACCEPT

# allow all VMware MUI HTTPS connections in from anywhere
iptables -A INPUT -p tcp --dport 8333 -j ACCEPT

# allow all VMware Authorization Daemon connections in from anywhere
iptables -A INPUT -p tcp --dport 902 -j ACCEPT

# Allow ssh from workstation local IP
iptables -A INPUT -s 192.168.0.11 -p tcp --dport 22 -j ACCEPT

# Allow ssh from workstation public IP
iptables -A INPUT -s 220.232.213.178 -p tcp --dport 22 -j ACCEPT

iptables -A INPUT -p icmp --icmp-type echo-request
iptables -A INPUT -j LOG


# OUTPUT

# Set the default policy to drop
iptables -P OUTPUT DROP

# Allow existing connections to continue
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A OUTPUT -d 127.0.0.1 -j ACCEPT

# Allow DNS requests out
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT

iptables -A OUTPUT -p icmp --icmp-type echo-request

```

Reboot PC


$ ping -c3 192.168.0.1 (gateway) ```

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2002ms

```


$ ping -c3 192.168.0.10 (router IP) ```

PING 192.168.0.10 (192.168.0.10) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.0.10 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2003ms

```

Can't connect ISP server

$ sudo iptables -L -nv```

Password:
Chain INPUT (policy DROP 14 packets, 713 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   33  5699 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8222 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8333 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:902 
    0     0 ACCEPT     tcp  --  *      *       192.168.0.11         0.0.0.0/0           tcp dpt:22 
    0     0 ACCEPT     tcp  --  *      *       220.232.213.178      0.0.0.0/0           tcp dpt:22 
    0     0            icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
   14   713 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy DROP 98 packets, 6216 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   18  1457 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     0    --  *      *       0.0.0.0/0            127.0.0.1           
   15   995 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
   14  1176            icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 

```


Run following commands
$ sudo iptables -F
Password:
$ sudo iptables -X
$ sudo iptables -P INPUT ACCEPT
$ sudo iptables -P FORWARD ACCEPT
$ sudo iptables -P OUTPUT ACCEPT


$ sudo iptables -L -nv```

Chain INPUT (policy ACCEPT 7075 packets, 7478K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 5398 packets, 730K bytes)
 pkts bytes target     prot opt in     out     source               destination         

```


$ ping -c3 192.168.0.1 (gateway) ```

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=150 time=0.629 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=150 time=0.702 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=150 time=0.688 ms

```


ISP can be connected and Internet browsing works


Would it be the problem of /etc/hosts.allow
???


$ cat /etc/hosts.allow```

sshd: 127.0.0.1

# Domain
sshd: .satimis.com

# Pacific from home
sshd: *.isp_domain.com

sshd sshd1 sshd2 : ALL : ALLOW

ALL:centos.satimis.com 192.168.0.20 *.satimis.com .satimis.com

```
192.168.0.20 is the IP addr of Cento running on VMWare


> 
Also you can add a line
iptables -A INPUT -j LOG
which if at the end of the chain will log packets that are about to receive the default policy (which is to drop).
$ sudo tail /var/log/messages```

Feb 23 12:12:23 mail kernel: [  363.671966] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=65.55.209.14
5 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=6814 DF PROTO=TCP SPT=61990 DPT=80 WINDOW=65535 RES=0x00 SYN UR
GP=0 
Feb 23 12:12:35 mail kernel: [  375.689262] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=65.55.209.14
5 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=12473 DF PROTO=TCP SPT=62712 DPT=80 WINDOW=65535 RES=0x00 SYN U
RGP=0 
Feb 23 12:12:38 mail kernel: [  378.755752] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=65.55.209.14
5 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=14480 DF PROTO=TCP SPT=62712 DPT=80 WINDOW=65535 RES=0x00 SYN U
RGP=0 
Feb 23 12:12:44 mail kernel: [  384.865242] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=65.55.209.14
5 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=17865 DF PROTO=TCP SPT=62712 DPT=80 WINDOW=65535 RES=0x00 SYN U
RGP=0 
Feb 23 12:12:57 mail kernel: [  396.992634] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=65.55.209.14
5 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=23749 DF PROTO=TCP SPT=62873 DPT=80 WINDOW=65535 RES=0x00 SYN U
RGP=0 
Feb 23 12:13:00 mail kernel: [  400.049258] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=65.55.209.14
5 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=25315 DF PROTO=TCP SPT=62873 DPT=80 WINDOW=65535 RES=0x00 SYN U
RGP=0 
Feb 23 12:13:06 mail kernel: [  406.062083] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=65.55.209.14
5 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=27960 DF PROTO=TCP SPT=62873 DPT=80 WINDOW=65535 RES=0x00 SYN U
RGP=0 
Feb 23 12:13:12 mail kernel: [  412.099687] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 
DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=38 PROTO=2 
Feb 23 12:15:18 mail kernel: [  537.989255] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 
DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39 PROTO=2 
Feb 23 12:17:24 mail kernel: [  663.878665] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 
DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=40 PROTO=2 

```

Which other files shall I check other than "messages"?  Thanks


Edit:

The problem unable to connect ISP comes on following line;```

iptables -P INPUT DROP

```
After commenting it out, ISP can be connected.


Edit:

Ubuntu can ssh-connect Arch on LAN and also Arch can ssh-connect Ubuntu.


But on Arch

$ ssh satimis.com```

ssh: connect to host satimis.com port 22: Connection refused

```
unable to connect Ubuntu w/o port 22 forwarded on router.  If on router port 22 forwarded to Ubuntu router IP then it works seamlessly.



B.R.
satimis

---

### Post by The Cog on 2008-02-23
I'm an idiot! I missed the -j ACCEPT clause off of the icmp rules. Sorry. Try these instead:
/sbin/iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
/sbin/iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

/var/log/messages is an OK place to see the log output. But all I can see there are some incoming HTTP connections (which are not allowed of course) and some IGMP which is not allowed, and probablu not interesting either.

---

### Post by satimis on 2008-02-23
> **The Cog said:**
> I'm an idiot! I missed the -j ACCEPT clause off of the icmp rules. Sorry. Try these instead:
/sbin/iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
/sbin/iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

/var/log/messages is an OK place to see the log output. But all I can see there are som incoming HTTP connections (which are not allowed of course) and some IGMP which is not allowed, adn probablu not interesting either.
For your info following rules also work here with the line "iptables -A INPUT -p tcp --dport 22 -j DROP" added after "iptables -A INPUT -s 192.168.0.52 -p tcp --dport 22 -j ACCEPT"

$ cat /etc/rc.local```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#exit 0


# INPUT

# Set the default policy to drop
#iptables -P INPUT DROP

# Allow existing connections to continue
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A INPUT -i lo -j ACCEPT

# allow all VMware MUI HTTP connections in from anywhere
iptables -A INPUT -p tcp --dport 8222 -j ACCEPT

# allow all VMware MUI HTTPS connections in from anywhere
iptables -A INPUT -p tcp --dport 8333 -j ACCEPT

# allow all VMware Authorization Daemon connections in from anywhere
iptables -A INPUT -p tcp --dport 902 -j ACCEPT

# Allow ssh from workstation local IP
iptables -A INPUT -s 192.168.0.52 -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j DROP  #added

# Allow ssh from workstation public IP
iptables -A INPUT -s 220.232.213.178 -p tcp --dport 22 -j ACCEPT

iptables -A INPUT -p icmp --icmp-type echo-request
iptables -A INPUT -j LOG


# OUTPUT

# Set the default policy to drop
iptables -P OUTPUT DROP

# Allow existing connections to continue
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A OUTPUT -j ACCEPT

# Allow DNS requests out
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT

iptables -A OUTPUT -p icmp --icmp-type echo-request

```


However on Arch to run "ssh satimis.com" port 22 forwarding is still needed.  It seems to me no clue on rules can replace it.


Test your suggestion.  It works.  Thanks

$ cat /etc/rc.local```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#exit 0


# INPUT

# Set the default policy to drop
iptables -P INPUT DROP

# Allow existing connections to continue
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A INPUT -i lo -j ACCEPT

# allow all VMware MUI HTTP connections in from anywhere
iptables -A INPUT -p tcp --dport 8222 -j ACCEPT

# allow all VMware MUI HTTPS connections in from anywhere
iptables -A INPUT -p tcp --dport 8333 -j ACCEPT

# allow all VMware Authorization Daemon connections in from anywhere
iptables -A INPUT -p tcp --dport 902 -j ACCEPT

# Allow ssh from workstation local IP
iptables -A INPUT -s 192.168.0.52 -p tcp --dport 22 -j ACCEPT

# Allow ssh from workstation public IP
iptables -A INPUT -s 220.232.213.178 -p tcp --dport 22 -j ACCEPT

iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -j LOG


# OUTPUT

# Set the default policy to drop
iptables -P OUTPUT DROP

# Allow existing connections to continue
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A OUTPUT -j ACCEPT

# Allow DNS requests out
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT

iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

```

ssh connection works both way.  But "ssh satimis.com" still needs port 22 forwarded on router.


$ tail /var/log/messages```

Feb 23 21:51:25 mail kernel: [  277.128189] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:0
0:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=192.168.0.255 LEN=167 TOS=0x00 PREC=0
x00 TTL=150 ID=919 PROTO=UDP SPT=1837 DPT=162 LEN=147 
Feb 23 21:51:26 mail kernel: [  278.095544] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:0
0:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=192.168.0.255 LEN=169 TOS=0x00 PREC=0
x00 TTL=150 ID=920 PROTO=UDP SPT=1838 DPT=162 LEN=149 
Feb 23 21:51:28 mail kernel: [  279.268622] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:0
0:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=192.168.0.255 LEN=167 TOS=0x00 PREC=0
x00 TTL=150 ID=921 PROTO=UDP SPT=1839 DPT=162 LEN=147 
Feb 23 21:51:28 mail kernel: [  279.400551] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:0
0:16:b6:c9:8a:a9:08:00 SRC=220.232.213.178 DST=192.168.0.10 LEN=60 TOS=0x00 PREC
=0x00 TTL=63 ID=1259 DF PROTO=TCP SPT=51707 DPT=443 WINDOW=5840 RES=0x00 SYN URG
P=0 
Feb 23 21:51:29 mail kernel: [  280.225675] IN=eth0 OUT= MAC=01:00:5e:00:00:01:0
0:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 T
TL=1 ID=20 PROTO=2 
Feb 23 21:51:46 mail kernel: [  298.023343] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:0
0:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=192.168.0.255 LEN=167 TOS=0x00 PREC=0
x00 TTL=150 ID=922 PROTO=UDP SPT=1840 DPT=162 LEN=147 
Feb 23 21:51:51 mail kernel: [  303.056667] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:0
0:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=192.168.0.255 LEN=169 TOS=0x00 PREC=0
x00 TTL=150 ID=923 PROTO=UDP SPT=1841 DPT=162 LEN=149 
Feb 23 21:51:55 mail kernel: [  307.047579] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:0
0:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=192.168.0.255 LEN=169 TOS=0x00 PREC=0
x00 TTL=150 ID=924 PROTO=UDP SPT=1842 DPT=162 LEN=149 
Feb 23 21:51:56 mail kernel: [  307.677253] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:0
0:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=192.168.0.255 LEN=169 TOS=0x00 PREC=0
x00 TTL=150 ID=925 PROTO=UDP SPT=1843 DPT=162 LEN=149 
Feb 23 21:52:16 mail kernel: [  327.339456] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:0
0:16:b6:c9:8a:a9:08:00 SRC=220.232.213.178 DST=192.168.0.10 LEN=60 TOS=0x00 PREC
=0x00 TTL=63 ID=1260 DF PROTO=TCP SPT=51707 DPT=443 WINDOW=5840 RES=0x00 SYN URG
P=0 

```



Edit:

With your last modified rules, "satimis.com/mail" can't start SquirrelMail



B.R.
satimis

---

### Post by The Cog on 2008-02-23
I don't under stand your reasoning for adding that DROP line. It will prevent ever accepting SSH from the workstation public address.

And I don't understand what you're sayng about router forwarding. You haven't moved the server the the CoLo yet, have you? Are you trying to call out to the internet and back in again - out and in throught the same router? If so, I don't believe that will ever work. So you won't be able to test accepting calls from your workstation public address until you have moved the server elsewhere.

---

### Post by satimis on 2008-02-24
Hi The Cog,


Today I'm stuck.


Ubuntu server can ping Internet/gateway but unable to browse Internet.  Arch can ssh-connect Ubunbu.  But Ubuntu can't ssh-connect Arch


On Arch

$ ssh 192.168.0.10```

Ubuntu 7.04
Welcome to my server
satimis@192.168.0.10's password: 
Linux mail.satimis.com 2.6.20-16-generic #2 SMP Tue Feb 12 02:11:24 UTC 2008 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have mail.
Last login: Sun Feb 24 21:57:18 2008
```


$ ping -c3 yahoo.com```

PING yahoo.com (66.94.234.13) 56(84) bytes of data.
64 bytes from w2.rc.vip.scd.yahoo.com (66.94.234.13): icmp_seq=1 ttl=56 time=246 ms
64 bytes from w2.rc.vip.scd.yahoo.com (66.94.234.13): icmp_seq=2 ttl=55 time=248 ms
64 bytes from w2.rc.vip.scd.yahoo.com (66.94.234.13): icmp_seq=3 ttl=56 time=247 ms

--- yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 246.963/247.490/248.055/0.603 ms

```


$ sudo iptables -L -nv```

Password:
Chain INPUT (policy DROP 10 packets, 566 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  193 17851 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8222 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8333 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:902 
    1    52 ACCEPT     tcp  --  *      *       192.168.0.52         0.0.0.0/0           tcp dpt:22 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
   10   566 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy DROP 48 packets, 2880 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  118 12379 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     0    --  *      *       0.0.0.0/0            127.0.0.1           
    3   205 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
   11   924 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 

```


$ tail /var/log/messages```

Feb 24 21:57:01 mail kernel: [   70.935511] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=220.232.213.178 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=12052 DF PROTO=TCP SPT=59480 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 24 21:57:04 mail kernel: [   73.929030] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=220.232.213.178 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=12053 DF PROTO=TCP SPT=59480 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 24 21:57:10 mail kernel: [   79.922178] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=220.232.213.178 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=12054 DF PROTO=TCP SPT=59480 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 24 21:57:22 mail kernel: [   91.908446] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=220.232.213.178 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=12055 DF PROTO=TCP SPT=59480 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb 24 21:58:47 mail kernel: [  176.542326] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=103 PROTO=2 
Feb 24 21:58:55 mail kernel: [  184.720330] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=192.168.0.255 LEN=150 TOS=0x00 PREC=0x00 TTL=150 ID=1063 PROTO=UDP SPT=1933 DPT=162 LEN=130 
Feb 24 21:58:55 mail kernel: [  184.720584] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=83.23.82.41 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=53334 DF PROTO=TCP SPT=2492 DPT=25 WINDOW=64240 RES=0x00 SYN URGP=0 
Feb 24 21:58:58 mail kernel: [  187.649462] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=83.23.82.41 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=53499 DF PROTO=TCP SPT=2492 DPT=25 WINDOW=64240 RES=0x00 SYN URGP=0 
Feb 24 21:59:04 mail kernel: [  193.679189] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:00:16:b6:c9:8a:a9:08:00 SRC=83.23.82.41 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=53652 DF PROTO=TCP SPT=2492 DPT=25 WINDOW=64240 RES=0x00 SYN URGP=0 
Feb 24 22:00:53 mail kernel: [  302.431671] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=104 PROTO=2 

```


$ cat /etc/rc.local```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#exit 0


# INPUT

# Set the default policy to drop
iptables -P INPUT DROP

# Allow existing connections to continue
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A INPUT -i lo -j ACCEPT

# allow all VMware MUI HTTP connections in from anywhere
iptables -A INPUT -p tcp --dport 8222 -j ACCEPT

# allow all VMware MUI HTTPS connections in from anywhere
iptables -A INPUT -p tcp --dport 8333 -j ACCEPT

# allow all VMware Authorization Daemon connections in from anywhere
iptables -A INPUT -p tcp --dport 902 -j ACCEPT

# Allow ssh from workstation local IP
iptables -A INPUT -s 192.168.0.52 -p tcp --dport 22 -j ACCEPT

# Allow ssh from workstation public IP
#iptables -A INPUT -s 220.232.213.178 -p tcp --dport 22 -j ACCEPT

iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -j LOG


# OUTPUT

# Set the default policy to drop
iptables -P OUTPUT DROP

# Allow existing connections to continue
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A OUTPUT -d 127.0.0.1 -j ACCEPT

# Allow DNS requests out
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT

iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

```


I have the above rules copied on /etc/network/if-up.d/iptables.start file.  So that on booting when the network is connected iptables starts to run.


$ cat /etc/network/if-up.d/iptables.start```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#exit 0


# INPUT

# Set the default policy to drop
iptables -P INPUT DROP

# Allow existing connections to continue
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A INPUT -i lo -j ACCEPT

# allow all VMware MUI HTTP connections in from anywhere
iptables -A INPUT -p tcp --dport 8222 -j ACCEPT

# allow all VMware MUI HTTPS connections in from anywhere
iptables -A INPUT -p tcp --dport 8333 -j ACCEPT

# allow all VMware Authorization Daemon connections in from anywhere
iptables -A INPUT -p tcp --dport 902 -j ACCEPT

# Allow ssh from workstation local IP
iptables -A INPUT -s 192.168.0.52 -p tcp --dport 22 -j ACCEPT
#iptables -A INPUT -p tcp --deport 22 -j DROP

# Allow ssh from workstation public IP
iptables -A INPUT -s 220.232.213.178 -p tcp --dport 22 -j ACCEPT

iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -j LOG



# OUTPUT

# Set the default policy to drop
iptables -P OUTPUT DROP

# Allow existing connections to continue
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A OUTPUT -d 127.0.0.1 -j ACCEPT 

# Allow DNS requests out
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT

iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

```


Another problem encountered is;

sudo /etc/rc.local  start/stop doesn't work.


Advice would be appreciated.  TIA


> **The Cog said:**
> I don't under stand your reasoning for adding that DROP line. It will prevent ever accepting SSH from the workstation public address.

On my previous test I commented out the 1st line "iptables -P INPUT DROP".  Therefore I added that line to replace it.  It has be erased later.


> 
And I don't understand what you're sayng about router forwarding. You haven't moved the server the the CoLo yet, have you? Are you trying to call out to the internet and back in again - out and in throught the same router? If so, I don't believe that will ever work. So you won't be able to test accepting calls from your workstation public address until you have moved the server elsewhere.
That is really my problem.  I have only one public IP here.  How can I test the rules before shipping the PC for colo?  Can I test it via a proxy server?


B.R.
satimis

---

### Post by The Cog on 2008-02-24
This is as it should be. You have applied vey restrictive rules on what protocols are allowed out of the server. You did not specify that the server should be allowed to SSH to anywhere. It might be better if you do not apply any outgoing rules - leave the default as ACCEPT like this:
iptables -P OUTPUT ACECEPT
then the server can make any outgoing connections it wants. You are still being restrictive about letting the bad guys connect to the server.

For testing the rule about your public address locally, I suggest this approach:
1) Configure your server to use your workstation as its default gateway.
2) Add a secondary address of your public address to your worksation eth0 like this:
sudo ifconfig eth0:1 1.2.3.4
or whatever your public address is.
2) SSH tp the server from the workstation, using your public address as the source address:
ssh -b 1.2.3.4 192.168.0.51

---

### Post by satimis on 2008-02-24
> **The Cog said:**
> This is as it should be. You have applied vey restrictive rules on what protocols are allowed out of the server. You did not specify that the server should be allowed to SSH to anywhere. It might be better if you do not apply any outgoing rules - leave the default as ACCEPT like this:
iptables -P OUTPUT ACECEPT
then the server can make any outgoing connections it wants. You are still being restrictive about letting the bad guys connect to the server.
Thanks.  After changing DROP as ACCEPT then Internet can be browsed and Arch can be ssh-connected.

I'll change it back to "DROP" before shipping the PC for colo.


> 
For testing the rule about your public address locally, I suggest this approach:
1) Configure your server to use your workstation as its default gateway.
2) Add a secondary address of your public address to your worksation eth0 like this:
sudo ifconfig eth0:1 1.2.3.4
or whatever your public address is.
2) SSH tp the server from the workstation, using your public address as the source address:
ssh -b 1.2.3.4 192.168.0.51

Performed following test;


On Ubuntu

$ cat /etc/network/interfaces```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast  192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 202.14.67.4 202.14.67.14
......

```
Change "gateway 192.168.0.1" to "gateway 1.2.3.4"

$ sudo /etc/init.d/networking restart```

 * Reconfiguring network interfaces...                                          SIOCADDRT: Network is unreachable
Failed to bring up eth0.
                                                                         [ OK ]

```


On Arch

$ sudo ifconfig eth0:1 1.2.3.4
No complaint


$ sudo ifconfig```

eth0      Link encap:Ethernet  HWaddr 00:13:D4:FE:DA:87  
          inet addr:192.168.0.52  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fefe:da87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2739 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:223972 (218.7 Kb)  TX bytes:411668 (402.0 Kb)
          Interrupt:20 Base address:0xc000 

eth0:1    Link encap:Ethernet  HWaddr 00:13:D4:FE:DA:87  
          inet addr:1.2.3.4  Bcast:1.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:280 (280.0 b)  TX bytes:280 (280.0 b)

```


$ ssh -b 1.2.3.4 192.168.0.52```

ssh_exchange_identification: Connection closed by remote host

```

Still fail.



Edit:

SquirrelMail needs port 443 to work.  So just add this port on the rules with following line;```

iptable -A INPUT -p tcp --dport 443 -j ACCEPT

```


However following 2 problems still unsolved.

1)
To start SM, must run;
[https://satimis.com/mail](https://satimis.com/mail)

[http://satimis.com/mail](http://satimis.com/mail) w/o "s" doesn't work


2)
Unable to start webmin and usermin.  They need ports 20000 and 10000 respectively to work.  However adding these ports to rules does not work.


Any clue,  TIA


B.R.
satimis

---

### Post by The Cog on 2008-02-25
Firstly, use the local address of your workstation 192.168.0.11 as Ubuntus defaut gateway, not the publc address which we have already decided is unreachable from inside your network.

Second, don't use 1.2.3.4, replace this with the public address of your workstation whatever that may be. It is your public address that you are trying to test. Still, we have proved that address 1.2.3.4 cannot SSH to the server, which is something.

You won't be able to connect to [www.satimis.com](www.satimis.com) from inside your network. If that refers to your home network then we have already established that you can't reach that publuc address from inside, and if it refers to the server's public address, I thought you haven't installed the server at taht site yet.

---

### Post by satimis on 2008-02-25
> **The Cog said:**
> Firstly, use the local address of your workstation 192.168.0.11 as Ubuntus defaut gateway, not the publc address which we have already decided is unreachable from inside your network.

Second, don't use 1.2.3.4, replace this with the public address of your workstation whatever that may be. It is your public address that you are trying to test. Still, we have proved that address 1.2.3.4 cannot SSH to the server, which is something.

Performed following test;


On Ubuntu

On /etc/network/interfaces

changing
gateway 192.168.0.1


as;
gateway 192.168.0.52
(the router IP of Arch, the workstation)

$ sudo /etc/init.d/networking restart```

 * Reconfiguring network interfaces...                                          SIOCDELRT: No such process
                                                                         [ OK ]

```

Still failed.


On Arch, the workstation

Run;

$ sudo ifconfig eth0:1 220.232.213.178
No complaint


$ ifconfig```

eth0      Link encap:Ethernet  HWaddr 00:13:D4:FE:DA:87  
          inet addr:192.168.0.52  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fefe:da87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69069 (67.4 Kb)  TX bytes:32747 (31.9 Kb)
          Interrupt:20 Base address:0xc000 

eth0:1    Link encap:Ethernet  HWaddr 00:13:D4:FE:DA:87  
          inet addr:220.232.213.178  Bcast:220.232.213.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:280 (280.0 b)  TX bytes:280 (280.0 b)

```


$ ssh -b 220.232.213.178 192.168.0.52```

ssh_exchange_identification: Connection closed by remote host

```


$ tail /var/log/messages```

Feb 25 19:53:06 mail kernel: [ 1337.751177] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:0
0:16:b6:c9:8a:a9:08:00 SRC=222.136.142.57 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=
0x00 TTL=115 ID=23017 DF PROTO=TCP SPT=2725 DPT=25 WINDOW=65535 RES=0x00 SYN URG
P=0 
Feb 25 19:53:09 mail kernel: [ 1340.579854] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:0
0:16:b6:c9:8a:a9:08:00 SRC=222.136.142.57 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=
0x00 TTL=115 ID=23450 DF PROTO=TCP SPT=2725 DPT=25 WINDOW=65535 RES=0x00 SYN URG
P=0 
Feb 25 19:53:15 mail kernel: [ 1346.593067] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:0
0:16:b6:c9:8a:a9:08:00 SRC=222.136.142.57 DST=192.168.0.10 LEN=48 TOS=0x00 PREC=
0x00 TTL=115 ID=23972 DF PROTO=TCP SPT=2725 DPT=25 WINDOW=65535 RES=0x00 SYN URG
P=0 
Feb 25 19:53:40 mail kernel: [ 1370.942560] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:0
0:16:b6:c9:8a:a9:08:00 SRC=63.150.131.10 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0
x00 TTL=59 ID=15752 DF PROTO=TCP SPT=80 DPT=54880 WINDOW=6624 RES=0x00 ACK FIN U
RGP=0 
Feb 25 19:53:40 mail kernel: [ 1371.047527] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:0
0:16:b6:c9:8a:a9:08:00 SRC=63.150.131.10 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0
x00 TTL=59 ID=8511 DF PROTO=TCP SPT=80 DPT=54881 WINDOW=7784 RES=0x00 ACK FIN UR
GP=0 
Feb 25 19:53:40 mail kernel: [ 1371.483816] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:0
0:16:b6:c9:8a:a9:08:00 SRC=63.150.131.10 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0
x00 TTL=59 ID=15753 DF PROTO=TCP SPT=80 DPT=54880 WINDOW=6624 RES=0x00 ACK FIN U
RGP=0 
Feb 25 19:53:40 mail kernel: [ 1371.597760] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:0
0:16:b6:c9:8a:a9:08:00 SRC=63.150.131.10 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0
x00 TTL=59 ID=8512 DF PROTO=TCP SPT=80 DPT=54881 WINDOW=7784 RES=0x00 ACK FIN UR
GP=0 
Feb 25 19:53:41 mail kernel: [ 1372.568699] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:0
0:16:b6:c9:8a:a9:08:00 SRC=63.150.131.10 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0
x00 TTL=59 ID=15754 DF PROTO=TCP SPT=80 DPT=54880 WINDOW=6624 RES=0x00 ACK FIN U
RGP=0 
Feb 25 19:53:41 mail kernel: [ 1372.700876] IN=eth0 OUT= MAC=00:0e:a6:f9:a3:5b:0
0:16:b6:c9:8a:a9:08:00 SRC=63.150.131.10 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0
x00 TTL=59 ID=8513 DF PROTO=TCP SPT=80 DPT=54881 WINDOW=7784 RES=0x00 ACK FIN UR
GP=0 
Feb 25 19:53:47 mail kernel: [ 1377.989177] IN=eth0 OUT= MAC=01:00:5e:00:00:01:0
0:16:b6:c9:8a:a9:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 T
TL=1 ID=42 PROTO=2 

```


Others noted with thanks


satimis

---

### Post by satimis on 2008-02-25
Hi The Cog,


Another thought.

I'm considering asking my friends assisting me testing the rules.  However all of them are running MS Windows and dynamic IP w/o ssh installed.  


For their public IP addr;
I'll request them to run "ipconfig" on DOS window to find out (I hope IIRC.  I haven't run MS Windows >7 years).  Their public IP addr only change on reboot.  Then I can adjust the rules before test started allowing them coming in.


I still can't find a way to solve "ssh".  I don't know whether it runs on MS Windows?  Besides my friends are NOT knowledgeable on software installation.  I don't expect running their workstation into trouble because of my test.


I think the last restore will be asking them burning a Live CD such as Knoppix and run the same on their workstation.  I hope ssh client and server are running on Knoppix.  Otherwise I have to find another Linux Live CD (there are plenty of them  available on Internet).  Immediately off my head is Scientific Linux, etc.


Any suggestion?  TIA


B.R.
satimis

---


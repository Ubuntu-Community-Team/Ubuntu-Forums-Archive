---
title: "OpenSSH on a unique port instead of the default 22 does not work from outside the LAN"
date: 2013-10-14
forum: Server Platforms
---

### Post by ub9sd12 on 2013-10-14
Have been experimenting with ssh connection by changing the default port for sshd in sshd_config on ubuntu 13.04. I was successfully able to ssh from inside the LAN and have been trying different ways to ssh in from outside my home network but have had no luck. Any help would be much appreciated!

Can listen on the unique port:

```

tomack12@gart23:~$ sudo netstat -nlp | grep -e sshd
tcp        0      0 0.0.0.0:3889           0.0.0.0:*               LISTEN      905/sshd        
tcp6       0      0 :::3889                 :::*                    LISTEN      905/sshd        

```

opened the unique port on the internal firewall:

```

tomack12@gart23:~$ sudo ufw status | grep 3889
3889                     ALLOW       Anywhere
3889/tcp                   ALLOW       192.0.0.0/6
3889/tcp                   ALLOW       192.168.1.64
3889                       ALLOW       Anywhere (v6)

```

opened the unique port on the router:

```

# iptables -L -t nat | grep 3889
ACCEPT     tcp  --  anywhere             adsl-203-147-115-21.ncp.bellsouth.net tcp dpt:3889 
ACCEPT     tcp  --  anywhere             www.routerlogin.com tcp dpt:3889 

```

What am i do wrong? Not wanting to give up and hoping someone out there has come across a similar situation.

---

### Post by hawkmage on 2013-10-14
If your NAT is correct I do not see any issues with you posted.  Since you can SSH to the system using port 3889 form the internal network the Firewall and SSH config on tomack12 is working so I would focus on the NAT on the router.  

On your router I assume if your cat /proc/sys/net/ipv4/ip_forward you get a 1 indicating that IPv4 forwarding is on.  Also that cat /proc/sys/net/ipv6/conf/all/forwarding or cat /proc/sys/net/ipv6/conf/<ExtIFace>/forwarding shows 1 if you are doing IPv6 forwarding as well.

I got port forwarding working on an Ubuntu LTS with the following:
```
# Always accept loopback trafficiptables -A INPUT -i lo -j ACCEPT


# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW ! -i eth0 -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT


# Allow outgoing connections from the LAN side.
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT


# Masquerade.
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE


iptables -A FORWARD -i eth0 -o eth1 -p tcp --dport 3889 -j ACCEPT
iptables -A PREROUTING -t nat -p tcp -i eth0 --dport 3889 -j DNAT --to 192.168.1.102:22


# Don't forward from the outside to the inside.
iptables -A FORWARD -i eth1 -o eth1 -j REJECT
```

The eth0 is the external interface and the eth1 is the internal.  

When behind a NAT I usually leave the SSH config alone and just NAT from the incoming port you want to use to the destination port of 22.

---

### Post by scbingham on 2013-10-15
hawkmage is quite correct, no need to change your internal port set up, all you need is to change the port forwarding settings in your router.
Choose a port above 10000, this will reduce unwanted break in attempts & then just point this to your internal port 22

---

### Post by TheFu on 2013-10-15
Some ISPs block unusual inbound ports. I'm 100% positive that many companies and hotels do this.

I agree with using the router to perform port translation, don't bother changing the default port 22/tcp on the server. This way, you can easily know if you are using an internal or external route in your testing.

Be certain to setup ~/.ssh/config with the alternative name and port on the clients. Makes life so much easier and pretty much every ssh-using client will honor those settings.  ssh, scp, sftp, rsync, rdiff-backup ... will. No need to specify the port or different userids this way, plus giving each stanza a nice nickname keeps confusion down.

Plus denyhosts or fail2ban default settings assume port22 ... using defaults on the server makes life easier and the monitoring and blocks work exactly the same with translated traffic from the router.

---

### Post by ub9sd12 on 2013-10-16
Thanks guys!

Here's the status of my NAT forwarding. It is interesting that only IPV6 is not forwarding?

```

# cat /proc/sys/net/ipv4/ip_forward
1
# cat /proc/sys/net/ipv6/conf/all/forwarding
2
# cat /proc/sys/net/ipv6/conf/eth0/forwarding
2
# cat /proc/sys/net/ipv6/conf/eth1/forwarding
2

```

hawkmage - i have a few questions before i can execute your code example for iptables. Is 'MASQUERADE' essential for the below 'FORWARD' and 'PREROUTING'?
Also, for the PREROUTING, the internal IP address with the ssh port specification should be the IP of the router. is this correct? and i should change the port specified in the sshd_config from 3889 back to 22. is this also correct?

```

iptables -A FORWARD -i eth0 -o eth1 -p tcp --dport 3889 -j ACCEPT 
iptables -A PREROUTING -t nat -p tcp -i eth0 --dport 3889 -j DNAT --to 192.168.1.102:22

```

Appreciate all your help!

---

### Post by TheFu on 2013-10-16
I'm confused.  If you have a separate router, then you don't need forward or pre-routing in your IP tables.  On the ssh server, just blocking is needed and denyhosts or fail2ban will do that well.

OTOH, if you are trying to use Linux as a router, then you don't want to install anything else on the same box - it really needs to be a single-purpose install following best practices.

Or I could be missing the entire purpose here.

---

### Post by Doug S on 2013-10-16
> **ub9sd12 said:**
> i have a few questions before i can execute [the] code example for iptables. Is 'MASQUERADE' essential for the below 'FORWARD' and 'PREROUTING'?Yes. It is required for the return path.> **ub9sd12 said:**
> Also, for the PREROUTING, the internal IP address with the ssh port specification should be the IP of the router. is this correct?No. The IP address should be your destination computer (if the firewall/router computer and the SSH computer are the same computer, that is a different story). > **ub9sd12 said:**
> and i should change the port specified in the sshd_config from 3889 back to 22. is this also correct?Yes.

I am curious about this:```

iptables -A FORWARD -i eth0 -o eth1 -p tcp --dport [COLOR=#ff0000]3889[/COLOR] -j ACCEPT 
iptables -A PREROUTING -t nat -p tcp -i eth0 --dport 3889 -j DNAT --to 192.168.1.102:22
``` because I think it should be this (where ESTABLISHED, RELATED is dealt with elsewhere, but that is not what I am curious about):```

iptables -A FORWARD -i eth0 -o eth1 -p tcp --dport [COLOR=#ff0000]22[/COLOR] -d 192.168.1.102 -m state --state NEW -j ACCEPT 
iptables -A PREROUTING -t nat -p tcp -i eth0 --dport 3889 -j DNAT --to 192.168.1.102:22
```

Edit: I was off typing and such for quite awhile, and I did not see the post by TheFu.

---

### Post by ub9sd12 on 2013-10-16
TheFlu - My bad! I should have clearly stated that the iptables rules where i'm attempting the port forward is on a netgear router that is linux based. SSH as a service is enabled on Ubuntu 13.04 (a completely separate device acting as a server) and ufw, fail2ban activated with the blocks.

---

### Post by hawkmage on 2013-10-16
If you are trying to NAT the IPv6 the way you are doing the IPv4 but use ip6tables instead of iptables

---

### Post by ub9sd12 on 2013-10-31
Still unable to access SSH via. port forward using default port 22. Not able to determine what is causing me to not open the port externally. I'm now using  dd-wrt for the port forward with a dynamic dns assignment using  no-ip and dnsomatic services. posting some details below and any help is  appreciated. 
 
Open SSH (Port 22) on IP: 192.168.11.13 
 
[TABLE="width: 90%, align: center"]
[TR]
 	  [TD]**Code:**[/TD]
	[/TR]
	[TR]
	  [TD="class: code"] 
tom23@max7:~$ sudo nmap -sT -sU -p 22 192.168.11.13 
 
Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2013-10-26 09:55 EDT 
Nmap scan report for max7 (192.168.11.13) 
Host is up (0.000084s latency). 
PORT   STATE  SERVICE 
22/tcp open   ssh 
22/udp closed ssh 
 
Nmap done: 1 IP address (1 host up) scanned in 0.09 seconds 
[/TD]
	[/TR]
[/TABLE]
 
 
DDNS enabled on DD-WRT router on WAN IP: 192.168.1.66 (LAN IP: 192.168.1.11) 
NOTE: no-ip address below is fictitious 
 
[TABLE="width: 90%, align: center"]
[TR]
 	  [TD]**Code:**[/TD]
	[/TR]
	[TR]
	  [TD="class: code"] 
root@DD_WRT:/tmp/ddns# cat ddns.log 
Sat Oct 26 08:54:01 2013: INADYN: Started 'INADYN Advanced version 1.96-ADV' - dynamic DNS updater. 
Sat Oct 26 08:54:01 2013: INADYN: IP read from cache file is '192.168.1.66'. No update required. 
Sat Oct 26 08:54:01 2013: I:INADYN: IP address for alias 'techie2.no-ip.net' needs update to '192.168.1.66' 
Sat Oct 26 08:54:01 2013: I:INADYN: Alias 'techie2.no-ip.net' to IP '192.168.1.66' updated successfully. 
[/TD]
	[/TR]
[/TABLE]
 
 
WAN IP: 192.168.1.66 is behind a router/adsl on IP: 192.168.1.64 with port forwarding enabled 
 
[TABLE="width: 90%, align: center"]
[TR]
 	  [TD]**Code:**[/TD]
	[/TR]
	[TR]
	  [TD="class: code"] 
# iptables -t nat -vnL PREROUTING 
Chain PREROUTING (policy ACCEPT 50804 packets, 3254K bytes) 
 pkts bytes target     prot opt in     out     source               destination          
   15   915 DNAT       udp  --  group1 *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 dnshj to:192.168.1.64  
 120K 7891K PRE_CNAPT  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
 120K 7891K PT_NAT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            
28868 1951K DNS_RELAY  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53  
 120K 7891K INBOUND_NAT  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
 120K 7891K PRE_VPN    all  --  *      *       0.0.0.0/0            0.0.0.0/0            
 120K 7891K REMOTE_NAT  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
 120K 7891K LOCAL_SERVICE_NAT  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
 120K 7891K USB_NAT    all  --  *      *       0.0.0.0/0            0.0.0.0/0            
 120K 7891K INBOUND_NAT  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
 120K 7891K IM_DETECT_NAT  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
 120K 7891K MINIUPNPD_W  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
 120K 7891K DMZ_NAT    all  --  *      *       0.0.0.0/0            0.0.0.0/0            
31064 2352K CUDP_NAT   udp  --  *      *       0.0.0.0/0            0.0.0.0/0            
 120K 7890K PRE_IGMP   all  --  *      *       0.0.0.0/0            0.0.0.0/0            
    0     0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 to:192.168.1.66:22  
[/TD]
	[/TR]
[/TABLE]
 
 
[TABLE="width: 90%, align: center"]
[TR]
 	  [TD]**Code:**[/TD]
	[/TR]
	[TR]
	  [TD="class: code"] 
# iptables -vnL FORWARD 
Chain FORWARD (policy DROP 0 packets, 0 bytes) 
 pkts bytes target     prot opt in     out     source               destination          
 177K   11M TCPMSS     tcp  --  *      *       0.0.0.0/0             0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU  
4274K  374M HTTP_DETECT  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
4274K  374M OUTBOUND_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
4274K  374M FWD_SPI    all  --  *      *       0.0.0.0/0            0.0.0.0/0            
4269K  374M FWD_VPN    all  --  *      *       0.0.0.0/0            0.0.0.0/0            
4269K  374M FWD_IGMP   all  --  *      *       0.0.0.0/0            0.0.0.0/0            
4269K  374M NAT_LIMIT  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
4269K  374M PT_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
4269K  374M ACCEPT_RULES  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
    0     0 DOS_DETECT  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
    0     0 MINIUPNPD  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
    0     0 INBOUND_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
    0     0 DMZ_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
    0     0 FIREWALL_DISABLE  all  --  *      *       0.0.0.0/0            0.0.0.0/0            
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0             192.168.1.66        tcp dpt:22 state NEW,RELATED,ESTABLISHED  
[/TD]
	[/TR]
[/TABLE]
 
 
WAN IP: 192.168.1.66 (LAN IP: 192.168.11.1) port forwarding to SSH server on IP: 192.168.11.13 
 
[TABLE="width: 90%, align: center"]
[TR]
 	  [TD]**Code:**[/TD]
	[/TR]
	[TR]
	  [TD="class: code"] 
root@DD_WRT:~# iptables -t nat -vnL PREROUTING 
Chain PREROUTING (policy ACCEPT 4701 packets, 380K bytes) 
 pkts bytes target     prot opt in     out     source               destination          
    6   360 DNAT       tcp  --  *      *       0.0.0.0/0            192.168.1.66        tcp dpt:23 to:192.168.11.1:23  
    0     0 DNAT       icmp --  *      *       0.0.0.0/0            192.168.1.66        to:192.168.11.1  
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            192.168.1.66        tcp dpt:22 to:192.168.11.13:22  
    0     0 DNAT       udp  --  *      *       0.0.0.0/0            192.168.1.66        udp dpt:22 to:192.168.11.13:22  
  495 49215 TRIGGER    0    --  *      *       0.0.0.0/0            192.168.1.66        TRIGGER type:dnat match:0 relate:0  
[/TD]
	[/TR]
[/TABLE]
 
 
[TABLE="width: 90%, align: center"]
[TR]
 	  [TD]**Code:**[/TD]
	[/TR]
	[TR]
	  [TD="class: code"] 
root@DD_WRT:~# iptables -vnL FORWARD 
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes) 
 pkts bytes target     prot opt in     out     source               destination          
    0     0 ACCEPT     47   --  *      eth1    192.168.11.0/24      0.0.0.0/0            
    0     0 ACCEPT     tcp  --  *      eth1    192.168.11.0/24      0.0.0.0/0           tcp dpt:1723  
    0     0 ACCEPT     0    --  br0    br0     0.0.0.0/0            0.0.0.0/0           
 5542  330K TCPMSS     tcp  --  *      *       0.0.0.0/0             0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU  
3363K 3702M lan2wan    0    --  *      *       0.0.0.0/0            0.0.0.0/0            
3360K 3702M ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED  
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            192.168.11.13       tcp dpt:22  
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            192.168.11.13       udp dpt:22  
    0     0 TRIGGER    0    --  eth1   br0     0.0.0.0/0            0.0.0.0/0           TRIGGER type:in match:0 relate:0  
 3234  233K trigger_out  0    --  br0    *       0.0.0.0/0            0.0.0.0/0            
 3039  225K ACCEPT     0    --  br0    *       0.0.0.0/0            0.0.0.0/0           state NEW  
  195  8280 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0            [/TD]
[/TR]
[/TABLE]

---

### Post by TheFu on 2013-10-31
> WAN IP: 192.168.1.66 is behind a router/adsl on IP: 192.168.1.64 with port forwarding enabled 

You can't have the WAN and LAN IPs on the same subnet.
No ISP will route to 192.168.x.x addresses.
Those are the issues.

---

### Post by ub9sd12 on 2013-10-31
TheFu - but i do not understand. this set up works internally and i'm able to ssh via. 22 to my server 192.168.11.13 and the LAN IP port forwards 22 to the WAN IP (192.168.1.66 generates 192.168.11.13 via. DHCP)

Also, I'm using the dynamic dns address being updated  by ddclient on my 192.168.11.13 and on 192.168.1.66 by dd-wrt's ddns service so the 192.168.11.13 is updated to the static IP provided by my ISP

---

### Post by TheFu on 2013-10-31
No ISP in the world will route traffic over the internet to any 192.168.x.x addresses. These are private IP address networks.
[http://tools.ietf.org/html/rfc5735](http://tools.ietf.org/html/rfc5735)

If you are lucky, double-NAT is happening and the modem inside your house has a real-public IP.  Use an internet service website to find your real IP - [http://www.whatsmyip.org/](http://www.whatsmyip.org/) is one.

Just reread what you wrote - every "server" needs a static IP - doesn't matter if this is on a public IP or a private one. The router needs a static IP to port forward at.

Perhaps if you drew an ascii picture of the setup, the issue would become clear? 

Here's mine:
```
|____50.x.x.x
|    |____50.x.x.49-ext-router w/ /28 subnet
|    |    |____50.x.x.45-int-router
|    |    |    |____192.168.1.x-internal_subnet /24
|    |    |    |    |____192.168.1.2
|    |    |    |    |____192.168.1.3
|    |    |    |    |____192.168.1.N
|    |    |    |    |____192.168.1.1
|    |    |    |    |____192.168.1.4
```

Hope that helps.

---

### Post by ub9sd12 on 2013-10-31
TheFu - Agreed that no ISP will route traffic over the internet to my internal private 192.168.x.x IP addresses. I am aware of this. Hence I have ddclient installed on my server to update the private IP (static - 192.168.11.13) to the public IP assigned by my ISP. This is the server (installed with OpenSSH) that i am hoping to connect from over the internet with the no-ip dynamic address & via. port 22

Please see ASCII picture of my current setup

```

|___108.x.x.x
|     |___108.x.x.52 - Public IP assigned to Netgear ADSLModem/Router w/ subnet
|     |     |___192.168.1.64 - Private IP assigned to Internal Router (above Netgear ADSLModem/Router) via. DHCP, Internal subnet /7
|     |     |     |___192.168.1.66 - Private WAN IP assigned to second Internal Router (running DD-WRT) via. DHCP from the above /7 pool)
|     |     |     |     |___192.168.11.1 - Private LAN IP assigned to second Internal Router (above DD-WRT device) internal subnet /5
|     |     |     |     |___192.168.11.12
|     |     |     |     |___192.168.11.13 - Linux Server running Open SSH, ddclient (account with no-ip) to update internal 192.168.11.13 to public IP:108.x.x.52
|     |     |     |     |___192.168.11.14
|     |     |     |     |___192.168.11.15

```

Thank you for your assistance.

---

### Post by Doug S on 2013-10-31
You can not do that, for multiple reasons.

You need to do port forwarding twice. Once between 108.X.X.52 to 192.168.1.66, and then again from 192.168.1.66 to 192.168.11.13.

---

### Post by TheFu on 2013-11-01
> **Doug S said:**
> You can not do that, for multiple reasons.

You need to do port forwarding twice. Once between 108.X.X.52 to 192.168.1.66, and then again from 192.168.1.66 to 192.168.11.13.

Actually, he might be able to do it, if the /7 really is a /7.  Though I doubt any ISP has a /7 to provide ... heck - does google have a /7?  I though /8 was a large as the networks got and most 192.168.x.x addresses stick to a /24 to make life easy.

I suspect a network calculator is needed, but if a /7 really is used, then both 192.168.1.x and 19.168.11.x ARE on the same network.  Just because Ive never heard of anyone doing that doesnt mean it didnt happen.

---

### Post by Doug S on 2013-11-01
> **TheFu said:**
> Actually, he might be able to do it, if the /7 really is a /7.  Though I doubt any ISP has a /7 to provide ... heck - does google have a /7?  I though /8 was a large as the networks got and most 192.168.x.x addresses stick to a /24 to make life easy.

I suspect a network calculator is needed, but if a /7 really is used, then both 192.168.1.x and 19.168.11.x ARE on the same network.  Just because Ive never heard of anyone doing that doesnt mean it didnt happen.I do not understand the ISP reference, as isn't all of this stuff internal? Also /7 isn't a legal mask for 192.168.X.X. Also, and as far as I know, any [DHCP server wouldn't have enough memory]("http://ubuntuforums.org/showthread.php?t=2150970&highlight=dhcp") to support a /7 pool. ... Anyway, I suspect you were somewhat joking with the reply, no?

I suspect the OP meant: /25 when /7 was mentioned; /27 when /5 was mentioned; LAN2 when WAN was mentioned; using ddclient (account with no-ip) to associate a domain name with 108.x.x.52 when 192.168.11.13 to public IP:108.x.x.52 was mentioned.

All communication challenges aside, I still think the OP needs to do port forwarding twice. Once between 108.X.X.52 to  192.168.1.66, and then again from 192.168.1.66 to 192.168.11.13.

---

### Post by TheFu on 2013-11-01
> **Doug S said:**
> All communication challenges aside, I still think the OP needs to do port forwarding twice. Once between 108.X.X.52 to  192.168.1.66, and then again from 192.168.1.66 to 192.168.11.13.

I think you are probably correct, but ...  I couldn't be certain.

---


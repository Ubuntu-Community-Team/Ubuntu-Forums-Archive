---
title: "IP Forwarding"
date: 2023-11-30
forum: Server Platforms
---

### Post by bon-the-one on 2023-11-30
Hi All,

I hope someone can please help, as I am tearing my hair our and crying with anger at this one...

I have Ubuntu Server 22.04 on a PI CM4 board (installed on the onboard flash). It's in a Waveshare CM4 carrier board with dual ETH ports. I've one port connected to my internal domestic switch, and the second port connected to the fibre ONT. PPP comes up fine, establishes ppp0. The internal interface is static. DNSMasq works fine, doleing out ip addresses to as requested, correct IP's going to correct MAC's.  DNSMasq is also recieving DHCP requests, resolving them fine and replying to the clients, I have checked that in my 'modem' logs and with dig on the clients themselves. 

HOWEVER...
I cannot get IP forwarding to work. I've tried all I can think of. Tested with UFW up and down, nothing. I've set sysctl IP_forwarding for v4 and v6. I've learned some new stuff about systemD over-riding sysctl and have configured that. On the 'modem' I can ping anything on the net. Client devices though, nada. Traceroute gets me to the CM4 'modem' then nothing. There is nothing in the UFW logs showing me blocks from my internal network. The traffic just vashishes. No www, no pings, no ssh, all just times out. 

I'm wondering if there is a routing issue, because the ppp0 takes a while to establish at boot time. Could it not be configuring the default route for forwarding properly? Should I reinstall rc.local and do some routing resets once the system is properly up? I am at a complete loss, and being autistic this is driving me batty. It used to be so simple to do this!! 

My routing is currently ...

root@modem:~# ip route
default dev ppp0 scope link 
[internal ip range]/24 dev eth0 proto kernel scope link src [modem ip] 
[isp gateway] dev ppp0 proto kernel scope link src [isp static ip for me]

My IP tables in UFW look like this...

root@modem:~# ufw status
Status: active


To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere                  
53/tcp on eth0             ALLOW       Anywhere                  
53/udp on eth0             ALLOW       Anywhere                  
67/udp on eth0             ALLOW       Anywhere                  
67/tcp on eth0             ALLOW       Anywhere                  
Anywhere on eth0           ALLOW       Anywhere                  
22/tcp (v6)                ALLOW       Anywhere (v6)             
53/tcp (v6) on eth0        ALLOW       Anywhere (v6)             
53/udp (v6) on eth0        ALLOW       Anywhere (v6)             
67/udp (v6) on eth0        ALLOW       Anywhere (v6)             
67/tcp (v6) on eth0        ALLOW       Anywhere (v6)             
Anywhere (v6) on eth0      ALLOW       Anywhere (v6)             


Anywhere                   ALLOW OUT   Anywhere on eth0          
Anywhere (v6)              ALLOW OUT   Anywhere (v6) on eth0     


Anywhere on ppp0           ALLOW FWD   Anywhere on eth0          
Anywhere (v6) on ppp0      ALLOW FWD   Anywhere (v6) on eth0

sysctl.conf...

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1


# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
net.ipv6.conf.all.forwarding=1

and in systemD...
root@modem:/etc/systemd/network# cat 80-dhcp.network 
[Match]
Name=enx00e04c68013f


[Network]
DHCP=yes
IPv6AcceptRA=yes
IPForward=ipv4
IPMasquerade=yes

Please someone help. This is driving me crazy, this all used to be so simple, but now I can't see what I've missed and it's upsetting me terribly.

Thanks in advance,

Ian B

---

### Post by darkod on 2023-11-30
I think you are missing to do NAT for traffic going outside. So it doesn't know to come back correctly.

Try this as a simple test (the setting will not stay there after reboots, it is just for a short test):
```
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
```

Does outgoing traffic work after that?

---

### Post by bon-the-one on 2023-12-06
Hi Darko,

Sorry for the tardy reply. (Work has been manic busy, Christmas build up).

Your tip worked, cheers!! Also, my bad, my new 'modem' was on a different IP than it used to be, and was sending out an old gateway IP address in DHCP provisioning, so it was a couple of things. I sorted the IP address, still didn't work. Added your iptables line and it sprang to life, thank you!

Can I just save that line into permanent with iptables -s, or should I add it into a config file somewhere to permanent it?

Cheers,

Bon

---

### Post by darkod on 2023-12-08
Actually since you are using ufw which is only a front for iptables I think you need to search what is the process to add that option through ufw. I don't use ufw so I don't have the commands at hand. If you add it directly in iptables then ufw might overwrite it.

Now that you know you need to add the postrouting masquerade option it shouldn't be difficult to find the process for ufw.

---


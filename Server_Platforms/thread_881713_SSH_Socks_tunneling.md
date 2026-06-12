---
title: "SSH Socks tunneling"
date: 2008-08-06
forum: Server Platforms
---

### Post by hampycalc on 2008-08-06
Hi everyone,
I have a server running 7.10 with 6 assigned IPs. I can connect and tunnel via SSH, but it will only tunnel through the default interface ETH0 which is bound to one IP. I want to find a way to tunnel through the other IP addresses which are bound to other network interfaces (ETH0:1, ETH 0:2, etc...), possibly by using different user names so I have access to all 6. Can anyone help?

---

### Post by moonpup on 2008-08-06
Have you tried configuring the ListenAddress directive in the sshd config file?


ListenAddress specifies the local addresses sshd should listen on.  The following forms may be used:

                   ListenAddress host|IPv4_addr |IPv6_addr
                   ListenAddress host|IPv4_addr : port
                   ListenAddress [host|IPv6_addr]: port

             If port is not specified, sshd will listen on the address and all prior Port options specified. The default is to listen on all local addresses.  Multiple ListenAddress options are permitted. Additionally, any Port options must precede this option for non port qualified addresses.

---

### Post by hampycalc on 2008-08-06
Thanks, but have already tried this. This just sets up the tunnel itself and does not determine which interface the server accesses the WAN on.
Sorry, re-reading my original post I can see I haven't explained myself properly. It doesn't matter which IP I setup the tunnel on, I want to be able to access the web using one of 6 IPs assigned to my server.

---

### Post by hampycalc on 2008-08-07
Any ideas?

---

### Post by hampycalc on 2008-08-07
I've had another thought but am useless with IP tables.
Would it be possible to change the outgoing IP (outgoing interface) used as standard by different users (UIDs) by using IPTABLES?

---

### Post by hampycalc on 2008-08-07
In fact, I don't even really have to use SSH tunneling, I could use a SOCKS proxy server, but none of them will do what I need them to do.

---

### Post by StickyStyle on 2008-08-07
I assume that all these subinterfaces are on the same subnet, and eth0 is not plugged into a trunked port?
Look at the output of '$netstat -r' and you will see your default gateway interface is eth0, packets are just going to go out that interface because that's how the routing works.

You may be able to do what you want with source based routing and iptables, but I really don't know enough about your setup to tell you yes or no.  [http://www.wlug.org.nz/SourceBasedRouting](http://www.wlug.org.nz/SourceBasedRouting)

---

### Post by hampycalc on 2008-08-07
Yes they are on the same subnet. I have 6 IPs on eth0, eth0:0, eth0:1, etc, all on the same hardware address.
I have been trying to work with iptables, but get an error with what I am trying to do:

iptables -A OUTPUT -t nat -mowner --uid-owner 1000 -j SNAT --to xxx.xxx.xxx.xxx  
iptables: No chain/target/match by that name
The xxx.xxx.xxx.xxx is one of six public IPs.

My thoughts were to change the source address of all packets coming from a certain uid. I could then assign a different external IP to each user. What is wrong with the iptables entry I have used?

I should probably also state that I am not behind a router so no funny NAT is going on.

---

### Post by hampycalc on 2008-08-07
I have found that the following iptables entry does almost exactly what I want:

iptables -t nat -A POSTROUTING -j SNAT --to xxx.xxx.xxx.xxx (the public IP I want to use)

If I then connect to the server via SSH and tunnel my traffic through it, my public IP is registered as xxx.xxx.xxx.xxx

However, you cannot use the '-mowner --uid-owner' with POSTROUTING, only OUTPUT, and you cannot use SNAT with OUTPUT. Also, as soon as I use '-m owner --uid-owner root', I get the "iptables: No chain/target/match by that name" error.

ARGH!!

I am using iptables v1.3.6 by the way

---

### Post by Mr_Toph on 2008-10-18
Hi hampycalc,
I'm not sure your using them in the right order. You need to load the owner module, as well as define the type or rule as NAT right off the bat. Try the below.

```
iptables -m owner -t nat -A POSTROUTING --uid-owner <uid-here> -j SNAT --to <snat-ip-here>
```

Thanks,
/toph

---


---
title: "Firestarter w/ port forwarding (maybe)"
date: 2007-08-27
forum: Server Platforms
---

### Post by KevinM1 on 2007-08-27
I'm having difficulty getting Firestarter to work.  I believe my boss used some port forwarding voodoo when he set up this box, so, as far as I know, the setup is basically:

internet <-------> this Ubuntu box <-------> local network

Every time I try starting Firestarter, I get the following error:
[http://www.rextrader.com/firestarter.png](http://www.rextrader.com/firestarter.png)

Any idea on how I can get it to work?

Thanks.

---

### Post by koenn on 2007-08-27
apparently eth0, connecting to the internet, is not working. 

try
```
sudo -i
ifconfig eth0 down
ifconfig eth0 up
ifconfig
cat /etc/network/interfaces
exit
```
in a terminal, and post the output

---

### Post by KevinM1 on 2007-08-28
> **koenn said:**
> apparently eth0, connecting to the internet, is not working. 

try
```
sudo -i
ifconfig eth0 down
ifconfig eth0 up
ifconfig
cat /etc/network/interfaces
exit
```
in a terminal, and post the output

No output from either ifconfig eth0 down or ifconfig eth0 up.

Output from plain old ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:18:F3:85:BF:DA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:60:67:70:A6:BD  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::260:67ff:fe70:a6bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27285967 (26.0 MiB)  TX bytes:11632920 (11.0 MiB)
          Interrupt:19 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63424 (61.9 KiB)  TX bytes:63424 (61.9 KiB)
```

Output from interfaces:
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.up.rules
post-down iptables-save > /etc/iptables.up.rules
address 65.175.139.109
netmask 255.255.255.0
gateway 65.175.139.1


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




auto eth0

iface eth1 inet dhcp
address 192.168.1.2
netmask 255.255.255.0
gateway 65.175.139.1

auto eth1
```

---

### Post by koenn on 2007-08-28
here's your problem: eth0 doen't have an ip address. compare eth0 and eth1 in the output of ifconfig and you'll see.

'interfaces' says eth0 uses dhcp, but still you put an ip address there. eth0 is also configured twice in interfaces. That's not right, it's either dhcp, or a static address set in interfaces. 
Do you know which of these alternatives you need ? 

If it is dhcp, it's apparently not working. Possible causes : maybe your pre-up iprules interfare with the dhcp exchange, or /etc/network/interfaces is too much of a mess for the system to work it out and do something usefull, like configuring eth0. 


Let us know how eth0 should be configured (my guess: dhcp from your internet provider) and we'll have another look.

---

### Post by KevinM1 on 2007-08-29
> **koenn said:**
> here's your problem: eth0 doen't have an ip address. compare eth0 and eth1 in the output of ifconfig and you'll see.

'interfaces' says eth0 uses dhcp, but still you put an ip address there. eth0 is also configured twice in interfaces. That's not right, it's either dhcp, or a static address set in interfaces. 
Do you know which of these alternatives you need ? 

If it is dhcp, it's apparently not working. Possible causes : maybe your pre-up iprules interfare with the dhcp exchange, or /etc/network/interfaces is too much of a mess for the system to work it out and do something usefull, like configuring eth0. 


Let us know how eth0 should be configured (my guess: dhcp from your internet provider) and we'll have another look.

Unfortunately, I'm not the person who originally set up this internet connection.  I know that we did purchase a static IP address from our ISP for the web hosting we're going to do on this machine, but I'm not sure of the details.  I know there's some port forwarding going on somewhere, as I've been told that this machine is the linkage between our LAN and the web, but that's all I know.  I'll try to get the details to you ASAP.

---

### Post by KevinM1 on 2007-08-29
It's strange...I've tried setting, via Gnome's Network window, both eth1 and eth0 as the static address (seperately -- so eth1 as the static address, eth0 as dhcp and vice versa), but everytime I do, I can no longer access the internet.  **But**, whenever I do that, regardless of the combination, Firestarter starts working.  You mentioned my iptables, but it now looks like my old rules have been erased!
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

EDIT: update on how my work's network is laid out:

internet <--static ip address-->router<----dhcp---->Ubuntu box<----dhcp---->LAN

---

### Post by KevinM1 on 2007-08-29
In my infinite wisdom, I attempted to do something similar to eth1 as you had me do to eth0, as I wanted to see if anything would change.  So, I did the following:

```

sudo -i
ifconfig eth0 down
ifconfig eth1 down
ifconfig eth0 up
ifconfig eth1 up
ifconfig
cat /etc/networking/interfaces
exit

```

I can't display the output from that as I'm currently at home, but this basically broke the internet connection.  I could ping out to, for example, Google, but I couldn't access any websites through the browser.  So, other than confirming that I'm an idiot, is there anything I e-mail my boss to try to restore the old, somewhat working, settings?

---

### Post by koenn on 2007-08-29
well, you show initiative and willingness to investigate - not too shabby for an 'idiot'.

What you need is have your interfaces cleaned up, some DROP, ACCEPT and possibly MASQUERADE  iptables rules  put in place, and ip-routing activated in the kernel (the latter is probably already done). It's not hard, but it has to be done right, and right now it's late, I'm tired, and I've been messing with config files all day so I'm not really in a mood to do some more. 

I've seen this type of touble being solved on these forums, so there are quite a few people around here who can help you out. If none show up, I'll come have an other look tomorrow.

---

### Post by KevinM1 on 2007-08-29
> **koenn said:**
> well, you show initiative and willingness to investigate - not too shabby for an 'idiot'.

What you need is have your interfaces cleaned up, some DROP, ACCEPT and possibly MASQUERADE  iptables rules  put in place, and ip-routing activated in the kernel (the latter is probably already done). It's not hard, but it has to be done right, and right now it's late, I'm tired, and I've been messing with config files all day so I'm not really in a mood to do some more. 

I've seen this type of touble being solved on these forums, so there are quite a few people around here who can help you out. If none show up, I'll come have an other look tomorrow.

Great, thanks.  Actually, I just got a call from my boss: he was able to restore the internet connection **and** start Firestarter (at least, temporarily...I'm in "I'll believe it when I see it for myself" mode right now).  From what he said, I guess he basically just turned off eth0.  I'll find out more tomorrow.  Unfortunately, I can't access the temporary website that we're hosting.  So, would my tinkering have any effect on Apache2?

Thanks again! :)

---

### Post by KevinM1 on 2007-08-30
Good news!  My internet connection is working, as is Firestarter!  Now the question is what should I allow for connections, and to whom?  Obviously, I need incoming HTTP connections, and I'd like an incoming SSH connection, but what else should I allow, with an eye towards security?

---

### Post by koenn on 2007-08-30
good news indeed. 
have a look at (in a terminal)
```
ifconfig
cat /etc/network/interfaces
cat /proc/sys/net/ipv4/ip_forward 

```
again, so you know what they're supposed to look like, for future reference

if cat /proc/sys/net/ipv4/ip_forward returns 1, the system is most likely set up to be a router. That would be interesting to know. In fact,  the way you drew the network layout suggests that the ubuntu box is a router/firewall for the LAN hosts. Is that the way it's supposed to be ? 
Do the have access to the web now ?  
This also matters re the firewall rules. 

On the other hand, if you're boss fixed things by turning OFF eth0, none of this makes sense. I thought eth0 being off was (the biggest part of) the problem. 

so, basically, the ubuntu system should allow access to its web server and ssh daemon. From the LAN, from the internet, or both ?

You probably also need to allow DNS and dhcp - I'll assume your router/internet provider handle's these unless you tell me otherwise. 

you can have a look at this thread, it turned out a small iptables tutorial : [http://ubuntuforums.org/showthread.php?t=533425](http://ubuntuforums.org/showthread.php?t=533425)

---

### Post by KevinM1 on 2007-08-30
> **koenn said:**
> good news indeed. 
have a look at (in a terminal)
```
ifconfig
cat /etc/network/interfaces
cat /proc/sys/net/ipv4/ip_forward 

```
again, so you know what they're supposed to look like, for future reference

if cat /proc/sys/net/ipv4/ip_forward returns 1, the system is most likely set up to be a router. That would be interesting to know. In fact,  the way you drew the network layout suggests that the ubuntu box is a router/firewall for the LAN hosts. Is that the way it's supposed to be ? 
Do the have access to the web now ?  
This also matters re the firewall rules. 

On the other hand, if you're boss fixed things by turning OFF eth0, none of this makes sense. I thought eth0 being off was (the biggest part of) the problem. 

so, basically, the ubuntu system should allow access to its web server and ssh daemon. From the LAN, from the internet, or both ?

You probably also need to allow DNS and dhcp - I'll assume your router/internet provider handle's these unless you tell me otherwise. 

you can have a look at this thread, it turned out a small iptables tutorial : [http://ubuntuforums.org/showthread.php?t=533425](http://ubuntuforums.org/showthread.php?t=533425)

Actually, ip_forwarding returns 0.  Your guess is as good as mine, as I was told that the Ubuntu box was a sort of de facto router for our system. :shrug:

The box should definitely allow incoming HTTP and SSH connections.  I'm thinking it should allow LAN DHCP connections too, at least, just to be safe for the time being.

I do have internet access.  I'm actually writing to you on the box.

So far, I've opened up a lot of ports right now to everyone, via Firestarter.  In part, because I'm not sure what to put for the IP of our network given it's vague, confusing design.  To be specific, I'm not sure if I should put in the static IP address, which is what the router uses, or something else.

---

### Post by koenn on 2007-08-30
:shrug: indeed. 

gues #1: the "allow" rules you're making are useless because the default policy if your firewall is ACCEPT, meaning that everything is allowed, unless a rule explicetily blocks it. 

guess #2: it's possibke that the ubuntu-system is running a proxy server that allows the LAN hosts to browse the web, without any forwarding/routing/ ...

could you confirm any of this (by testing it/ checking proxy settings on the hosts / ... )

and you're right : networking gets easier if the important parts (servers, routers, ...) hace fixed IP addresses i.s.o. dhcp

---

### Post by KevinM1 on 2007-08-30
> **koenn said:**
> :shrug: indeed. 

gues #1: the "allow" rules you're making are useless because the default policy if your firewall is ACCEPT, meaning that everything is allowed, unless a rule explicetily blocks it. 

From what I could see, it looked like all of the ports were actually closed when I started Firestarter, as the internet and e-mail only worked after I allowed those ports while it was running.  I had to whitelist the specific ports.

> guess #2: it's possibke that the ubuntu-system is running a proxy server that allows the LAN hosts to browse the web, without any forwarding/routing/ ...

could you confirm any of this (by testing it/ checking proxy settings on the hosts / ... )

and you're right : networking gets easier if the important parts (servers, routers, ...) hace fixed IP addresses i.s.o. dhcp

I don't think that the Ubuntu box is running a proxy server as, to my knowledge, I'm the only one who's touched the system, except for the initial OS installation and last night's fix.

The eth0 thing is still driving me crazy though.  From what I saw at work, it looked to be connected, verifying what you said a few messages back.  But my boss mentioned something about turning it off during the phone conversation we had last night.  Unfortunately, my boss knows a lot less than he claims regarding this stuff, so I'm not really sure what he did or how he did it.

Regarding the checks of the proxy settings, where should I look for that?  Like I said, I don't think it's a proxy issue, but at this point anything is possible.  Also, if I wanted to limit DHCP traffic to just the office LAN, what would I put for an IP value or hostname?  There's some wireless routing going on (which looks to be *seperate* from the router that has the static IP address...yeah, I'm annoyed with this entire setup, too), so I can see the IP addresses of the networked machines through its interface.  Would I just use those IP addresses?

---

### Post by koenn on 2007-08-30
would you mind posting 'ifconfig" and "/etc/network/interfaces" again, just to make sure i have everything straight ?


re your firewall, I was going by tour earlier post that says "all rules disappeared" and shouw ACCEPT policies on all chains. 

The usual way to do this is block everything, then allow what's needed. Block everyting bu executing (as root)
```
for CHN in INPUT OUTPUT FORWARD ; do
    iptables -P $CHN DROP ;
done

```
this sets a "drop" policy on all chains. You'll have to put this in a startup script, or use a tool (iptables-save, Firestarter, ... ) for it to be set automatically after reboots


Then, for your dhcp:
somwhere in the dhcpd config file (/etc/dhcp3d/dhcpd.conf probably), you can indicate what interface the dhcp daemon should listen / send on. set that to (ip adress of ?) eth1 (check the file's comments for the right way to do it). This makes sure that yout only serving dhcp to your LAN. 
Then, allow it in your firewall with
```
iptables -A INPUT -i eth1 -p udp --sport 68 --dport 67 -j ACCEPT
iptables -A OUTPUT  -o eth1 -p udp --sport 67 --dport 68 -j ACCEPT
```
you can not use addresses here, because the dhcp uses a broadcast address (lots of the dhcp dialog happens before the client has an IP address). 

But you could use addresses to accept only ssh coming from hosts on your lan. combined with an input-interface, it's even more secure
```
iptables -A INPUT -i eth1 -s 192.168.1.0/24  -p tcp --sport 22 -j ACCEPT

```

All of the above allows packets coming to your server ( thus : "INPUT"). You also need to allow to corresponding replies from the server to the clients. This, is usually handled with a --state ESTABLISHED,RELATED statement. See that other post I linked to. 

re the checks for the proxy : just look in the settings (options/preferences) of your LAN hosts's web browsers to see if the use a proxy, and what name/IP adress it has. 

Besides all that, I recommend your boss be fired.

---

### Post by KevinM1 on 2007-08-31
> **koenn said:**
> would you mind posting 'ifconfig" and "/etc/network/interfaces" again, just to make sure i have everything straight ?

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:18:F3:85:BF:DA  
          inet6 addr: fe80::218:f3ff:fe85:bfda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2408415 (2.2 MiB)  TX bytes:468 (468.0 b)
          Interrupt:23 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:60:67:70:A6:BD  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::260:67ff:fe70:a6bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:117415 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24101236 (22.9 MiB)  TX bytes:3292730 (3.1 MiB)
          Interrupt:19 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:956634 (934.2 KiB)  TX bytes:956634 (934.2 KiB)

```

interfaces:
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.up.rules
post-down iptables-save > /etc/iptables.up.rules
address 65.175.139.109
netmask 255.255.255.0
gateway 65.175.139.1


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






iface eth1 inet dhcp
address 192.168.1.5
netmask 255.255.255.0
gateway 65.175.139.1

auto eth1



auto eth0

```


> re your firewall, I was going by tour earlier post that says "all rules disappeared" and shouw ACCEPT policies on all chains. 

The usual way to do this is block everything, then allow what's needed. Block everyting bu executing (as root)
```
for CHN in INPUT OUTPUT FORWARD ; do
    iptables -P $CHN DROP ;
done

```
this sets a "drop" policy on all chains. You'll have to put this in a startup script, or use a tool (iptables-save, Firestarter, ... ) for it to be set automatically after reboots

So, that code block would just be executed at the terminal prompt?  Also, does Firestarter automatically save iptables settings?  I've looked for some way to save policy/iptables rules, but I haven't found anything in its interface.

> Then, for your dhcp:
somwhere in the dhcpd config file (/etc/dhcp3d/dhcpd.conf probably), you can indicate what interface the dhcp daemon should listen / send on. set that to (ip adress of ?) eth1 (check the file's comments for the right way to do it). This makes sure that yout only serving dhcp to your LAN. 
Then, allow it in your firewall with
```
iptables -A INPUT -i eth1 -p udp --sport 68 --dport 67 -j ACCEPT
iptables -A OUTPUT  -o eth1 -p udp --sport 67 --dport 68 -j ACCEPT
```
you can not use addresses here, because the dhcp uses a broadcast address (lots of the dhcp dialog happens before the client has an IP address).

I think that may have happened automatically with my tinkering with Firestarter.  I told it to open up the dhcp ports for both input and output.

> But you could use addresses to accept only ssh coming from hosts on your lan. combined with an input-interface, it's even more secure
```
iptables -A INPUT -i eth1 -s 192.168.1.0/24  -p tcp --sport 22 -j ACCEPT

```

Unfortunately, I'm not going to using SSH on our LAN.  I'm going to (if I can get the daemon to work) connect into the server from my home PC.  Since I was deemed to be the server guy, my old work PC has been turned into a mere antivirus/anti-spyware scanner, where my co-workers connect our clients' troubled hard disks for scanning.

> All of the above allows packets coming to your server ( thus : "INPUT"). You also need to allow to corresponding replies from the server to the clients. This, is usually handled with a --state ESTABLISHED,RELATED statement. See that other post I linked to.

Will do.

> re the checks for the proxy : just look in the settings (options/preferences) of your LAN hosts's web browsers to see if the use a proxy, and what name/IP adress it has.

I'm a bit confused here.  Would I just look at the browser proxy settings of any other networked computer in the office?  Or something else?

> Besides all that, I recommend your boss be fired.

Hehe, yeah.  He's a nice guy, but a bit over his head at times.  Unfortunately, he's the business owner, so I'm a bit stuck there.  We're a small 3-man opperation: the boss, myself, and the 18 year old.

I just thought of something: I can show you my current iptables setup.  I don't really know what I'm looking at, but it probably says that everything is more or less open (it's long):
```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  cust-dns-01.metrocast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cust-dns-01.metrocast.net  anywhere            
ACCEPT     tcp  --  cust-dns-02.metrocast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  cust-dns-02.metrocast.net  anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply limit: avg 1/sec burst 5 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:33434 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp host-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp timestamp-request 
ACCEPT     icmp --  anywhere             anywhere            icmp timestamp-reply 
ACCEPT     icmp --  anywhere             anywhere            icmp address-mask-request 
ACCEPT     icmp --  anywhere             anywhere            icmp address-mask-reply 
ACCEPT     icmp --  anywhere             anywhere            icmp redirect limit: avg 2/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench limit: avg 2/sec burst 5 
LSI        icmp --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply limit: avg 1/sec burst 5 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:33434 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp host-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp address-mask-request 
ACCEPT     icmp --  anywhere             anywhere            icmp address-mask-reply 
ACCEPT     icmp --  anywhere             anywhere            icmp redirect limit: avg 2/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench limit: avg 2/sec burst 5 
LSI        icmp --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.5          cust-dns-01.metrocast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.5          cust-dns-01.metrocast.net udp dpt:domain 
ACCEPT     tcp  --  192.168.1.5          cust-dns-02.metrocast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.1.5          cust-dns-02.metrocast.net udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:bootps:bootpc 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:bootps:bootpc 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:bootps:bootpc 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:bootps:bootpc 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:netbios-ns:netbios-ssn 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:netbios-ns:netbios-ssn 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:microsoft-ds 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:pop3 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (4 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       0    --  anywhere             anywhere            

Chain LSO (1 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:bootps:bootpc 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:bootps:bootpc 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:25 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:pop3 
LSO        0    --  anywhere             anywhere   
```

For reference, Metrocast is our ISP.

Thanks again! :D

---


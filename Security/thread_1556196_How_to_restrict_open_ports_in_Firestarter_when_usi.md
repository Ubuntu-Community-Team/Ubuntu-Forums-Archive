---
title: "How to restrict open ports in Firestarter when using torrents?"
date: 2010-08-19
forum: Security
---

### Post by zozza on 2010-08-19
Hello,

I am trying to configure Bittorando and iptables using Firestarter.  I have got it working but am concerned about security holes.

Let me explain.

AIUI, the Bittornado program contacts the "tracker" on various ports which (from the previously blocked connections in Firestarter) ranged from 4664 to 65532.  Therefore, currently I have set this range to be open to allow downloads of the torrent. 

However, this seems, IMHO, to devalue to point of having a restrictive exit policy for Firestarter since now virtually all ports are open.  I can see nothing on the Bittornado client to restrict the outgoing ports although the "listening" (incoming) ports can be restricted.  

I would prefer to have my system locked-down so that the minimal number of ports are open to initiate external connections so is there any way to achieve this with Bittornado?

Thanks.

---

### Post by CharlesA on 2010-08-19
Use a different torrent client.

There really isn't a huge need to block out-going connections, especually if you are doing torrents. You want to block incoming ones, since those are the ones that are normally initiated from the internet or local network.

---

### Post by Ve5ahchoo8ah on 2010-08-19
I use same programs and also I'm connected to the Internet with adsl and through my my adsl modem and a hub (to share Internet in the house)
When I use torrents my firewall alerts me that there is a hit from 192.168.1.1 (which is my adsl modem) and cannot download torrent
finally I grant access from 192.168.1.1 and 192.168.1.2 in my firewall setting to my computer
is this secure?

---

### Post by CharlesA on 2010-08-19
Do you have a rule that allows established and related connections?

If not, then that's why you are getting those warnings.

---

### Post by Ve5ahchoo8ah on 2010-08-19
I don't know if i have the rule which you said but a attached a picture of my firewall rule setting. i hope it helps

---

### Post by CharlesA on 2010-08-19
Can you post the output of this command please, it will be easier to check the rules:

```
sudo iptables -L
```

---

### Post by Ve5ahchoo8ah on 2010-08-19
thanks
sudo iptables -L gives me this:

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  google-public-dns-a.google.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  google-public-dns-a.google.com  anywhere            
ACCEPT     tcp  --  google-public-dns-b.google.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  google-public-dns-b.google.com  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             localhost           
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.2          google-public-dns-a.google.com tcp dpt:domain 
ACCEPT     udp  --  192.168.1.2          google-public-dns-a.google.com udp dpt:domain 
ACCEPT     tcp  --  192.168.1.2          google-public-dns-b.google.com tcp dpt:domain 
ACCEPT     udp  --  192.168.1.2          google-public-dns-b.google.com udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             localhost           
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.1.1          anywhere            
ACCEPT     all  --  192.168.1.2          anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6881:6889 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSO        tcp  --  anywhere             anywhere            tcp dpt:telnet 
LSO        udp  --  anywhere             anywhere            udp dpt:23 
ACCEPT     all  --  anywhere             anywhere            

```I have set my dns to 8.8.8.8 (google) so somethings are related to that

---

### Post by CharlesA on 2010-08-19
You have the established/related rule in the output chain, not input. Add it there and see what happens.

Should look like this:

```
ACCEPT     all  --  anywhere             anywhere            state ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            state RELATED
```

---

### Post by Ve5ahchoo8ah on 2010-08-19
Sorry I don't know what should I do! :(
could you please give me the commands? thanks a lot

---

### Post by CharlesA on 2010-08-19
```
sudo iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
sudo iptables -A INPUT -m state --state RELATED -j ACCEPT

```

---

### Post by Ve5ahchoo8ah on 2010-08-19
I did as you said and now "sudo iptables -L" gives me this:

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  google-public-dns-a.google.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  google-public-dns-a.google.com  anywhere            
ACCEPT     tcp  --  google-public-dns-b.google.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  google-public-dns-b.google.com  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             localhost           
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.2          google-public-dns-a.google.com tcp dpt:domain 
ACCEPT     udp  --  192.168.1.2          google-public-dns-a.google.com udp dpt:domain 
ACCEPT     tcp  --  192.168.1.2          google-public-dns-b.google.com tcp dpt:domain 
ACCEPT     udp  --  192.168.1.2          google-public-dns-b.google.com udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             localhost           
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.1.1          anywhere            
ACCEPT     all  --  192.168.1.2          anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6881:6889 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSO        tcp  --  anywhere             anywhere            tcp dpt:telnet 
LSO        udp  --  anywhere             anywhere            udp dpt:23 
ACCEPT     all  --  anywhere             anywhere            

```

---

### Post by CharlesA on 2010-08-19
I didn't see where it added that. It should be listed in the INPUT chain.

It could be that firestarter is messing with things. I wouldn't use it since it's out of development and UFW/GUFW are better alternatives.

---

### Post by bodhi.zazen on 2010-08-19
Torrents and firewalls are a bit complex because they use a wide range of ports for a variety of reasons.

IMO firewalls play little to no role in securing torrents, the whole point is you are sharing data with unknown computers.

It is difficult to have your cake and eat it too, either you are going to share your connections or not. Unless you know the clients you are connecting to it makes little to no sense to firewall the sharing process.

If you do not want to share, do not use torrents.

If you must you will need to research your client. You will then allow traffic to a port or range of ports which you set.

You will need to select a client, decide on a port or range of ports you wish to allow, and configure your client to use those port(s). The details vary by client.

The "basic" rule for your firewall is :

```
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT
```

where "6881" can be a single or a range of ports. You can allow all ports above 1024 if you wish or restrict to a single or smaller range of ports, your choice.

There are some variations on the theme, but, you are going to allow traffic so what is there to "firewall" ? What is your goal in firewalling a torrent client ?

---

### Post by Ve5ahchoo8ah on 2010-08-20
Thanks a lot everyone
I changed my firewall to GUFW
the only problem with this program is that it doesn't show which programs are connected to the Internet.
anyway thanks you all you're so kind

---

### Post by JBAlaska on 2010-08-20
Try using Deluge as a BT client and enabling just ONE tcp port (example) 35000

Enable the blocklist plugin and try this for a blocklist url:
```
http://list.iblocklist.com/?list=bt_level1
```

Thats about as safe as torrenting gets without using a seedbox.

---

### Post by Ve5ahchoo8ah on 2010-08-20
Sorry but I used deluge and there was problems!
[http://ubuntuforums.org/showthread.php?t=913376](http://ubuntuforums.org/showthread.php?t=913376)

---


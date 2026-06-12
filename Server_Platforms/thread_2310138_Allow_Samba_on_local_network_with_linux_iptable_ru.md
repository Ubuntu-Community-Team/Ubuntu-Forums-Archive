---
title: "Allow Samba on local network with linux iptable rules firewall csf / lfd"
date: 2016-01-16
forum: Server Platforms
---

### Post by jonah1980 on 2016-01-16
Hi any help would be really appreciated for the correct IPTABLE rules set to allow samba on my local network. Currently my firewall is blocking it...

I've looked around and I realise you can lookup the right ports with netstat -tulpn | egrep "samba|smbd|nmbd|winbind"

but I've no idea the correct syntax and the correct rules needed to do this right and still keep the firewall safely working etc.

Can anyone please post the lines I would need to add to achieve this on my ubuntu server?

Thanks again for any help!

---

### Post by nerdtron on 2016-01-17
If you use ubuntu, better use the ufw utility instead. Samba runs on TCP ports 139 and 445 and UDP ports 137 and 138

So I guess the simplest command to allow those:
```
 sudo ufw allow 139
sudo ufw allow 445
sudo ufw allow 137
sudo ufw allow 138

```

---

### Post by jonah1980 on 2016-01-17
hi thanks for the help. Unfortunately this doesn't seem to work for me as I'm using CSF and LFD. I would use ufw but I also have webmin installed which offers a csf module. I'd rather use that as I'm used to the same on the other cPanel servers I have.

Does anyone know how I can get local-only samba to work with CSF?

Thanks again for any help.

---

### Post by darkod on 2016-01-17
Pardon my ignorance, but what's CSF and LFD? Type of firewall?

Since you found out how to check relevant ports, you only need to open those ports for inbound traffic and that's it. Doesn't matter much what the firewall is if you do that right.

For direct iptables, you would do something like:
```
sudo iptables -A INPUT -p tcp --dport 139 -j ACCEPT
```

Do that for all needed tcp and udp ports and test if it worked. However, if you are using some firewall "frontend" that uses iptables at the end, such commands directly with iptables might not be supported.

Those rules will be temporary unless you make them permanent, but only for testing it will do. After that, there are variations like if you want to allow it only for some source IPs/networks you should use the '-s x.x.x.x/xx' option added to the above command. That will allow the traffic only from those IPs and networks. But if you need worldwide access, you can't really limit by IP.

PS. Webmin??? Try to learn what you need and not to use webmin. There is a reason it is not a recommended and supported tool.

---

### Post by jonah1980 on 2016-01-17
Hi thanks for the reply.

CSF is just an iptables firewall for linux servers: [http://configserver.com/cp/csf.html]("http://configserver.com/cp/csf.html")

Doing netstat -tulpn | egrep "samba|smbd|nmbd|winbind"

gives me: 

```
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      23102/smbd      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      23102/smbd      
tcp6       0      0 :::139                  :::*                    LISTEN      23102/smbd      
tcp6       0      0 :::445                  :::*                    LISTEN      23102/smbd      
udp        0      0 192.168.122.255:137     0.0.0.0:*                           1267/nmbd       
udp        0      0 192.168.122.1:137       0.0.0.0:*                           1267/nmbd       
udp        0      0 192.168.0.255:137       0.0.0.0:*                           1267/nmbd       
udp        0      0 192.168.0.100:137       0.0.0.0:*                           1267/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1267/nmbd       
udp        0      0 192.168.122.255:138     0.0.0.0:*                           1267/nmbd       
udp        0      0 192.168.122.1:138       0.0.0.0:*                           1267/nmbd       
udp        0      0 192.168.0.255:138       0.0.0.0:*                           1267/nmbd       
udp        0      0 192.168.0.100:138       0.0.0.0:*                           1267/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1267/nmbd
```

so that's my ports and such. But I'm not sure how I actually add them correctly in the right syntax and format to the iptables so that my local network has access to samba but no one else does?

Thanks again for any help. I can paste my iptables as they are currently if that helps?

---

### Post by darkod on 2016-01-17
I am confused why do you need a firewall on this server at all. The server is in the private network 192.168.x.x right? This network is not routeable for anyone outside, no one can reach it from the internet. Usually local networks already have a firewall on the gateway to the internet. You don't need more than that...

I'm not familiar with that firewall, so you will have to do that part of the investigation by yourself. They probably have FAQ or support page with what you need.

If you want the server open to the whole 192.168.122.x network you need to allow ports tcp/139, tcp/445, udp/137 and udp/138 for source 192.168.122.0/24. That covers the whole network.

But again, if the machine is already behind a firewall/gateway, don't use any firewall on it and save yourself the trouble...

---

### Post by Doug S on 2016-01-17
> **darkod said:**
> If you want the server open to the whole 192.168.122.x network you need to allow ports tcp/139, tcp/445, udp/137 and udp/138 for source 192.168.122.0/24. That covers the whole network.Does it? I see also 192.168.0.100 so we would need to know more about the local area network to know for sure. Maybe its 192.168.0.0/16 or somehow two subnets, 192.168.122.0/24 and 192.168.0.0/24 or?

I agree, why bother at all, if the computer in already internal.

> **nerdtron said:**
> If you use ubuntu, better use the ufw utility instead. That is an opinion. My opinion is that iptables is better.

---

### Post by jonah1980 on 2016-01-18
Hi thanks for the reply.

The server is actually mainly for hosting/storage externally. The samba part is just handy for my internal network as a way to access parts of it and stream content to other devices.

So I would like to keep the firewall running for outside, but just have the samba shares for internal use and only have them blocked to the outside world if anyone did try to gain access. Currently the firewall just blocks samba completely!

---

### Post by darkod on 2016-01-18
FYI, if you want samba available only to one of the private networks, you can also attach it to only one of the interfaces. That way the other private network will not be able to use/open it.

But if you insist doing it with a firewall inside a private network, you know what to do. Allow the network you want to (the 192.168.0.x or 192.168.122.x) for inbound traffic on the four ports mentioned above, and that's it... Basically you allow inbound traffic to those ports from specific source network.

Depends how the CFS interface is done, it should not be difficult.

---

### Post by jonah1980 on 2016-01-20
I've tried adding the below to my /etc/csf/csf.allow file and restarted but for some reason it is still blocked:


```
# TCP connections inbound to port 139 and 445 from local network (192.168.0.0/24)
tcp|in|d=139|s=192.168.0.0/24
tcp|in|d=445|s=192.168.0.0/24

# UDP connections inbound to port 137 and 138 from local network (192.168.0.0/24)
udp|in|d=137|s=192.168.0.0/24
udp|in|d=138|s=192.168.0.0/24
```

The above seems to be the correct syntax I can find for CSF... Here is what it says at the top of the file:

> ###############################################################################
# Copyright 2006-2016, Way to the Web Limited
# URL: [http://www.configserver.com](http://www.configserver.com)
# Email: [email]sales@waytotheweb.com[/email]
###############################################################################
# The following IP addresses will be allowed through iptables.
# One IP address per line.
# CIDR addressing allowed with a quaded IP (e.g. 192.168.254.0/24).
# Only list IP addresses, not domain names (they will be ignored)
#
# Advanced port+ip filtering allowed with the following format
# tcp/udp|in/out|s/d=port|s/d=ip
# See readme.txt for more information
#
# Note: IP addressess listed in this file will NOT be ignored by lfd, so they
# can still be blocked. If you do not want lfd to block an IP address you must
# add it to csf.ignore

Thanks again for any help.

---

### Post by jonah1980 on 2016-01-21
Hi I still haven't gotten anywhere with this, even after posting on the csf forum.

I've now found the syslog and it's giving this error when I try to connect to samba:

> Jan 21 11:56:46 svr kernel: [63782.300001] Firewall: *UDP_OUT Blocked* IN= OUT=p2p1 SRC=192.168.0.100 DST=192.168.0.16 LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=24138 DF PROTO=UDP SPT=137 DPT=40757 LEN=70 UID=0 GID=0


So this made me think I need to add udp_out rules to my allow file which I did as follows:

> # TCP connections inbound to port 139 and 445 from local network (192.168.0.0/24)
tcp|in|d=139|s=192.168.0.0/24
tcp|in|d=445|s=192.168.0.0/24

# UDP connections inbound to port 137 and 138 from local network (192.168.0.0/24)
udp|in|d=137|s=192.168.0.0/24
udp|in|d=138|s=192.168.0.0/24

# UDP connections outbound to port 137 to local network (192.168.0.0/24)
udp|out|d=137|s=192.168.0.0/24


but I still get the same udp_out block error after restarting the firewall...

---

### Post by CharlesA on 2016-01-21
I just checked what my line looks like for csf and it looks like mine is set up like this for OpenVPN:

```
tcp|in|d=22|s=10.8.0.0/24
```

Are you reloading csf after changing the config?

```
sudo csf -r
```

Are other ports being opened if you add firewall rules?

---

### Post by jonah1980 on 2016-01-21
Thanks Charles - now I'm getting somewhere!

The line I just added:

>  udp|out|d=137|s=192.168.0.0/24 

turns out was wrong and should be:

> udp|out|s=137|s=192.168.0.0/24

so I was putting the port as destination not the source. That's all it was!!

I'm going to try removing the other entries I made and see if I'm still blocked and then just re-add what is necessary again trying d/s combos until I've got the correct rule set.

Thanks everyone for the help!

---

### Post by darkod on 2016-01-21
That's the problem when blocking outgoing traffic with your firewall too. :) You have to remember to allow it also.

Usually all threats are outside and I tend to leave the OUTPUT policy at ACCEPT. However, if blocking outgoing too never forget to adjust rules...

---

### Post by jonah1980 on 2016-01-21
Thanks Darko, could you advise if this ruleset now looks correct of if I should tweak it or remove any unneeded lines? I just tried again removing some of them to see through trial and error but it didn't work as the syslog showed different errors and wasn't clear what port or IP was the new issue. So I've just put them all back again for now until I get a better option:

> # TCP connections inbound to port 139 and 445 from local network (192.168.0.0/24)
tcp|in|d=139|s=192.168.0.0/24
tcp|in|d=445|s=192.168.0.0/24

# UDP connections inbound to port 137 and 138 from local network (192.168.0.0/24)
udp|in|d=137|s=192.168.0.0/24
udp|in|d=138|s=192.168.0.0/24

# UDP connections outbound to port 137 to local network (192.168.0.0/24)
udp|out|s=137|s=192.168.0.0/24

Thanks again.

---

### Post by CharlesA on 2016-01-21
> **jonah1980 said:**
> Thanks Charles - now I'm getting somewhere!

The line I just added:



turns out was wrong and should be:



so I was putting the port as destination not the source. That's all it was!!

I'm going to try removing the other entries I made and see if I'm still blocked and then just re-add what is necessary again trying d/s combos until I've got the correct rule set.

Thanks everyone for the help!

Good luck! That should get it working for you.

> **darkod said:**
> That's the problem when blocking outgoing traffic with your firewall too. :) You have to remember to allow it also.

Usually all threats are outside and I tend to leave the OUTPUT policy at ACCEPT. However, if blocking outgoing too never forget to adjust rules...

Yeah. I tend to ignore outbound rules for internal servers, but I filter them via csf for stuff that is accessible from the Internet. Probably not the best way to do it, but *shrugs*

---

### Post by darkod on 2016-01-21
Since it seems you are blocking outgoing traffic too, I would say you also need 4 rules for outgoing, to match the 4 incoming rules. Also, on the outgoing you don't need to allow whole subnet s=192.168.0.0/24 because in this case the traffic is coming from one specific machine, your server. Lets assume your server IP is 192.168.0.100. In such case, i would say you need these outgoing rules:

```
# TCP connection outbound
tcp|out|s=139|s=192.168.0.100
tcp|out|s=445|s=192.168.0.100

# UDP connection outbound
udp|out|s=137|s=192.168.0.100
udp|out|s=138|s=192.168.0.100
```

I don't know if samba sends replies from all those ports but better to cover all four. Combined with your inbound rules, that should cover it.

---

### Post by jonah1980 on 2016-01-21
That's great thanks I've updated to use those 4 too. Is it still safe having 4 outward ports open for external traffic, as I'm just trying to have samba on the local network only?

---

### Post by darkod on 2016-01-21
Which ports exactly are you talking about? The outbound traffic is leaving your server not coming into it. So the outbound rules are not a danger.

The inbound rules are limited to traffic coming from 192.168.0.0/24 also, so unless someone from your internal network attacks the server, it is not a danger.

Don't forget that ALL servers have ports/services open, otherwise no client would ever be able to use them. Opening ports for your network is usually not any danger at all. And we are talking specific ports too. You can't ssh with these rules or anything...

You are not open to "external traffic". Maybe you misunderstand what the rules do, so you might think that.

---

### Post by jonah1980 on 2016-01-21
Thanks, a sigh of relief for a good job well done on that one then thanks for the help.

After all that though, now I can't print with my cups network printer that is attached to the server! If I disable the firewall it shows up in "Printers" on my laptop or desktop on the local network, but if I enable the firewall again it's gone. So I thought I could just do similar rules for port 631 like we've done for samba and it would work. But again I'm having problems and the printer isn't showing. Tried this:

> # Printer
tcp|out|s=631|s=192.168.0.0/24
tcp|in|s=631|s=192.168.0.0/24
udp|out|s=631|s=192.168.0.0/24
udp|in|s=631|s=192.168.0.0/24
tcp|out|d=631|s=192.168.0.0/24
tcp|in|d=631|s=192.168.0.0/24
udp|out|d=631|s=192.168.0.0/24
udp|in|d=631|s=192.168.0.0/24


to try to cover all bases to no avail. Also tried restart cups after restarting the firewall... Just when I thought I'd finished huh?

---

### Post by darkod on 2016-01-21
Are you sure printer communication goes through 631? Does it show in netstat?

PS. This is exacly why running a firewall on an internal network is not recommended. You run into all sort of issues even for simplest things. As we already discussed on the first page, unless the other private network 192.168.122.0/24 presents a real danger to your server, there is no need to run a firewall on it at all. It's not published on the internet, it's in your private network(s).

---

### Post by CharlesA on 2016-01-21
> **darkod said:**
> Are you sure printer communication goes through 631? Does it show in netstat?

PS. This is exacly why running a firewall on an internal network is not recommended. You run into all sort of issues even for simplest things. As we already discussed on the first page, unless the other private network 192.168.122.0/24 presents a real danger to your server, there is no need to run a firewall on it at all. It's not published on the internet, it's in your private network(s).

Depends if you have SSH open to the whole internet of not imo.

It is better to firewall the machine with rules that work rather than leave it open IMHO.

---

### Post by darkod on 2016-01-22
To the whole internet? We are talking about private networks, no? How can a 192.168.x.x be open to the whole internet if you are not forwarding ports to it on your main router or something...

A server with a private IP is not accessible from the internet... Or am I wrong?

---

### Post by jonah1980 on 2016-01-22
Hi thanks, I'm not sure how I gave you the impression it was a private server - as some posts in this thread say the server is mainly for external use but I just wanted some private samba shares and a private printer hence why we were trying to add firewall rules. Sorry for any confusion.

---

### Post by darkod on 2016-01-22
Because all the IPs mentioned so far (192.168.0.x and 192.168.122.x) are private subnets. There was no mentioning of the server having a public IP. Does it have one?

It doesn't matter much if people are using it from "inside" or "outside", if a server has no public IP no one can access it from the internet without port forwarding done on the internet gateway.

On the other hand, with port forwarding configured on the internet gateway it makes little sense blocking ports with a firewall on the server since traffic can arrive only from the forwarded ports. And there is also little sense blocking those forwarded ports because you are forwarding them with the purpose to be used.

The majority of servers that need a firewall are the ones with a public IP, reachable directly from the internet on various (if not all) ports... Even this is not exactly correct since the reachable ports are mainly only the ones running services, not ALL in the true meaning of the word.

Now, if your server really has public IP, then it's another story...

PS. Even in such case, and depending how your FW is working, you can disable it on the private interfaces, just let it protect the public one. That will save you from FW issues towards your clients on your private subnet(s).

---

### Post by CharlesA on 2016-01-22
> **darkod said:**
> To the whole internet? We are talking about private networks, no? How can a 192.168.x.x be open to the whole internet if you are not forwarding ports to it on your main router or something...

A server with a private IP is not accessible from the internet... Or am I wrong?

In my case, I have my server's port 22 exposed via port forwarding, but it only accepts connections from whitelisted IPs. That's what I meant. :)

---


---
title: "UFW and port mapping?"
date: 2009-12-14
forum: Security
---

### Post by MrMonster on 2009-12-14
Hi! I'm setting up a server with Karmic and have configured UFW, as I haven't really got my head around iptables yet. This is working fine so far, and I really like UFW. Unfortunately, I need to map incoming Port 80 connections from a specific Internet IP (I have two) to a localhost port, say 8080.

Following tips from Google, I tried this:

```
sudo iptables -t nat -A PREROUTING -i eth+ -p tcp --dport 80 -j REDIRECT --to-port 8080
```but it did not work. Setting UFW logging to high, I see that it gets blocked. I tried adding the following UFW rules, but to no avail.

```
sudo ufw allow proto tcp to <INTERNET IP> port 8080
sudo ufw allow proto tcp to 127.0.0.1 port 8080
```Is the iptables rule wrong, or does it need something else in addition, or could it be a ordering problem? I have UFW block everything by default, and only opened the ports that are really needed in the required direction. Also, I would need to include <INTERNET IP> in the iptables rule, so that it only maps the port from a specific IP.

---

### Post by cdenley on 2009-12-14
That looks correct, assuming <INTERNET IP> is the LAN address of the server you are running the command on. How are you testing it? I don't think it will work from the server itself.

---

### Post by MrMonster on 2009-12-15
"INTERNET IP" is a real public IP address, that anyone can access. I'm being reckless and testing on my real server! :twisted: So I am testing by pointing my browser at home to my server domain. What I maybe should check first is that the port is at all publicly accessible by temporarily installing apache on that public IP port.

---

### Post by cdenley on 2009-12-15
> **MrMonster said:**
> "INTERNET IP" is a real public IP address, that anyone can access. I'm being reckless and testing on my real server! :twisted: So I am testing by pointing my browser at home to my server domain. What I maybe should check first is that the port is at all publicly accessible by temporarily installing apache on that public IP port.

Is your browser at home on the same system listening for connections on port 8080 with the UFW rule? If it is a separate computer on your LAN, but you are pointing it to your router's WAN address, not all routers will route this according to port forwarding rules. You need to test with the LAN address, or from a system outside your network.

Also, creating a UFW rule to allow traffic to your router's WAN address is meaningless, since your NAT router translates the destination IP to your server's LAN address before it can be filtered by iptables/UFW. *If* you want to specify a "to" address for some reason, it should be the server's LAN address.

---

### Post by MrMonster on 2009-12-15
First of all, thank you for sticking with me! I haven't understood all that you meant, but I have understood enough to see that you didn't understand me, so I will try to be clearer.

I googled some more, and discovered part of the problem, but not the solution.

Firstly, I thought that iptables -L would show me all the rules, and therefore assumed that my "experiments" had been "discarded silently" by iptables, when in fact they were all still there. I needed iptables -t nat -S to see them. So I then deleted them all.

Secondly, I read that -j REDIRECT means "go to the source ip", when I thought it meant "go to localhost". Somewhere, I read that I should use REDIRECT "when I stay inside the same host", but REDIRECT doesn't allow specifying a target IP address, and one host can have many IP addresses. 

What I concretely want is to map all traffic coming to <INTERNET-IP>:80 to localhost:8080 (inside the server itself), as my apache is running inside a virtual machine running inside the host, and the port 80 of the VM has been mapped to localhost:8080 by the VM software. Running a wget localhost:8080 (from indide the host) returns the expected index.html from the VM. And if I instead run Apache directly inside the host on port 80, I can successfully connect to it from my home PC browser, so there is not problem involving my home PC firewall, my home router firewall, or my webserver firewall.

Looking at netfilter.org, I found this example, which is similar to what I want to do:
```
## Change destination addresses of web traffic to 5.6.7.8, port 8080.
# iptables -t nat -A PREROUTING -p tcp --dport 80 -i eth0  -j DNAT --to 5.6.7.8:8080
```So I though that this would do the trick:
```
iptables -A PREROUTING -i eth+ -t nat -p tcp -d <INTERNET-IP> --dport 80 -j DNAT \
--to 127.0.0.1:8080
```But no dice. I was hoping this would take all the TCP traffic coming from anywhere to <INTERNET-IP>:80 and forward it to localhost:8080, which would then forward it to VM:80. Looking at the webserver logs in the VM, I see that it doesn't get there at all (access log empty). Do I need some kind of SNAT? Or maybe must this rule come first in the nat table? (No clue how to do that.) It looks like this:
```
user@server:~$ sudo iptables -t nat -S
-P PREROUTING ACCEPT
-P POSTROUTING ACCEPT
-P OUTPUT ACCEPT
-A PREROUTING -d <INTERNET-IP>/32 -i eth+ -p tcp -m tcp --dport 80 -j DNAT \
--to-destination 127.0.0.1:8080
```I have checked my logfiles, but not trace of incoming connection being blocked, which shouldn't be the case anyway, since I tested that I CAN connect when Apache runs in the host itself.

I also tried again REDIRECT with another syntax, but in vain.```
iptables -t nat -A PREROUTING -d <INTERNET-IP>/32 -p tcp --dport 80 -j REDIRECT --to 2080
```This produces messages in the logfile that don't make sense to me:```
[UFW BLOCK] IN=eth0 OUT= MAC=... SRC=<DYNAMIC-HOME-IP> DST=<INTERNET-IP> LEN=48 TOS=0x00 PREC=0x00 TTL=120 ID=22940 DF PROTO=TCP SPT=25894 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0
```My home PC doesn't even know anything about port 8080; as far as it's concerned, it is accessing port 80, which is actually open in the firewall. And even if opening port 8080 in the firewall would help, I don't want to do that anyway, because the "clients" should only be able to "get in" using 80.
[EDIT]
I actually tried adding the following:```
ufw limit 8080/tcp
```and then it DID work, but now I can point my browser to <INTERNET-IP>:8080, and it works as well, which I don't want. 
[/EDIT]

---

### Post by cdenley on 2009-12-16
So you have a VM. The host of the VM is running an apache server on port 80. The guest is also running some web server on port 80. Apparently, the guest's network is configured separately from the host's network, and not bridged, hence the need for this "redirection". The VM software apparently routes incoming traffic on port 8080 on the host to port 80 on the guest. Is this correct?

If I understand correctly, you want connections received on the host on port 80 to be handled by the guest on the same port. You say only connections to "<INTERNET-IP>", though? Is this an address assigned to one of the hosts network interfaces? Are there multiple interfaces? LAN or WAN IP? Are there incoming connections on port 80 which should be handled by the host (not the guest)?

I think it would be easier to do this via apache than to configure some complicated routing. The "REDIRECT" target in iptables changes the destination port of a packet, not the source or destination IP. The "DNAT" target changes the destination IP of the packet to route it somewhere else. I believe this would work if the host were acting as an internet gateway for the guest, but I'm not sure.

I think it would be best to configure apache with mod_proxy to accomplish this. Exactly how would depend on the answers to my questions.

---

### Post by MrMonster on 2009-12-16
> ... Is this correct?Almost. I don't actually want to have a webserver on the host. It was only a test. I cannot have the port 80 inside the VM mapped to port 80 on the host directly, because the VM runs as "user X", and the VM software could only open the host's port 80 if it was root. There is no way to specify on which IP the VM software should do the mapping, and it seems that it listens to the configured port on all interfaces, as I can now the access the VM webserver through the host port 8080 on <INTERNET-IP>.

I have one LAN interface, and two <INTERNET-IP> addresses. I only want to map the traffic of one of them to the VM. The other IP should go directly to the host.

In all cases, "-j DNAT --to-destination 127.0.0.1:8080" does not seem to work at all. I think I have read in some other forum that it is to be expected.

As I now see it, I have several possibilities:

[LIST=1]
[*]Run the VM as root, and have the VM software map port 80 in the VM to port 80 in the host. Problem is that it would use *all* port 80, instead of just one. OTHO, I might want to do just that eventually.
[*]Use the current REDIRECT rule, and with some luck find a way of blocking port 8080 on the host interfaces from the outside, but I don't really believe in that anymore. It's annoying, but I don't rally see a major problem with it.
[*]Use Apache on the host and proxy it all to the VM, instead of using iptables. This is probably easier to setup then iptables, but has the disadvantages that: A) I now have an extra host process running. B) It is surely slower then iptables. C) Breaking into Apache would mean breaking into the host. D) Apart from security, the main reasons to use VM is that almost all the "configuration" is in the VM, making the setup of a new host much faster. Putting Apache in the host goes against that principle.
[*]Trying some other networking option of the VM software. I could also use something like a host-only virtual adapter, which would have it's own non-127.0.0.1 IP inside the host. Maybe I can use DNAT on that, which would be better then REDIRECT.
[/LIST]
One thing that would help my decision, is to know if the source IP gets lost in any of those scenarios, as I could then eliminate them, since I want to know who is accessing my webserver.

Do you see any other pro or con that could help me decide?

---

### Post by cdenley on 2009-12-16
> **MrMonster said:**
> 
I have one LAN interface, and two <INTERNET-IP> addresses. I only want to map the traffic of one of them to the VM. The other IP should go directly to the host.

Unless the two "<INTERNET-IP>" addresses are assigned to interfaces on the server, there is no way for the server to determine which "internet" IP it was originally sent to. When a packet reaches your router, your router forwards it to the correct LAN server by changing the destination IP. If you want to differentiate between traffic sent to different WAN IP's on your LAN server, you need them forwarded to different LAN addresses or different ports.
[http://ubuntuforums.org/showthread.php?t=555319](http://ubuntuforums.org/showthread.php?t=555319)

---

### Post by MrMonster on 2009-12-17
> **cdenley said:**
> Unless the two "<INTERNET-IP>" addresses are assigned to interfaces on the server, there is no way for the server to determine which "internet" IP it was originally sent to. When a packet reaches your router, your router forwards it to the correct LAN server by changing the destination IP. If you want to differentiate between traffic sent to different WAN IP's on your LAN server, you need them forwarded to different LAN addresses or different ports.
[http://ubuntuforums.org/showthread.php?t=555319](http://ubuntuforums.org/showthread.php?t=555319)

Sorry. :( I was confused. I somehow thought that when you said LAN and WAN, you meant "Ethernet" and "Wireless". I wasn't even drunk, so I'm starting to doubt my sanity.

Anyway, I have one physical "interface" (Ethernet) with two WAN (public Internet) IPs. I don't have any LAN IP at all. Trying to think ahead, it occurred to me that I don't actually have a choice but to use the "host-only" networking for the VMs, because otherwise with NAT they will only be able to communicate with the Internet, but not with each other. Once this is done, each VM will have an "host-internal" LAN IP which will not be localhost anymore, so I can keep the same port number everywhere, and I will be able to use DNAT instead of REDIRECT. In other words, I think I have my solution now.

---

### Post by BkkBonanza on 2009-12-18
I had to do this once to run a server inside VirtualBox on my system.
You do need a redirect type rule. The ones I used were,

# routing to allow accessing guest websvr machine on privelaged ports
iptables -t nat -A OUTPUT -o lo -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -t nat -A OUTPUT -o lo -p tcp --dport 443 -j REDIRECT --to-port 1443

Of course you may not need 443 for ssl use. On VirtualBox this is not enough as you also need to forward 8080 through the nat using a VBoxManage command. But not sure if you're using VB anyway so maybe irrlevant. If your VM is behind a "virtual" nat then you would also need to config a port forward to get it into the VM.

I ended up disabling this after a while because it was just easier and more flexible to use a host mode interface in VirtualBox rather than nat mode.

BTW a good place to put this redirect so it starts on boot is in the /etc/rc.local file. It will run as root during boot.

---

### Post by MrMonster on 2009-12-21
Yes, I am using VB, and trying to do precisely that. ATM, I have settled to running VB as root and doing VB nat-ing directly to 80 and 443 (no iptables rules). But this is only temporary. One of the main problem is that VB listens on all interfaces/IPs, and you cannot specify which one.  Eventually I want several VM listening to the same ports on several IPs.

Do I understand correctly that, if I do:

iptables -t nat -A OUTPUT -o lo -p tcp --dport 80 -j REDIRECT --to-port 8080

then I don't have to open 8080 in the FW, but get about the same effect as:

iptables -t nat -A PREROUTING -d <INTERNET-IP>/32 -p tcp --dport 80 -j REDIRECT --to 8080

? Can I then also limit this by destination IP address?

If you now use the "host mode interface", how do you get your VM to access the Internet, for example to download updates and do reverse DNS lookups for the logs?

---

### Post by BkkBonanza on 2009-12-21
I just add a second NAT mode interface to the VM. This allows it to connect out to do it's own stuff.

My use may be different from what you desire because in my case above I just accessed the VM from my host system. I was using it for dev work and so could test sites as needed. 

As far as a working network of VM servers the way I would do it is to use bridged mode and the DHCP server (router) on the real network will assign IPs to each VM you have. This just looks like an extension of your real LAN.

If you want to run multiple servers on the same port on one IP then a reverse proxy is needed. If you want to run multiple IPs on an interface then you can configure virtual interfaces with "ip add addr" or "ifconfig" also works. Then tell your server config which IP to listen on.

There are, of course, many ways to do things so it depends heavily on the goal desired.

---

### Post by Rich43 on 2011-04-10
Can UFW really not do port forwarding from the command line interface? I would like a definite yes or no.

Putting iptable rules in its config seems like a ugly hack to me and defeats the point of having ufw in the first place (ease of use).

I am using it for masquerading and I really need to forward a port from one ethernet device to another. I have my gateway on a DMZ and it is handling the firewalling with ufw.

Surly they thought of this when designing ufw :S

---

### Post by bodhi.zazen on 2011-04-11
ufw is a front end for iptables which in turn is a front end for netfilter.

ufw can do "basic" configuration, but for what you want, either learn iptables (you are half way there if you understand ufw) or use an alternate tool, such as shorewall.

That I know, ufw will not do port forwarding, you can look at man ufw:

[http://manpages.ubuntu.com/manpages/maverick/en/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/ufw.8.html)

Be warned, alternate tools can take as long to learn as iptables ;)

---

### Post by Rich43 on 2011-04-12
> **bodhi.zazen said:**
> ufw is a front end for iptables which in turn is a front end for netfilter.

ufw can do "basic" configuration, but for what you want, either learn iptables (you are half way there if you understand ufw) or use an alternate tool, such as shorewall.

That I know, ufw will not do port forwarding, you can look at man ufw:

[http://manpages.ubuntu.com/manpages/maverick/en/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/ufw.8.html)

Be warned, alternate tools can take as long to learn as iptables ;)

That is sad news, ufw is such a nice interface. I guess I will be learning shorewall (which is nice but little more learning curve).

---


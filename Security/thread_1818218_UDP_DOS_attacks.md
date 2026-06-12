---
title: "UDP DOS attacks"
date: 2011-08-04
forum: Security
---

### Post by Shii0 on 2011-08-04
Hello,
I have problem with DOS attacks repeating many times daily. Attacker sends large number of UDP packets to random ports which looks like this:
> 
Aug  3 01:59:52 xxx kernel: [135562.869465] ** DDOSudp> IN=eth0 OUT= MAC=xxx SRC=xxx DST=xxx LEN=8220 TOS=0x00 PREC=0x00 TTL=116 ID=10744 PROTO=UDP SPT=4325 DPT=1165 LEN=8200
> 
How it looks from FW log:
Packets  Time  Desc      LEN
852      01:59 DDOSudp   7684
5990     01:59 DDOSudp   8220
8132     02:00 DDOSudp   7684
56495    02:00 DDOSudp   8220
8338     02:01 DDOSudp   7684
57802    02:01 DDOSudp   8220
3525     02:02 DDOSudp   7684
25197    02:02 DDOSudp   8220
9520     02:03 DDOSudp   7684
66600    02:03 DDOSudp   8220
9069     02:04 DDOSudp   7684
63709    02:04 DDOSudp   8220
1112     02:05 DDOSudp   7684
7808     02:05 DDOSudp   8220
207      02:08 DDOSudp   7684
1479     02:08 DDOSudp   8220
7521     02:09 DDOSudp   7684
51905    02:09 DDOSudp   8220
1730     02:10 DDOSudp   7684
11978    02:10 DDOSudp   8220
937      02:11 DDOSudp   7684
7420     02:11 DDOSudp   8220
1186     02:12 DDOSudp   7684
8842     02:12 DDOSudp   8220
I have set up an firewall using iptables which will drop all packets from the IP after first DDOSudp   entry.
Problem is, that even so server will become inaccessible.
With packet length 8200 I suspect he overloads my 100mb connection.
Is there a way to overcome this?
Maybe something like braking connection when its exceeded certain length? Unfortunately I dont have much UDP related knowledge. 

I'm running Ubuntu 10.10 2.6.35-30-server

I will be grateful for any help in this.

---

### Post by Beacon11 on 2011-08-04
> **Shii0 said:**
> Problem is, that even so server will become inaccessible.
With packet length 8200 I suspect he overloads my 100mb connection.

You can setup rules to forward valid traffic and drop the flood, but if the flood is indeed eating your entire bandwidth it won't help; dropping traffic with iptables still ties up the port (as you seem to have noticed). Is it all coming from the same IP? To my knowledge, your only hope is to get the flood blocked somewhere up the line (e.g. your ISP). By the way, do those random ports need to be open?

---

### Post by Shii0 on 2011-08-04
> **Beacon11 said:**
> You can setup rules to forward valid traffic and drop the flood, but if the flood is indeed eating your entire bandwidth it won't help. Is it all coming from the same IP?
So far its from two ips. I'm dropping it, but still kills the service.
I have firewall set to just 3 allowed ports, so everything else is blocked out.
I could request to block ports on firewall before the server, but once he attacks my used ports, I'm in same problem.

---

### Post by Beacon11 on 2011-08-04
> **Shii0 said:**
> So far its from two ips. I'm dropping it, but still kills the service.

Sorry, I accidentally hit submit before I was done with my comment. You replied too fast! I would contact your ISP and inquire about getting these IPs blocked. They may not be thrilled about it, but they might help.

---

### Post by Shii0 on 2011-08-04
> **Beacon11 said:**
> Sorry, I accidentally hit submit before I was done with my comment. You replied too fast! I would contact your ISP and inquire about getting these IPs blocked. They may not be thrilled about it, but they might help.
They could agree, but for additional cost of course. Since its hosted dedicated server.
Isnt there any way to just break the packet flow on the server?

---

### Post by Beacon11 on 2011-08-04
> **Shii0 said:**
> Isnt there any way to just break the packet flow on the server?

I would install a firewall in front of your server (rather than having the server handle everything) to drop the bad packets and let the good stuff through. It will help, but not completely alleviate the problem if the attack is indeed a DDoS and is eating your connection.

EDIT: Oh wait... it doesn't sound like this is your own machine. This probably isn't an option. I'm not sure what to tell you then, other than to wait for a networking expert to stop by.

---

### Post by psusi on 2011-08-04
If you are the target of the DDOS, then there is nothing you can do on your end.  The firewall is on this side of your line, so the bandwidth has already been used by the time it sees them.

You mention though that all of the packets seem to be from the same ( or a few ) source addresses.  That means it is not a DDOS ( the D is for distributed, meaning hundreds or thousands of attackers are flooding you ).  In that case, you might be able to get your ISP to block it on their end ( from what I have seen, few, if any, are willing to do this ), or look up the owner of the source IP address and send them a cease and desist letter threatening legal action.

---

### Post by Shii0 on 2011-08-04
> **psusi said:**
> If you are the target of the DDOS, then there is nothing you can do on your end.  The firewall is on this side of your line, so the bandwidth has already been used by the time it sees them.

You mention though that all of the packets seem to be from the same ( or a few ) source addresses.  That means it is not a DDOS ( the D is for distributed, meaning hundreds or thousands of attackers are flooding you ).  In that case, you might be able to get your ISP to block it on their end ( from what I have seen, few, if any, are willing to do this ), or look up the owner of the source IP address and send them a cease and desist letter threatening legal action.
Yes, I mentioned its DOS, I just have one chain in firewall for it.
I have tried to contact my provider. Problem is additional cost here.
I would have to be able to set up ports I want + ability to push offending ip's on the fly.

---

### Post by Beacon11 on 2011-08-04
> **psusi said:**
> You mention though that all of the packets seem to be from the same ( or a few ) source addresses.  That means it is not a DDOS ( the D is for distributed, meaning hundreds or thousands of attackers are flooding you ).

Quick nitpick: Distributed by definition just means more than one. I would postulate that two pipes (two IPs), if they're fast enough, could overwhelm Shii0's pipe. Sort of a sucky botnet though :P .

---

### Post by Shii0 on 2011-08-04
was asked for 25euro per month just for firewall with ability to open some ports one time at installation (no changes later).
that would not even solve a problem :(

---

### Post by Beacon11 on 2011-08-04
> **Shii0 said:**
> was asked for 25euro per month just for firewall with ability to open some ports one time at installation (no changes later).
that would not even solve a problem :(

Yeah man... I hate to say it but I think you're stuck. You might try taking down the server for a little bit to see if the attacks give up now that you're not responding.

Heck, depending on what this server is for you might have a couple more options. Ask your host for a new IP, and/or if you have a domain name, come up with a secondary and black-hole the primary for a period of time.

---

### Post by Shii0 on 2011-08-05
> For DDOS'es we do not really have as solution. It fully depends on the way how you are using the server. For
example if the ddos is on IP base (not domain) you can nullroute the primary IP and continue with the
secondary. Also you can route the traffic to a third party covering DDOS attacks filtering the attacks. Besides
this we do not really offer protection for DDOS at the moment.
Got reply from my provider. So they don't really care. So much for their advised  Cisco CRS-1.
Even trough my original question was asking for renting a firewall.

---

### Post by uRock on 2011-08-05
If your service is important, then a small fee for having the ISP drop the packets before they reach your network is worth it.

---

### Post by Beacon11 on 2011-08-05
> **Shii0 said:**
> Got reply from my provider. So they don't really care. So much for their advised  Cisco CRS-1.
Even trough my original question was asking for renting a firewall.

Shii0, you're missing something very fundamental: there IS no solution. It's not that they don't care, they're simply saying exactly what I said in my previous post (nullroute == black-hole). If a DDOS is eating your connection, that's all you've got. While a properly configured firewall might help, it wouldn't be a magic solution.

EDIT: Their reply seems to imply you have a primary and secondary IP. Is that the case?

---

### Post by Shii0 on 2011-08-05
> **Beacon11 said:**
> Shii0, you're missing something very fundamental: there IS no solution. It's not that they don't care, they're simply saying exactly what I said in my previous post (nullroute == black-hole). If a DDOS is eating your connection, that's all you've got. While a properly configured firewall would help, it wouldn't be a magic solution.
well, not firewall at my 100mb input but on wan router. dropping offender ip's at entry level to datacenter would help indeed or it would crash whole datacenter if offender have enough bandwidth available.
I did that already and it works like charm. I dont have access to these devices trough.
With their hardware its easy to create a solution, well, if they are willing to spend few hours.

In any case I doubt getting another ip would help since its trough same port. They dont offer adding ports.

Edit: no, I dont have 2 ip's

---

### Post by Beacon11 on 2011-08-05
> **Shii0 said:**
> well, not firewall at my 100mb input but on wan router. dropping offender ip's at entry level to datacenter would help indeed or it would crash whole datacenter if offender have enough bandwidth available.
I did that already and it works like charm. I dont have access to these devices trough.
With their hardware its easy to create a solution, well, if they are willing to spend few hours.

In any case I doubt getting another ip would help since its trough same port. They dont offer adding ports.

Edit: no, I dont have 2 ip's

Okay-- I would try pointing your domain name elsewhere to begin with. That will help you to determine whether the attacks are based on your domain name or the IP address. Let us know if the attacks continue. If they do, ask your host if it would be willing to change your IP (have you done that?).

---

### Post by Shii0 on 2011-08-05
> **Beacon11 said:**
> Okay-- I would try pointing your domain name elsewhere to begin with. That will help you to determine whether the attacks are based on your domain name or the IP address. Let us know if the attacks continue. If they do, ask your host if it would be willing to change your IP (have you done that?).
well yeah, thats a problem. That would create a permanent service interruption at least for few days.
DNS sync can take long

Well, how I see it, only possible solution is to make changes at wan firewall. other then then there is no hope.

---

### Post by Beacon11 on 2011-08-05
> **Shii0 said:**
> well yeah, thats a problem. That would create a permanent service interruption at least for few days.
DNS sync can take long

Well, how I see it, only possible solution is to make changes at wan firewall. other then then there is no hope.

Ah, I was under the impression you already HAD a service interruption, sorry. Best of luck.

---

### Post by wacky_sung on 2011-08-05
As recommended by some others is the alternative solutions but present days there is no 100% solution for DDOS.What you can do is reported to your local police and get them to trace down the cyber attack.

---

### Post by psusi on 2011-08-06
Again, if all of the packets are coming from one or two addresses, then the solution is quite simple: look up the administrative contact for the network in the whois database, and send them an email asking them to stop the machine in question from flooding you, or you will have to take legal action.  More likely than not, they will resolve it quickly.

---


---
title: "Help: Somebody is trying to access my PC"
date: 2008-10-24
forum: Security
---

### Post by etdsbastar on 2008-10-24
Whenever I view my network status through SAMBA (SWAT) by typing the url:

[http://192.168.1.2:901/](http://192.168.1.2:901/)

I found that one ip-address is shown in the Active Connections and Active Shares with some unusual random names. 

I think someone is trying to access my PC or trying to hack me. 

Pls help me to get rid of this problem..

---

### Post by Bölvaður on 2008-10-24
block all incoming ports if you can.

that is from the outside.. like block from router side.

---

### Post by PmDematagoda on 2008-10-24
Assuming that this problem is on Ubuntu, this thread has been moved to the Security Discussions section.

---

### Post by etdsbastar on 2008-10-24
> **Bölvaður said:**
> block all incoming ports if you can.

that is from the outside.. like block from router side.

is there some other option for blocking all incoming ports.

Or there is another way to solve my problem.

Please help anyone...

---

### Post by Keen101 on 2008-10-24
you could try the firestarter GUI frontend for the firewall stuff.

search for it in synaptic.

---

### Post by cdenley on 2008-10-24
> **etdsbastar said:**
> Whenever I view my network status through SAMBA (SWAT) by typing the url:

[http://192.168.1.2:901/](http://192.168.1.2:901/)

I found that one ip-address is shown in the Active Connections and Active Shares with some unusual random names. 

I think someone is trying to access my PC or trying to hack me. 

Pls help me to get rid of this problem..

Is that ip address an internet ip or a LAN ip? You shouldn't have internet traffic being forwarded to your samba server. If you do, re-configure your router. You could also filter it using UFW.
```

sudo ufw enable
sudo ufw default deny
sudo ufw allow from 192.168.0.0/16

```
This would only allow LAN users to connect to any server running on that computer.

If you want to block LAN users who are trying to guess passwords or shares, you can adapt fail2ban to accomplish that.

---

### Post by etdsbastar on 2008-10-28
Thanks cdenly,

I hope this option will block my connections and allow only lan users.

I used:

sudo ufw with 192.168.1.1/16

Is that correct (This is my routers IP).

Reply soon.

---

### Post by cdenley on 2008-10-28
> **etdsbastar said:**
> Thanks cdenly,

I hope this option will block my connections and allow only lan users.

I used:

sudo ufw with 192.168.1.1/16

Is that correct (This is my routers IP).

Reply soon.

That does the same thing. The /16 makes it an ip range which will allow all 192.168.*.* addresses. These are unroutable IP addresses, meaning any host with that address must be on your LAN.

---

### Post by etdsbastar on 2008-10-29
> **cdenley said:**
> That does the same thing. The /16 makes it an ip range which will allow all 192.168.*.* addresses. These are unroutable IP addresses, meaning any host with that address must be on your LAN.

Hey dear,

I tried your solution. Its ok, some IPs are blocked. I saw them in my log files. But, still some IP's are entering my PC, I saw them in my Samba status.

Please give me another solution for the same. I am giving my IP Tables information to you:

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  127.0.0.0/8          anywhere            LOG level warning 
DROP       all  --  127.0.0.0/8          anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  192.168.1.0/24       anywhere            
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
LOG        all  --  192.168.1.0/24       anywhere            LOG level warning 
DROP       all  --  192.168.1.0/24       anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  anywhere             117.198.1.253       
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  192.168.1.0/24       anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        all  --  anywhere             192.168.1.0/24      LOG level warning 
DROP       all  --  anywhere             192.168.1.0/24      
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  anywhere             192.168.1.0/24      
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
LOG        all  --  anywhere             192.168.1.0/24      LOG level warning 
DROP       all  --  anywhere             192.168.1.0/24      
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  117.198.1.253        anywhere            
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain ufw-after-forward (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK FORWARD]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-input (0 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK INPUT]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-output (0 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-forward (0 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-input (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
DROP       all  --  anywhere             anywhere            ctstate INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK NOT-TO-ME]: ' 
DROP       all  --  anywhere             anywhere            

Chain ufw-user-forward (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  192.168.0.0/16       anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

```Please provide a complete security solution to block all IPs except my LAN connectivity, Internet and Internet Sharing. 

I am also attaching my screenshot of Samba Shares. Please have a look on Active Connections, The ip address shown there is unexpected.

Awaiting... and Thanks in advance.

---

### Post by etdsbastar on 2008-10-29
Awaiting for your early reply...

Help me please...

---

### Post by etdsbastar on 2008-10-29
Please, Is anyone there to help me ...

---

### Post by cdenley on 2008-10-29
> 
ACCEPT     all  --  anywhere             anywhere

The first line in your input chain accepts everything. This would cause any other firewall rules to be ignored.

---

### Post by Girya on 2008-10-30
How about modifying your /etc/hosts.allow file to allow only connections from your local network? 

> httpd: LOCAL, 192.168.1.0/255.255.255.0

the above would allow only ips' 192.168.1.1-192.168.1.255

---

### Post by etdsbastar on 2008-10-30
let me try this and be back soon...

Thanks...

---

### Post by etdsbastar on 2008-11-09
please tell me some more solutions... i am frustrated now ... please help me ....

---

### Post by casper0191 on 2009-03-18
[FONT="Century Gothic"][/FONT] Well have you already using a firewall and an Anti virus? Try it might help to restrict and file or packet sending. If you are already using one set up the fire wall to restrict file sending that is exceeding on your file size of your choice.

---

### Post by Megalomania on 2009-06-22
just wondering - what are these mysterious IP addresses?

---

### Post by Soul-Sing on 2009-06-23
```
sudo apt-get install tcpdump
```

if eth0 is your network
run: ```
tcpdump -n -i eth0 > tcpdump.txt
gzip tcpdump.txt
```

I want/you can take a look at the "traffic" for some minutes.

---

### Post by DGortze380 on 2009-06-23
> **Megalomania said:**
> just wondering - what are these mysterious IP addresses?

Finally, someone asked the right question.

Is it 117.198.52.69 that you're worried about?

Please go to [http://www.whatsmyip.org/](http://www.whatsmyip.org/)
I'd be willing to bet it's you're own external address seeing as the whois lookup for that IP comes back as NIB in India.

---

### Post by cariboo on 2009-06-23
It is a lot easier to open a terminal and type:

```
whois 117.198.52.69
```

---

### Post by DGortze380 on 2009-06-23
> **cariboo907 said:**
> It is a lot easier to open a terminal and type:

```
whois 117.198.52.69
```

Right ... for the lookup ... but I want him to compare that address from the logs to HIS Public IP ... which he can get a number fo ways, but it's easiest to go to whatsmyip.org

---


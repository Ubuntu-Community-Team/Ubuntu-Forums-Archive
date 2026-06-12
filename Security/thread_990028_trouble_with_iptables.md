---
title: "trouble with iptables"
date: 2008-11-22
forum: Security
---

### Post by ace201 on 2008-11-22
i'm having trouble opening ports with iptables. i've used firestarter before and it works great, but i want to start using iptables because i work on the server edition quite a bit.

anyway, this is what i see when i type 'iptables -L':

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  


which is the default. I want open port 11211 so i ran the following command:

iptables -A INPUT -s 192.168.1.4 -d 192.168.1.3 -p tcp --dport 11211 -j ACCEPT

and it showed up in the output when i ran 'iptables -L'. So i ran the following command from 192.168.1.4

sudo nmap -sS -O 192.168.1.3

but the port still seems to be closed. it only shows two open ports.
what am i doing wrong?

---

### Post by Lars Noodén on 2008-11-22
Use different options when running the program nmap.  -sO will not give you the information you are looking for:


      [INDENT] "When an IP protocol scan is
       requested (-sO), Nmap provides information on supported IP
       protocols rather than listening ports."[/INDENT]

See:
      [INDENT][http://linux.die.net/man/1/nmap](http://linux.die.net/man/1/nmap)
[/INDENT]
One of the ways to find out if the port is open is to use these options with the nmap program:

[INDENT]       nmap -A -T4 -P0 -p 11211 192.168.1.3[/INDENT]

Another way would be to run the program telnet, pointed at port 11211:

[INDENT]      telnet 192.168.1.3 11211[/INDENT]

---

### Post by ace201 on 2008-11-22
Thanks for your reply. i tried the nmap command as you supplied and it said that the port is closed. I also tried the telnet command but connection was refused (most likely because the port is closed). When a rule is set using iptables does it take effect staright away?

any help appreciated.

---

### Post by kevdog on 2008-11-22
It should, however please list 

iptables -L

That will always list the current policies

---

### Post by ace201 on 2008-11-22
hi, the following is what i get when i execute 'iptables -L'

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  desktop.asim.homelinux.net  asim-laptop.local   tcp dpt:11211 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  



the only difference i can spot is the ip addresses have been replaced to domain names by iptables. does that matter?

thanks

---

### Post by gombadi on 2008-11-22
> **ace201 said:**
> 
anyway, this is what i see when i type 'iptables -L':

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  


which is the default. I want open port 11211 so i ran the following command:

iptables -A INPUT -s 192.168.1.4 -d 192.168.1.3 -p tcp --dport 11211 -j ACCEPT



According to this you currently have no firewall rules and default policy is to accept all packets.

When you added the rule to allow incoming packets on port 11211 it just allowed packets that were already going to be allowed by the default policy.


> 
Thanks for your reply. i tried the nmap command as you supplied and it said that the port is closed. I also tried the telnet command but connection was refused (most likely because the port is closed). When a rule is set using iptables does it take effect staright away?


Yes rules take effect straight away.

If you are still getting a connection refused message then it looks like nothing is listening on that port.

At a command prompt type this and see if anything is using the port.

```

sudo netstat -plntu

```

---

### Post by kevdog on 2008-11-22
To change the default rule policy to DROP rather than accept, this is the syntax:


iptables -P INPUT DROP
iptables -P FORWARD DROP

---

### Post by ace201 on 2008-11-22
thanks guys, i've figured it out.

i had to enter the following rules:

# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A FORWARD -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
The last rule obviously allows any traffic the leave the server. 
(taken from [http://www.howtoforge.com/linux_iptables_sarge](http://www.howtoforge.com/linux_iptables_sarge))

Finally i edited the memcached configuration file. i commented out the line '-l 127.0.0.1' and it's working. By default it listens only on the localhost in ubuntu.

---


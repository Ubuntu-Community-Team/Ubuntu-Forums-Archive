---
title: "iptables not blocking IP"
date: 2009-11-10
forum: Security
---

### Post by silvita on 2009-11-10
Hello everyone, 
I have configured my Ubuntu Jaunty to include fail2ban, and it seemed to work fine (IPs were added to iptables and such). However, after simulating an attack, I noticed that I was still able to access the server. My IP, however, was set as "DROP". 
   
I know I am missing something, but I just cannot see the mistake. Am I supposed to add something else to the iptables list?
   
Thanks for your help. 
   
By the way, here is my iptables -L: 
   
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh
ACCEPT     all  --  anywhere             anywhere
REJECT     all  --  anywhere             127.0.0.0/8         reject-with icmp-port-unreachable
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:(mysshport)
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/min burst 5 LOG level debug prefix `iptables denied: '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere

Chain fail2ban-ssh (1 references)
target     prot opt source               destination
DROP       all  --  (my ip)              anywhere
RETURN     all  --  anywhere             anywhere

```

---

### Post by cdenley on 2009-11-10
That looks like it should drop any connections on port 22 from your IP.
```

nc -z -v (my ip) 22

```
Are you sure the rule didn't expire between the time you checked iptables and when you attempted to connect? Are you sure you aren't connecting to 127.0.0.1? Are you sure you're using port 22?

---

### Post by silvita on 2009-11-10
Hi, thanks for your reply. 
   
  When I tested it, the fail2ban operation had not expired. I am also connecting from my home computer to the server, so I am using the machine's full IP. 

   
  I am not using port 22; I am using a custom port for SSH (I think it's 30000). The alternate port is set in sshd_config. 
   
  I tried using nc like you suggested (on port 30000), but it appears that the connection is open, even after checking that the IP was still on the Drop list (I checked it both before and after doing the operations). 
   
  Could this be due to my custom port? Should I revert it to 22, or could it be something else?
   
  Thanks again.

---

### Post by cdenley on 2009-11-10
You want to use your custom port, then either configure fail2ban to block all ports, or change it to block your custom port.
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination
fail2ban-ssh  tcp  --  anywhere             anywhere            **[COLOR="Red"]multiport dports ssh[/COLOR]**
ACCEPT     all  --  anywhere             anywhere
REJECT     all  --  anywhere             127.0.0.0/8         reject-with icmp-port-unreachable
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:(mysshport)
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/min burst 5 LOG level debug prefix `iptables denied: '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere

Chain fail2ban-ssh (1 references)
target     prot opt source               destination
DROP       all  --  (my ip)              anywhere
RETURN     all  --  anywhere             anywhere

```

in /etc/fail2ban/jail.conf
```

[ssh]

enabled = true

# filter only port 30000
port    = **[COLOR="Red"]30000[/COLOR]**

# filter all connections from that IP
#port   = all
filter  = sshd
logpath  = /var/log/auth.log
maxretry = 6

```

---

### Post by silvita on 2009-11-10
Thanks, it worked wonderfully!

---


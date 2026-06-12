---
title: "Restrict SSH to specific source ips?"
date: 2010-04-07
forum: Security
---

### Post by yeleek on 2010-04-07
Hi,

I want to restrict SSH so that its only accessible via the machines I own on this network.  Obviously need to secure user authentication/host authentication, that aside though is the following sufficient at a network level given technical users also use this network?  IP addresses are static, though I know they could be spoofed.

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
existing-connections  all  --  anywhere             anywhere            
allowed    all  --  anywhere             anywhere            
LOGNDROP   all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain LOGNDROP (1 references)
target     prot opt source               destination         
LOG        tcp  --  anywhere             anywhere            limit: avg 5/min burst 5 LOG level notice prefix `IPTABLES Denied TCP: ' 
LOG        udp  --  anywhere             anywhere            limit: avg 5/min burst 5 LOG level notice prefix `IPTABLES Denied UDP: ' 
LOG        icmp --  anywhere             anywhere            limit: avg 5/min burst 5 LOG level notice prefix `IPTABLES Denied ICMP: ' 

Chain allowed (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.60.3         anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  192.168.60.4         anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  192.168.60.5         anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  192.168.60.6         anywhere            tcp dpt:ssh 

Chain existing-connections (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state RELATED 
```

and

```
# /etc/hosts.allow: list of hosts that are allowed to access
sshd: 192.168.60.2
sshd: 192.168.60.3
sshd: 192.168.60.4
sshd: 192.168.60.5
sshd: 192.168.60.6

```

and

```
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system
sshd: ALL
```

Thanks

---

### Post by bodhi.zazen on 2010-04-07
You can do this with

1. SSH - edit /etc/ssh/sshd_congig

see man sshd_config

[http://manpages.ubuntu.com/manpages/lucid/en/man5/sshd_config.5.html](http://manpages.ubuntu.com/manpages/lucid/en/man5/sshd_config.5.html)

See the section on AllowUsers, syntax is 

user@ip_address

2. Iptables / firewall. You have several options to configure your firewall, from iptables to ufw to other config tools.

3. tcp_wrappers - which is what you are doing with hosts.allow and hosts.deny.

Your config looks fine to me, are you having a problem ?

---

### Post by yeleek on 2010-04-08
> Your config looks fine to me, are you having a problem ? 

Thank you for the reply.  Not a problem yet, but one of the individuals who uses this network has been know to 'dabble' with the likes of Backtrack4.  

Given the above config then, would it be possible to setup ssh to require both a password and a cryptographic key (i.e. two factor authentication).  I know this means I'd have to carry the key with me - which is fine, but just wondered?

Thanks again

Ben

---

### Post by bodhi.zazen on 2010-04-08
> **yeleek said:**
> Thank you for the reply.  Not a problem yet, but one of the individuals who uses this network has been know to 'dabble' with the likes of Backtrack4.  

Given the above config then, would it be possible to setup ssh to require both a password and a cryptographic key (i.e. two factor authentication).  I know this means I'd have to carry the key with me - which is fine, but just wondered?

Thanks again

Ben

Yes. That is how I manage ssh, set up a key and disable password logins.

The keys require passwords ...

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by yeleek on 2010-04-09
Great - thanks :)

---


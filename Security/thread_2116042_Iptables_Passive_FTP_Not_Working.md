---
title: "Iptables Passive FTP Not Working"
date: 2013-02-14
forum: Security
---

### Post by Baswazz on 2013-02-14
I am trying to setup iptables to allow pasv ftp.
If i am right i need ip_conntrack_ftp module for this. Only it looks like it has changed to nf_conntrack

I created the following shell script:

```
#!/bin/sh
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
**modprobe nf_conntrack_ftp**
# Setting default filter policy
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
# Block specific ip-address
iptables -A INPUT -s xxx.xxx.xxx -j DROP
# Unlimited access to loop back
iptables -A INPUT -i lo -j ACCEPT
# Allow SSH and Passive FTP
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --dport 22 -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --dport 33600 -j ACCEPT
# DROP everything and Log it
#iptables -A INPUT -j LOG
iptables -A INPUT -j DROP
```

I am getting this error from the FTP client
> [L] Data Socket Error: Connection timed out
[L] List Error

My Ubuntu version is
Ubuntu 10.04.4 LTS
```
$ uname -r
2.6.32-45-generic-pae
```

```
$ lsmod | grep ftp
nf_nat_ftp              1836  0
nf_nat                 15735  2 nf_nat_ftp,iptable_nat
nf_conntrack_ftp        5381  1 nf_nat_ftp
nf_conntrack           61615  6 nf_nat_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state,nf_conntrack_ftp
```

Can someone help me how to fix this.

---

### Post by JKyleOKC on 2013-02-14
Your rule to accept the passive data ports must be a range, not just one port, and the server must be configured to use the same range. Then the opening dialog within FTP will tell the server to use passive transfer, and the server will reply with a randomly selected port number within that range. The FTP program then listens for the data on that specified port number.

Hope this helps!

---

### Post by Baswazz on 2013-02-14
> **JKyleOKC said:**
> Your rule to accept the passive data ports must be a range, not just one port, and the server must be configured to use the same range. Then the opening dialog within FTP will tell the server to use passive transfer, and the server will reply with a randomly selected port number within that range. The FTP program then listens for the data on that specified port number.

Hope this helps!

```
$IPTABLES -A INPUT -p tcp --destination-port 30000:30999 -j ACCEPT
```

I am used to use this line of code. It does work. Only it is more a security risk because this port range is wide open.
I did read i can fix this using the modprobe nf_conntrack_ftp for the tracking.

---

### Post by alphacrucis2 on 2013-02-14
You don't need to specify any port or port range for either active or passive ftp. That's the whole point of RELATED.

You need to specify the ftp control port 21 for the initial connection - add a line for that in addition to the port 22 (SSH) line. The  ESTABLISHED,**[COLOR="Red"]RELATED[/COLOR]** handles the rest.

---

### Post by Baswazz on 2013-02-14
> **alphacrucis2 said:**
> You don't need to specify any port or port range for either active or passive ftp. That's the whole point of RELATED.

You need to specify the ftp control port 21 for the initial connection - add a line for that in addition to the port 22 (SSH) line. The  ESTABLISHED,**[COLOR="Red"]RELATED[/COLOR]** handles the rest.

Like this (my first post)?

```
iptables -A INPUT -p tcp -i eth0 --dport 22 -j ACCEPT
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp -i eth0 --dport 33600 -j ACCEPT
```

---

### Post by alphacrucis2 on 2013-02-14
You haven't allowed for tcp 21 - the ftp control port.


```
iptables -A INPUT -p tcp -i eth0 --dport 21 -j ACCEPT
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
```


port 22 is SSH not FTP. You can run file transfer over SSH but that has nothing to do with ftp protocol and RELATED is not required for that.

---

### Post by Baswazz on 2013-02-15
> **alphacrucis2 said:**
> You haven't allowed for tcp 21 - the ftp control port.


```
iptables -A INPUT -p tcp -i eth0 --dport 21 -j ACCEPT
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
```


port 22 is SSH not FTP. You can run file transfer over SSH but that has nothing to do with ftp protocol and RELATED is not required for that.


I setup a custom ftp port 33600, i forgot to mention that.

```
iptables -A INPUT -p tcp -i eth0 --dport 33600 -j ACCEPT
```

---

### Post by alphacrucis2 on 2013-02-15
> **Baswazz said:**
> I setup a custom ftp port 33600, i forgot to mention that.

```
iptables -A INPUT -p tcp -i eth0 --dport 33600 -j ACCEPT
```

But ftp conntrack module doesn't know that, so RELATED wont work. I don't know if you can tell ftp conntrack to look for an alternative ftp control port - it has to know because the control port signals what passive port will be used for each data transfer. ftp contrack monitors the control port to determine this. I suppose you could patch the module source and compile it with the alternate port number.


Edit: Looking into it you should be able to use helper match

[http://ipset.netfilter.org/iptables.man.html](http://ipset.netfilter.org/iptables.man.html)

You would add before the -j your line above

-m helper --helper ftp-33600 

ie:
```

iptables -A INPUT -p tcp -i eth0 --dport 33600 -m state --state NEW -m helper --helper ftp-33600 -j ACCEPT
```


I also added the match for NEW to make sure you only allow SYN packets with dest 33600, as without that it will allow packets that are out of state 
which is bad practice. You should do the same with your SSH rule. The in state packets are handled by checking for ESTABLISHED. BTW make sure the normal conntrack module is load as well as conntrack_ftp

---

### Post by Baswazz on 2013-02-15
> **alphacrucis2 said:**
> But ftp conntrack module doesn't know that, so RELATED wont work. I don't know if you can tell ftp conntrack to look for an alternative ftp control port - it has to know because the control port signals what passive port will be used for each data transfer. ftp contrack monitors the control port to determine this. I suppose you could patch the module source and compile it with the alternate port number.

This was indeed what i am reading on the internet.
As Ubuntu does not have a config file, it has to be made manually. And i did read somewhere that it has to be placed in the /etc/modeprobe.d/

conntrack.conf
```
options ip_conntrack_ftp ports=21,33600
```

> 
Edit: Looking into it you should be able to use helper match

[http://ipset.netfilter.org/iptables.man.html](http://ipset.netfilter.org/iptables.man.html)

You would add before the -j your line above

-m helper --helper ftp-33600 

ie:
```

iptables -A INPUT -p tcp -i eth0 --dport 33600 -m state --state NEW -m helper --helper ftp-33600 -j ACCEPT
```


I also added the match for NEW to make sure you only allow SYN packets with dest 33600, as without that it will allow packets that are out of state 
which is bad practice. You should do the same with your SSH rule. The in state packets are handled by checking for ESTABLISHED. BTW make sure the normal conntrack module is load as well as conntrack_ftp

When adding this rule i can't connect to the ftp server.

```
~$ lsmod | grep conntrack
xt_conntrack            2302  1
nf_conntrack_ipv4      10672  4 iptable_nat,nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
x_tables               14299  6 xt_conntrack,ipt_LOG,iptable_nat,xt_state,xt_tcpudp,ip_tables
**nf_conntrack_ftp**        5381  0
**nf_conntrack**           61615  6 xt_conntrack,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state,nf_conntrac                                                          _ftp

```

Both nf_conntrack_ftp and nf_conntrack modules are loaded.

One thing that could be important is that i am using encrypted connection SSL. ip_conntrack_ftp is not able to inspect encrypted traffic, thus data traffic is not identified as RELATED and is thus dropped.

---

### Post by alphacrucis2 on 2013-02-15
> **Baswazz said:**
> This was indeed what i am reading on the internet.
As Ubuntu does not have a config file, it has to be made manually. And i did read somewhere that it has to be placed in the /etc/modeprobe.d/

conntrack.conf
```
options ip_conntrack_ftp ports=21,33600
```



When adding this rule i can't connect to the ftp server.

```
~$ lsmod | grep conntrack
xt_conntrack            2302  1
nf_conntrack_ipv4      10672  4 iptable_nat,nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
x_tables               14299  6 xt_conntrack,ipt_LOG,iptable_nat,xt_state,xt_tcpudp,ip_tables
**nf_conntrack_ftp**        5381  0
**nf_conntrack**           61615  6 xt_conntrack,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state,nf_conntrac                                                          _ftp

```

Both nf_conntrack_ftp and nf_conntrack modules are loaded.

One thing that could be important is that i am using encrypted connection SSL. ip_conntrack_ftp is not able to inspect encrypted traffic, thus data traffic is not identified as RELATED and is thus dropped.


That's right. RELATED doesn't work if the ftp control port is encrypted. That is the problem with ftp-s versus sftp. Can you configure the ftp to specify a range of ports that are to be used for the PASV data transfer - that is probably the only option in this case. Better still would be to use sftp which operates only using the SSH port so nothing special has to be done other than allow the SSH connection.

---

### Post by Baswazz on 2013-02-15
> **alphacrucis2 said:**
> That's right. RELATED doesn't work if the ftp control port is encrypted. That is the problem with ftp-s versus sftp. Can you configure the ftp to specify a range of ports that are to be used for the PASV data transfer - that is probably the only option in this case. Better still would be to use sftp which operates only using the SSH port so nothing special has to be done other than allow the SSH connection.

Ok thanks for your help.
There are a lot of topics around but none of them did say it can't be done with secure connections.

---


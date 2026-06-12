---
title: "Error on iptables implementation"
date: 2013-02-06
forum: Security
---

### Post by slickymaster on 2013-02-06
I'm trying to alter my computer security paradigm by giving up on UFW and implementing IPtables.

So far I've done my script but when I try to run it, I get this error:
```
iptables v1.4.12: Cannot use -X with -A
```

I've tried to goolge it for any help but to no avail. It seems that no one ever got stuck with the same situation.

I don't think that the problem lies with my script which is as follow:

```
#!/bin/bash


echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
echo 0 > /proc/sys/net/ipv4/conf/all/accept_source_route
echo 1 > /proc/sys/net/ipv4/tcp_syncookies
echo 0 > /proc/sys/net/ipv4/conf/all/accept_redirects
echo 0 > /proc/sys/net/ipv4/conf/all/send_redirects
echo 1 > /proc/sys/net/ipv4/conf/all/rp_filter
echo 1 > /proc/sys/net/ipv4/conf/all/log_martians

iptables --flush

iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

iptables -A OUTPUT -p tcp --dport 21 -j ACCEPT #-->FTP
iptables -A OUTPUT -p tcp --dport 22 -j ACCEPT #-->SSH
iptables -A OUTPUT -P TCP --dport 23 -j ACCEPT #-->TELNET
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT #-->DNS
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT #-->HTTP
iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT #-->HTTPS
iptables -A OUTPUT -p tcp --dport 51413 -j ACCEPT #-->BT
iptables -A OUTPUT -p tcp --dport 6969 -j ACCEPT #-->BT tracker
iptables -A OUTPUT -P tcp --dport 8001 -j ACCEPT #-->IRC
iptables -A OUTPUT -p udp --dport 67:68 -j ACCEPT #-->DHCP
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT #-->DNS
iptables -A OUTPUT -p udp --dport 51413 -j ACCEPT #-->BT

iptables -N LOGNDROP
iptables -A INPUT -j LOGNDROP
iptables -A LOGNDROP -j LOG
iptables -A LOGNDROP -j DROP

iptables-save > /etc/iptables.rules
```

Is there something that perhaps I'm missing?

---

### Post by SeijiSensei on 2013-02-06
I'm not sure I understand why you are using OUTPUT in all the rules having to do with services like SSH.  Is this a server?  If so, you would want to allow INPUT to those ports.  Any replies the machine sends are going to be sent to high ports (>1023) on the client.  

For instance, my webservers have rules like this:
```
iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 80 -j ACCEPT
```

It's very rare that you need OUTPUT rules, including the ESTABLISHED,RELATED rule.

I wonder if the capitalization of TCP in the telnet line is causing a problem.  Certainly iptables is case-sensitive when it comes to chain labels like INPUT.  I don't know about the other parameters; I've only ever used lower-case for them.

---

### Post by iponeverything on 2013-02-06
```

iptables -A OUTPUT -P TCP --dport 23 -j ACCEPT #-->TELNET
iptables -A OUTPUT -P tcp --dport 8001 -j ACCEPT #-->IRC

```

make these -p instead of -P

---

### Post by spynappels on 2013-02-07
I presume you are running the script using sudo, or as root?

I would agree with SeijiSensei though, your rule set looks odd.

Is this a desktop/laptop you use to connect to the Internet? I'm pretty sure it is not a server. Can you explain how you think that limiting outbound connections improves your security? The inbound (INPUT) chain rules look fine, as long as you are not running any server services, but the outbound (OUTPUT) chain rules do not add any ral value, and might make other stuff break, such as accessing a Windows share, or a network printer shared using Samba for example.

---

### Post by slickymaster on 2013-02-07
> **SeijiSensei said:**
> I'm not sure I understand why you are using OUTPUT in all the rules having to do with services like SSH.  Is this a server?  If so, you would want to allow INPUT to those ports.  Any replies the machine sends are going to be sent to high ports (>1023) on the client.  

For instance, my webservers have rules like this:
```
iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 80 -j ACCEPT
```

It's very rare that you need OUTPUT rules, including the ESTABLISHED,RELATED rule.

I wonder if the capitalization of TCP in the telnet line is causing a problem.  Certainly iptables is case-sensitive when it comes to chain labels like INPUT.  I don't know about the other parameters; I've only ever used lower-case for them.

> **spynappels said:**
> I presume you are running the script using sudo, or as root?

I would agree with SeijiSensei though, your rule set looks odd.

Is this a desktop/laptop you use to connect to the Internet? I'm pretty sure it is not a server. Can you explain how you think that limiting outbound connections improves your security? The inbound (INPUT) chain rules look fine, as long as you are not running any server services, but the outbound (OUTPUT) chain rules do not add any ral value, and might make other stuff break, such as accessing a Windows share, or a network printer shared using Samba for example.

No, it's not a server, just a laptop I use for development, but there's an error in the script I paste in my previous post that I come to notice just now, but that has nothing to do with the issue I'm dealing. The error is that I forgot to comment out the rules for FTP, SSH and TELNET, which for now I have no intention on using.

But the idea behind the limiting of all outbound connections is in fact a purpose of increasing safety.
Myself I am, or better, I use to be, one of those who sat comfortably under the misconception that just because I was running a Linux OS, being behind a NAT router and having UFW enabled there was no danger or harm that could hit me. And truthfully, until today, to my best knowledge I never had any problems.

But recently I was browsing this forum and by chance I came across this thread: [Do I need a Firewall for Ubuntu?]("http://ubuntuforums.org/showthread.php?t=1871177") which I avidly read and  in turn led me to the very extensive and pedagogic thread [Security for newbies]("http://ubuntuforums.org/showthread.php?t=1873643").
And the nuclear premise I extract from both (specially from the expert opinions of **Dangertux** and **haqking**), besides the need of a layered defence schema approach, is the need of having a rigid outbound traffic control.

If you guys think that I'm misunderstanding what is meant in those threads I really will appreciate all the information that you're willing to generously offer me.
Basically I just use this computer for Java, SQL and PL/SQL development, surf the web and occasionally access to IRC.

One other thing, since most of my work is towards database applications development, I also have, and need to communicate with, mySQL and Apache Derby databases, Glassfish and Tomcat servers, all local, so I'm going to have to set rules for them, also. If you'd be kind and generous enough to help, I would be very thankfull. 

> **iponeverything said:**
> ```

iptables -A OUTPUT -P TCP --dport 23 -j ACCEPT #-->TELNET
iptables -A OUTPUT -P tcp --dport 8001 -j ACCEPT #-->IRC

```make these -p instead of -P

Anyway, I'm not sure what happened but I've got it working.

---

### Post by spynappels on 2013-02-08
I guess it is always going to be a trade-off between security and useability, and blocking all but a specific set of outbound connections will theoretically add an extra layer of security, at the cost of making it less easy to access further services without further configuration.

If you understand that and are happy to put in the extra work every time you need to allow another outbound connection for another piece of the infrastructure like a MySQL server, Tomcat server, etc., that's fine.

If you are careful about what sites you visit and create strict AppArmor profiles for your browser, you may find that you will never have any other outbound connections logged, and in the interest of making your own life somewhat easier, you may decide to relax the outbound rules somewhat.

Even if you don't, you can be happy that you are in control of your own system and what's allowed in or out, and to me, that's part of the joy of Linux.

Glad it's working for you now.

---

### Post by slickymaster on 2013-02-08
> **spynappels said:**
> I guess it is always going to be a trade-off between security and useability, and blocking all but a specific set of outbound connections will theoretically add an extra layer of security, at the cost of making it less easy to access further services without further configuration.

If you understand that and are happy to put in the extra work every time you need to allow another outbound connection for another piece of the infrastructure like a MySQL server, Tomcat server, etc., that's fine.

I'm aware of that. My aim is to try to find the best equilibrium between security and functional pragmatism.

> **spynappels said:**
> If you are careful about what sites you visit and create strict AppArmor profiles for your browser, you may find that you will never have any other outbound connections logged, and in the interest of making your own life somewhat easier, you may decide to relax the outbound rules somewhat.

Even if you don't, you can be happy that you are in control of your own system and what's allowed in or out, and to me, that's part of the joy of Linux.

So far I haven't dive into AppArmor's complexity. I've not been able to manage to spare the necessary time to devote myself to the learning process it requires.
So I just practice some common sense measures when surfing, adblock plus, block third-party cookies and site data, don't allow any site to run JavaScript or any plugins without explicit permission.

By the way, allow me to question you something. Imagine that in future I want to permanently disable iptables and return to UFW, what I am to do?
Does flushing all my iptables rules and reinstalling and configure UFW enough? Or do I have to preform something else?
The reason I'm asking is that I didn't manage to find any vast information on this subject.

---


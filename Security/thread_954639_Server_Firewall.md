---
title: "Server Firewall"
date: 2008-10-21
forum: Security
---

### Post by craigp on 2008-10-21
Now i have a ubuntu web server with php mysql apache as well as a few other services like VNC, SSH, FTP etc..

I have a statefull firwall in between the ubuntu server and the internet connection. Do you guys recommend having the firewall turned on the server as well?  If so which one? I am fine with command line and have used iptables before.. Any recommendations?

Cheers

---

### Post by Dr Small on 2008-10-21
If you have a firewall between your modem and server (as you say) then having rules for your firewall on your server are not really needful. It can be useful if you plan to setup DenyHosts or Fail2Ban to block unauthorized attempts at your server, but otherwise, you shouldn't need to configure the firewall.

---

### Post by nubdora on 2008-10-21
Nevermind, misread.

---

### Post by Sarmacid on 2008-10-21
I would recommend setting up iptables on the server, I do that on all my ubuntu servers as an aditional protection and anyways, it's not like setting up iptables will hurt :P

Couple of nice places to check are:

[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables+tutorial](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables+tutorial)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Dr Small on 2008-10-21
> **Sarmacid said:**
> I would recommend setting up iptables on the server, I do that on all my ubuntu servers as an aditional protection and anyways, it's not like setting up iptables will hurt :P

Couple of nice places to check are:

[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables+tutorial](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables+tutorial)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
Iptables is installed by default, just with no rules applied.

---

### Post by koenn on 2008-10-21
> **Sarmacid said:**
> I would recommend setting up iptables on the server, I do that on all my ubuntu servers as an aditional protection and anyways, it's not like setting up iptables will hurt :P

Couple of nice places to check are:

[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables+tutorial](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables+tutorial)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

I disagree.
It's highly likely that the firewall rules on the server will just be duplicates of the rules on the actual firewall - so what passes the firewall (intentionally or not) will also pass the server fw rules - so in stead of extra protection you get a false sense of protection, plus the overhead of packet filtering and state checking on the server.

I'd rather do the following :
- have a perimeter firewall to filter traffic coming to or going out of the network (that would be the fw between the server and the modem)

- on the server, focus on protecting the exposed services by other means than packet filtering, stateful inspection, etc : think inetd, tcpwrapper, ... + solid user management + service-specific configuration (chrooted ftp ? Configure ssh to allow only from specific hosts, only execution of specific commands, use key pair authentication or certs i.s.o. passwords ? ...

that way, you really add extra protection.

---

### Post by Sarmacid on 2008-10-21
> **koenn said:**
> I disagree.
It's highly likely that the firewall rules on the server will just be duplicates of the rules on the actual firewall - so what passes the firewall (intentionally or not) will also pass the server fw rules - so in stead of extra protection you get a false sense of protection, plus the overhead of packet filtering and state checking on the server.
Having 2 different firewalls means they don't share the same vulnerabilities, thus would be much harder for an attacker to get a hold of the machine. However hardening the server by focusing on services would be an approach that should be taken either way.

---

### Post by david_lynch on 2008-10-21
I don't like using cpu cycles needlessly, so if there is already an
external firewall with the required rules, I let the system work.

To maxmimize security, just don't run unneeded services.

For extra protection, I use e.g tcp wrappers and other measures. For
instance, if ssh access is allowed through the firewall, I use tcp
wrappers (hosts.allow,deny) to narrow the list of IP addresses which are
allowed to connect, and edit the ssh allowed users list to narrow the
list of users allowed to connect via ssh.

For apache/php there are dos mitigation parameters, for postfix there
are various sanity checking parameters, tarpitting etc.

Disable all plain text auth, use pop3s, ftps, etc instead of their
unencrypted counterparts. That's just for a start. There are lots of
things you can do beyond the firewall itself, to enhance security.

---

### Post by koenn on 2008-10-21
> **Sarmacid said:**
> Having 2 different firewalls means they don't share the same vulnerabilities, thus would be much harder for an attacker to get a hold of the machine. 
Theoretically, yes.
In real life, you think you get 2 different firewalls but probably end up with different appliances both running BSD and Netfilter.
Besides that, If you don't allow external connections to the firewall, but only traffic passing through it and a maintenance interface from your secure lan, the danger of someone exploiting a vulnerability from the outside is rather small, I think. 

> **Sarmacid said:**
> However hardening the server by focusing on services would be an approach that should be taken either way.  
Yet most people tend to think security=firewall, more security=more firewalls - as is obvious from the OP. That's why I brought up the additional measures, which would complement a firewall way more effectively than a 2nd firewall would.

---

### Post by kevdog on 2008-10-21
There is no right answer on this discussion.  Whether to use iptables firewall or use other application such as fail2ban, denyhosts, or whether to configure each application individually with its given security options is a matter of debate.  No one is going to win this argument.  I prefer iptables since its the only program I need to modify for all listening services (and the more you write iptables rules the better you get), however this is definitely the right answer according to others.  Investigate each option and do what you feel the most comfortable with.

---

### Post by craigp on 2008-10-23
thanks guys.. i'll look at all the comments and see what i decide..  awesome how quick of a response you get on here

---


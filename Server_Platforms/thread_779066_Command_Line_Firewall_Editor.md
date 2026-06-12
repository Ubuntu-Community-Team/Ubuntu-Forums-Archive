---
title: "Command Line Firewall Editor?"
date: 2008-05-02
forum: Server Platforms
---

### Post by quietas on 2008-05-02
Is there anything out there for easy editing of IPTABLES in a command line editor? Some sort of tool like Firestarter, but at the command line rather than in a GUI?

Yes, yes, I've read the guides on using Iptables, but that is such an *** backwards way to set up a firewall. Some other firewall would be fine if there is an easier way to do it at the CLI on a server with no GUI. Webmin worked, but Ubuntu folks dislike it's internal messiness.

---

### Post by HermanAB on 2008-05-02
Webmin

---

### Post by ginjabunny on 2008-05-02
if you have server 8.04 it now comes with a new firewall called UFW which is command line driven - see [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

personally I use Shorewall which is config file driven (or use webmin), it takes a bit of work to set it up initially but is very good.

There are others but personally I've not tried them

---

### Post by liathus on 2008-05-02
> **quietas said:**
> Is there anything out there for easy editing of IPTABLES in a command line editor? Some sort of tool like Firestarter, but at the command line rather than in a GUI?

Yes, yes, I've read the guides on using Iptables, but that is such an *** backwards way to set up a firewall. Some other firewall would be fine if there is an easier way to do it at the CLI on a server with no GUI. Webmin worked, but Ubuntu folks dislike it's internal messiness.

Just make a file with permissions 700 in /usr/local/bin called firewall.

Then edit it with vi or nano or whatever, have it run by default at boot, and if you want to change anything, simply edit the file, and rerun the script, the flush command will start things over.

here is an example,

```
#!/bin/bash
#Clear existing firewall rules
/usr/local/bin/ipflush

#### DEFAULT POLICIES ##############
/sbin/iptables -P FORWARD DROP
/sbin/iptables -P OUTPUT ACCEPT
/sbin/iptables -P INPUT DROP
####################################


####################################
########## Input Rules #############
####################################

######### Needed for some local stuff to work ################
/sbin/iptables -A INPUT -i lo -j ACCEPT
##############################################################


#### DENY PRIVATE ADDRESSES ON PUBLIC INTERFACE ##############
/sbin/iptables -A INPUT -s 10.0.0.0/8 -i eth1 -j DROP 
/sbin/iptables -A INPUT -s 127.0.0.0/8 -i eth1 -j DROP 
/sbin/iptables -A INPUT -s 192.168.0.0/255.255.0.0 -i eth1 -j DROP
/sbin/iptables -A INPUT -s 172.16.0.0/12 -i eth1 -j DROP 
/sbin/iptables -A INPUT -s 240.0.0.0/5 -i eth1 -j DROP 
#############################################################


###DENY BASED ON ABUSE###

###############################################
####### PUBLIC SERVICES #######################
###############################################
#Allow Pings
/sbin/iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 2/s -j ACCEPT

#Allow FTP Services
/sbin/iptables -A INPUT -p tcp --dport 21 -j ACCEPT

#Allow DNS Services
/sbin/iptables -A INPUT -p udp --dport 53 -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 53 -j ACCEPT

#Allow WWW Services
/sbin/iptables -A INPUT -p tcp --dport 80 -j ACCEPT

#Allow Imap(s) Services
/sbin/iptables -A INPUT -p tcp --dport 143 -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 993 -j ACCEPT

#Allow Pop3 Services
/sbin/iptables -A INPUT -p tcp --dport 110 -j ACCEPT

#Allow SMTP(s) Services
/sbin/iptables -A INPUT -p tcp --dport 25 -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 465 -j ACCEPT

###############################################
####### REMOTE ADMIN RULES ####################
###############################################

#Allow SSH
/sbin/iptables -A INPUT -p tcp --dport 22 s some.ip.adress.here -j ACCEPT
#webmin
/sbin/iptables -A INPUT -p tcp --dport 10000 -s some.ip.adress.here -j ACCEPT


####################################
####### STATEFULL RULE #############
#Allow connection through that we started internall
/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
####################################


####################################
##### DEFAULT LOG RULE #############
#Log Everything Else
/sbin/iptables -A INPUT -j LOG --log-level warning --log-prefix "Unauthorized Network Access"
####################################
```

---


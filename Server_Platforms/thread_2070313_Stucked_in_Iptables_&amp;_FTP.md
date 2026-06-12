---
title: "Stucked in Iptables &amp; FTP"
date: 2012-10-12
forum: Server Platforms
---

### Post by xaidi1989 on 2012-10-12
:confused:   hey i am using ubuntu 12.4 LTS with 2 ethernets eth0 is external and eth1 is internal, I have tried so many iptables rules to allow only ftp service from that server only a few ports are allowed even port 80 is blocked because i am using squid on that gateway.
BUT no luck :( Please Help!!!!

---

### Post by CharlesA on 2012-10-12
Please wait at least 24 hours before bumping your thread if there have been no responses.

---

### Post by darkod on 2012-10-12
Is the ftp service running on that server or it needs to forward it to another machine?

If it's on that server, and you are using the default port 21, you just need to allow that port and the one below, like:

sudo iptables -A INPUT -i eth0 -p tcp --dport 20:21 -j ACCEPT

If you want to limit it to certan source IP, you will need to use the -s option too.

Give the above command a shot, if it works you can implement it in your permanent rules because running it from the command line is only temporary. After you reboot it's lost.

---

### Post by xaidi1989 on 2012-10-12
I want to allow network users to access any online ftp servers through that gateway.

---

### Post by xaidi1989 on 2012-10-12
Still Same

Status:	Connecting to XX.XX.XX.XX:21...
Status:	Connection established, waiting for welcome message...
Error:	Connection timed out
Error:	Could not connect to server
Status:	Resolving address of ftp.XXXXXXXX.com
Status:	Connecting to XX.XX.XX.XX:21...
Status:	Connection established, waiting for welcome message...

---

### Post by darkod on 2012-10-12
Of course it's the same, I said if you are running ftp on that server, which you are not. Only now you are explaining what you want to do.

So, this machine is only the gateway? Does the internet work correctly on your machines on the internal network or not?

It could only be a question of your iptables rules blocking the communication, or maybe you don't have it configured correctly as gateway.

So, step one is: Does the internet work on the machines on the LAN?

PS. And what are the iptables policies for the INPUT, FORWARD and OUTPUT chains?

---

### Post by xaidi1989 on 2012-10-12
Yes internet is working Perfectly, And here is the IPtables
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X

#FTP
iptables -A OUTPUT -o eth0 -p tcp --sport ftp -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport ftp-data -j ACCEPT

modprobe ip_conntrack_ftp
iptables -A INPUT -m helper --helper ftp -j ACCEPT

# Examine the state of a packet 
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#Turn on connection tracking
iptables -I FORWARD 1 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

# Setting default filter policy
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT

# Allow Established Connection
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables --append FORWARD --in-interface eth1 -j ACCEPT

# DROP everything and Log it
iptables -A INPUT -j LOG
#iptables -A FORWARD -j LOG
iptables -A INPUT -j DROP

---

### Post by darkod on 2012-10-12
If that machine is a gateway, usually you need a POSTROUTING rule which you don't seem to have. I think this is what might be missing.

Also, those FTP rules you have are worthless since they are in the OUTPUT chain, which means they apply to connection originating on the gateway and going out. They wouldn't apply to connections originating on your LAN computers and just going through the gateway.

Also, put the policy rules at top right after the flush rules and continue adding rules below. I don't see a point to set the policy in the middle.

Try adding something like this (I hope I'll get the syntax right):
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

That will make outgoing connections to include the public IP so that the reply knows how to go back to it. I think right now the ftp servers you are trying can't reach back.
Usually a gateway wouldn't even work without this rule.

---

### Post by xaidi1989 on 2012-10-12
Thanks man! now it is working.

---


---
title: "need to secure server - iptables basics"
date: 2011-08-20
forum: Security
---

### Post by 007casper on 2011-08-20
need to secure server - iptables basics

I wanted to secure the servers I am managing, and making sure no pest comes around.

I am actually hoping to make this thread into a great shell script that is a good start for iptables.  At the moment, this thread is work in progress.  There might be mistakes.  If you see any please let me know.  I want to make sure everything is proper before I run with it.

I have an application server, and a database server.  In a day or two, I am going to add another application server to the mix.
So, I would like to finish the iptables rules, before I roll out.

Again... Please, let me know if there are any errors.


overview
    INPUT - Holds rules for traffic directed at this server. 
    
    FORWARD - Holds rules for traffic that will be forwarding on to an IP behind this server (i.e. If this box serves as a firewall for other servers). 
    
    OUTPUT - Holds rules for traffic that is coming from this server out to the internet. 

    ACCEPT - Traffic is accepted for delivery. 

    REJECT - Traffic is rejected, sending a packet back to the sending host. 

    DROP - The traffic is dropped. Nothing is sent back to the sending host. 

I found a few iptable rules set.

for starters I have...```

#!/bin/bash
IPT="/sbin/iptables"

Main IP - Three way handshake is complete to establish traffic for eth0
# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A FORWARD -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT 

LAN IP - Three way handshake is complete to establish traffic for eth0:1
# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A FORWARD -i eth0:1 -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT

BAD GUYS (Block Source IP Address):
# iptables -A INPUT -s 172.34.5.8 -j DROP

NO SPAMMERS (notice the use of FQDN):
# iptables -A INPUT -s mail.spammer.org -d 10.1.15.1 -p tcp --dport 25 -j REJECT

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

MYSQL (Allow Remote Access To Particular IP):
# iptables -A INPUT -s 172.50.3.45 -d 10.1.15.1 -p tcp --dport 3306 -j ACCEPT
SSH:
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 22 -j ACCEPT

Sendmail/Postfix:
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 25 -j ACCEPT

FTP: (Notice how you can specify a range of ports 20-21)
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 20:21 -j ACCEPT

Passive FTP Ports Maybe: (Again, specifying ports 50000 through 50050 in one rule)
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 50000:50050 -j ACCEPT

HTTP/Apache/nginx
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 80 -j ACCEPT
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 8080 -j ACCEPT
SSL/Apache
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 443 -j ACCEPT

IMAP
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 143 -j ACCEPT

IMAPS
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 993 -j ACCEPT

POP3
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 110 -j ACCEPT

POP3S
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 995 -j ACCEPT

Any Traffic From Localhost:
# iptables -A INPUT -d 10.1.15.1 -s 127.0.0.1 -j ACCEPT

ICMP/Ping:
# iptables -A INPUT -d 10.1.15.1 -p icmp -j ACCEPT

GLOBAL Reject everything else to that IP:
# iptables -A INPUT -d 10.1.15.1 -j REJECT

Or, reject everything else coming through to any IP:
# iptables -A INPUT -j REJECT
# iptables -A FORWARD -j REJECT

```

You need to save to disk after you load shell script.  You can save to disk with....   
```
iptables-save
```
otherwise you will lose all your iptables rules.


To see what rulesets we currently have in place, execute:
```
iptables --list
```

If you want to delete your iptables set up, you can by using...
```
iptables --flush
```


question
from app server to database - on database server
/sbin/iptables -A INPUT -i eth0 -s 192.168.1.0/24 -p tcp --destination-port 3306 -j ACCEPT

lets say 192.168.1.49 is the application server IP. And the application server's public IP is 124.562.313.52 and I dont want to use eth0

eth0 124.562.313.52
eth0:1 192.168.1.49 
since, I am in VPS, I would like to lock it down to a specific lan ip, will this work?
/sbin/iptables -A INPUT -i 124.562.313.52 -s 192.168.1.49 -p tcp --destination-port 3306 -j ACCEPT

it looks a bit wrong.

sources for above iptables rule set
[http://www.5dollarwhitebox.org/wiki/index.php/Howtos_Basic_IPTables](http://www.5dollarwhitebox.org/wiki/index.php/Howtos_Basic_IPTables)
[http://www.howtoforge.com/linux_iptables_sarge](http://www.howtoforge.com/linux_iptables_sarge)
[http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html](http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html)
[http://ubuntuforums.org/showthread.php?t=1813000&highlight=dos+attack](http://ubuntuforums.org/showthread.php?t=1813000&highlight=dos+attack)

---

### Post by 007casper on 2011-08-20
before I used ufw... would there a be conflict with iptables setup?

ufw status on application server
```

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere
2222                       ALLOW       61.152.4.31 (my client IP)
Anywhere                   ALLOW       192.128.1.2 (database server)
```

I was checking this link out
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)


would this work? having ufw first, and then loading iptables.  Should I disable the ufw?  Do you see anything wrong with iptable rules above @ OP.

thank you.

---

### Post by 007casper on 2011-08-21
what if you have more than one ip address?  how does handshake work?
> 
Three handshake is complete to establish traffic.
# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A FORWARD -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# Configuration for eth0 and aliases

# This line ensures that the interface will be brought up during boot.
auto eth0 eth0:0 eth0:1

# eth0 - This is the main IP address that will be used for most outbound connections.
# The address, netmask and gateway are all necessary.
iface eth0 inet static
 address 12.411.533.79
 netmask 255.255.255.0
 gateway 12.411.533.1

# eth0:0
# This is a second public IP address.
#iface eth0:0 inet static
# address 12.24.98.54
# netmask 255.255.255.0

# eth0:1 - local IPs have no gateway.  They are not publicly routable, so only
# specify the address and netmask.
iface eth0:1 inet static
 address 192.168.546.147
 netmask 255.255.128.0


```

---

### Post by Dangertux on 2011-08-21
> **007casper said:**
> what if you have more than one ip address?  how does handshake work?


```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# Configuration for eth0 and aliases

# This line ensures that the interface will be brought up during boot.
auto eth0 eth0:0 eth0:1

# eth0 - This is the main IP address that will be used for most outbound connections.
# The address, netmask and gateway are all necessary.
iface eth0 inet static
 address 12.411.533.79
 netmask 255.255.255.0
 gateway 12.411.533.1

# eth0:0
# This is a second public IP address.
#iface eth0:0 inet static
# address 12.24.98.54
# netmask 255.255.255.0

# eth0:1 - local IPs have no gateway.  They are not publicly routable, so only
# specify the address and netmask.
iface eth0:1 inet static
 address 192.168.546.147
 netmask 255.255.128.0


```

The same way it would with only one. If you are designating interface in your rules, which you are, or destination. It will apply only to that interface or destination. So if you don't apply ESTABLISHED, RELATED to all interfaces/destinations you may find some problems when you add a default drop rule.

---

### Post by 007casper on 2011-08-21
```

Three way handshake is complete to establish traffic for eth0
# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A FORWARD -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT 

Three way handshake is complete to establish traffic for eth0:1
# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A FORWARD -i eth0:1 -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT 

```
is that correct?

---

### Post by Dangertux on 2011-08-21
> **007casper said:**
> ```

Three way handshake is complete to establish traffic for eth0
# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A FORWARD -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT 

Three way handshake is complete to establish traffic for eth0:1
# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A FORWARD -i eth0:1 -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT 

```is that correct?

Looks good :-)

---

### Post by 007casper on 2011-08-22
The sample above, 10.1.15.1 is the server IP right?

---

### Post by 007casper on 2011-08-22
I loaded the shell script to root folder, and chmod it to 0600.  Then, ran it on the terminal.

I got... 
> 
Warning: weird character in interface `eth0:1' (No aliases, :, ! or *).

---

### Post by spynappels on 2011-08-24
I just have 3 small things to add, not specific to rules though.

First, disable UFW, don't use them both at the same time.

Second, make the script interactive, so when the script runs it asks you whether you are installing an application server or a db server or whatever other servers you envisage running, and depending on the answer given apply different sets of rules.

Third, if this is on your VPS servers mentioned in other threads, I would suggest approaching this slightly differently. This is based on experience with VPS servers.
Connect each VPS to a VPN you set up using OpenVPN or similar.
Allow all traffic on the lo and tun0 (loopback and VPN tunnel interface)
Block everything inbound on the eth0 interface except for the port(s) you need such as 80 and/or 443 on the web/application server and 3306 for a MySQL server. For the MySQL server you could set up a rule which only allows connections into eth0 from the IPs of your application servers.

This makes the number of rules required much smaller, as all your FTP access etc can be done across your VPN, and if a third party needs to upload stuff, you can open a port temporarily.

It also makes your Internet facing interfaces more secure, and as the VPN connection is always initiated from the VPS, it will not be blocked, as long as you have the rule which allows CONNECTED and RELATED connections in.

---

### Post by 007casper on 2011-08-27
Thank you so much.

I already have the application server and mysql on a VPN.  

The database server only sees application server, and the other open port is for ssh.

The application server has 80, 443 and specified port for ssh.

I also filter IP addresses that tries to use other ports besides port 80 and 443 and block them through iptables every a few days. I would like to update the bad IP list everyday on the server, but having issues with iptables --flush.

When I want to update the bad IPs list on the iptables, I do 'iptables --flush' and update it with a new set of rules.  Then, the terminal on my computer (the client) side freezes.  You cant even type on the terminal.  Then, I think the server eats the dust. 

I figure maybe only terminal doesnt respond.  Then, I go to the site, and see that it is getting really slow to a point that it could time out.  So, I reboot the server.  

I know I can update only the new bad IPs. However, as far as I know the iptables follow a certain pattern. First, second... last etc.  Since, I dont know much about iptables, and how to insert the new rule in between a specific set.  I just update it on kate/gedit in order, iptables flush, and reload new set.

I am not using fail2ban, or any other application etc.  I am trying to keep the server to minimum essential applications.  I am not sure if there are much better alternatives to block bad IPs to protect the server.  However, I am getting a much lower number of bad IPs now.
At the moment, the traffic is going up steady, but bad IP list is not getting much bigger.  Hopefully, it will stay that way.

As you suggest, I will default to iptables, and disable ufw.

Is there any other way I could update iptables?  Such as start, stop, reload on iptables?  

thank you once again.

---

### Post by 007casper on 2011-08-31
When I do 'iptables --flush' the terminal freezes on the client site, and the website says 'The connection has timed out'.

Is there another way to delete/replace the old iptables rule set and insert new iptables rules without having the terminal freeze up?

---

### Post by spynappels on 2011-08-31
Is your default set to DROP?

That can lock you out if you are accessing the server through a ssh session.

I tend to set my default to ALLOW and just have the last rule in the chain set to DROP everything.

---

### Post by debd on 2011-09-02
just some resources on iptables

[http://openpdf.info/ebook/iptables-pdf.html](http://openpdf.info/ebook/iptables-pdf.html)
[http://www.frozentux.net/documents/iptables-tutorial/](http://www.frozentux.net/documents/iptables-tutorial/)

---

### Post by 007casper on 2011-09-03
I have DROP to block bad IPs, after three way handshake.  Here is the .sh file I am using.

Are you suggesting that I place bad IPs at the end of the file?  
> BAD GUYS (Block Source IP Address):
# iptables -A INPUT -s 172.34.5.8 -j DROP

On the original list I am using, I do have several hundred bad IPs on the list.  Maybe around 280 bad IPs.  The rule set below is just a sample.  Every a few days, I go through the logwatch and gather the IPs that are trying to access the server on different ports and block them.  I place the new bad IPs on the iptables rule set file, flush the old, and reload the new.

```

#!/bin/bash
IPT="/sbin/iptables"

Main IP - Three way handshake is complete to establish traffic for eth0
# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A FORWARD -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT 

LAN IP - Three way handshake is complete to establish traffic for eth0:1
# iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A FORWARD -i eth0:1 -m state --state RELATED,ESTABLISHED -j ACCEPT
# iptables -A OUTPUT -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT

BAD GUYS (Block Source IP Address):
# iptables -A INPUT -s 172.34.5.8 -j DROP

NO SPAMMERS (notice the use of FQDN):
# iptables -A INPUT -s mail.spammer.org -d 10.1.15.1 -p tcp --dport 25 -j REJECT

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

MYSQL (Allow Remote Access To Particular IP):
# iptables -A INPUT -s 172.50.3.45 -d 10.1.15.1 -p tcp --dport 3306 -j ACCEPT
SSH:
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 22 -j ACCEPT

Sendmail/Postfix:
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 25 -j ACCEPT

FTP: (Notice how you can specify a range of ports 20-21)
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 20:21 -j ACCEPT

Passive FTP Ports Maybe: (Again, specifying ports 50000 through 50050 in one rule)
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 50000:50050 -j ACCEPT

HTTP/Apache/nginx
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 80 -j ACCEPT
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 8080 -j ACCEPT
SSL/Apache
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 443 -j ACCEPT

IMAP
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 143 -j ACCEPT

IMAPS
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 993 -j ACCEPT

POP3
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 110 -j ACCEPT

POP3S
# iptables -A INPUT -d 10.1.15.1 -p tcp --dport 995 -j ACCEPT

Any Traffic From Localhost:
# iptables -A INPUT -d 10.1.15.1 -s 127.0.0.1 -j ACCEPT

ICMP/Ping:
# iptables -A INPUT -d 10.1.15.1 -p icmp -j ACCEPT

GLOBAL Reject everything else to that IP:
# iptables -A INPUT -d 10.1.15.1 -j REJECT

Or, reject everything else coming through to any IP:
# iptables -A INPUT -j REJECT
# iptables -A FORWARD -j REJECT

```

---


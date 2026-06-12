---
title: "Evolution can't download emails on server"
date: 2008-04-22
forum: Server Platforms
---

### Post by satimis on 2008-04-22
Hi folks,


Ubuntu 7.04 server amd64
Postfix 2.3.8
Evolution 2.22.1 (running on Archlinux)


Evolution can't download emails on server but can send mails via server


Settings:
Sending Email
Server Type: SMTP
Server: smtp.satimis.com
Type: Plain


Receiving Email
Server Type: POP
Server: pop3.satimis.com
Authentication Type
Password


On clicking Send/Receive, it doesn't popup "Enter Password for Personl" window

Remark:
having tried Server: pop.satimis.com
On clicking "Check for Supported Types" it only hangs there.


On Sending: clicking "Sent" it popup for Password.  After keying in password it sends mails.


However with same settings only changing "pop3.satimis.com" to "pop.ISP.com

Evolution can download mails on ISP server


Please advise where shall I check?  TIA


Edit:

$ apt-cache policy courier-base```

courier-base:
  Installed: 0.53.3-5ubuntu1
  Candidate: 0.53.3-5ubuntu1
  Version table:
 *** 0.53.3-5ubuntu1 0
        500 http://us.archive.ubuntu.com feisty/universe Packages
        100 /var/lib/dpkg/status

```


$ apt-cache policy courier-imap```

courier-imap:
  Installed: 4.1.1.20060828-5ubuntu1
  Candidate: 4.1.1.20060828-5ubuntu1
  Version table:
 *** 4.1.1.20060828-5ubuntu1 0
        500 http://us.archive.ubuntu.com feisty/universe Packages
        100 /var/lib/dpkg/status

```


$ apt-cache policy courier-maildrop```

courier-maildrop:
  Installed: 0.53.3-5ubuntu1
  Candidate: 0.53.3-5ubuntu1
  Version table:
 *** 0.53.3-5ubuntu1 0
        500 http://us.archive.ubuntu.com feisty/universe Packages
        100 /var/lib/dpkg/status

```



B.R.
satimis

---

### Post by satimis on 2008-04-22
Hi folks,


It is the rules of iptables on the remote Mail Server preventing Evolution downloading mails.


# cat /etc/rc.local```

# INPUT

# Set the default policy to drop
iptables -P INPUT DROP

# Allow existing connections to continue
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A INPUT -i lo -j ACCEPT

# allow all VMware MUI HTTP connections in from anywhere
iptables -A INPUT -p tcp --dport 8222 -j ACCEPT

# allow all VMware MUI HTTPS connections in from anywhere
iptables -A INPUT -p tcp --dport 8333 -j ACCEPT

# allow all VMware Authorization Daemon connections in from anywhere
iptables -A INPUT -p tcp --dport 902 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -p tcp --dport 25 -j ACCEPT   # add allowing incoming mails 20080307

# Allow ssh from workstation local IP
iptables -A INPUT -s 192.168.0.52 -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -s 192.168.0.2 -p tcp --dport 22 -j ACCEPT

# Allow ssh from workstation public IP
#iptables -A INPUT -s 220.232.213.178 -p tcp --dport 22 -j ACCEPT

iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -j LOG


# OUTPUT

# Set the default policy to drop
iptables -P OUTPUT ACCEPT

# Allow existing connections to continue
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A OUTPUT -d 127.0.0.1 -j ACCEPT

# Allow DNS requests out
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT

iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT


```

After stopping iptables running Evolution can download mails on the Mail Server.


Please advise what rule shall I add to allow Evolution downloading mail.  

Router IP of Archlinux - 192.168.0.52


TIA


B.R.
satimis

---


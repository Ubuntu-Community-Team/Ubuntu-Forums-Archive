---
title: "[SOLVED] Webmin iptables"
date: 2007-07-12
forum: Server Platforms
---

### Post by Footballkid4 on 2007-07-12
I have been using webmin to administer quite a few features on my Ubuntu server.  Recently, while trying to get a good firewall up and running, I realized a few setbacks in the webmin iptables configuration.  If I set the default action to DROP for **incoming** packets, and allow TCP connections with a destination port of 80 (since I have an http server), I can no longer conenct to the internet.

I am trying to setup firewall rules for the following:
HTTP, HTTPS, FTP, POP3, POP3 (SSL/TLS), IMAP, IMAP (SSL/TLS), SMTP, SSH

Since that is what is currently installed and function on the server.  However, as stated, when I change the default action for incoming packets to drop, the connection to my internet breaks.

As a way around this, I have been using Firestarter to configure my firewall, but I'm really starting to hate that program seeing that it has issues auto-starting...plus I'd rather not keep a program if I really don't need it installed.  What I was wondering is...does anyone know the solution to the webmin issue?  And if not, is there a simple way to remove firestarter but keep the iptables configuration that it has set.

(By the way, I have tried visudo and added
ALL ALL = NOPASSWD: /etc/init.d/firestarter, and I can run /etc/init.d/firestarter start even from a non-administrative account, but it still doesn't load at boot).

---

### Post by simonn on 2007-07-12
IMHO, I find it easier to use iptables directly from a shell script.

Probably what is happening is you are dropping incoming packets completely. If you do this, then **nothing** can get through. You need to allow established and related packets through.

The script below should give you some ideas. Please ask any questions you have on it.

```

#!/bin/sh

# Set default policies for all three default chains
/sbin/iptables -P INPUT DROP
/sbin/iptables -P FORWARD DROP
/sbin/iptables -P OUTPUT ACCEPT

# Enable free use of loopback interfaces
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A OUTPUT -o lo -j ACCEPT

# All TCP sessions should begin with SYN
/sbin/iptables -A INPUT -p tcp ! --syn -m state --state NEW -j DROP

# Accept established and related inbound packets
/sbin/iptables -A INPUT -j ACCEPT -m state --state ESTABLISHED,RELATED

# Allow SSH from LAN
/sbin/iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 22 -j ACCEPT

# Allow NTP from LAN
/sbin/iptables -A INPUT -p udp -s 192.168.1.0/24 --dport 123 -j ACCEPT

# Allow HTTPS access to Apache from anywhere
/sbin/iptables -A INPUT -p tcp --dport 443 -j ACCEPT

```

---

### Post by Footballkid4 on 2007-07-12
That solved it, thanks.  I just started with linux about a week ago, and managed to get 90% of my servers running on my own...but a few things held me back.

I know it's easier to do this through command line but for now I'm trying to keep everything I do centralized in Webmin because it just provides a much easier way to manage things.

Again, thank you.

---


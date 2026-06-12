---
title: "Postfix not accepting outgoing mail on 18.04"
date: 2018-07-28
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2018-07-28
I am setting up a new 18.04 server. One of the functions of this server is to send outgoing mail from our local network. 

I have installed and configured postfix just like postfix on the 16.04 server it will be replacing. The 16.04 server was built a long time ago on an old  version of Ubuntu which has been continuously upgraded. The 18.04 server is a new install of the server iso with stuff added. dpkg reports that postfix is installed and configured.

I ran dpkg-reconfigure and it generated this main.cf
I updated the firewall with 
```
# ufw allow Postfix
```
I reloaded postfix with
```
# service postfix reload
```

```

# postfix main.cf
# for hamlet.no.steinmetznet.com
# outgoing mail server
smtpd_use_tls = no
compatibility_level = 2
mynetworks = 192.168.1.0/24 127.0.0.0/8
relay_domains =
mailbox_size_limit = 0
message_size_limit = 0
inet_interfaces = all
inet_protocols = ipv4

myorigin = /etc/mailname
mydestination =
relayhost =
recipient_delimiter =
```

My other postfix install that works has this main.cf

```
# postfix main.cf
# for hamlet.no.steinmetznet.com
# outgoing mail server
smtpd_use_tls = no
compatibility_level = 2
mynetworks = 192.168.1.0/24 127.0.0.0/8
relay_domains =
mailbox_size_limit = 0
message_size_limit = 0
inet_interfaces = all
inet_protocols = ipv4
```

I wonder if the server iso requires something more to allow postfix to receive and forward messages to the Internet.

When I try to send an email from a windows machine using SeaMonkey I get this error

```
Sending of the message failed.
The message could not be sent because connecting to Outgoing server (SMTP) 192.168.1.1 failed. The server may be unavailable or is refusing SMTP connections. Please verify that your Outgoing server (SMTP) settings are correct and try again.
```

---

### Post by lisati on 2018-07-28
*Thread moved to **Server Platforms**.*

Do you have your server set to a static (or reserved) IP address on your router?

---

### Post by rsteinmetz70112 on 2018-07-29
> **lisati said:**
> *Thread moved to **Server Platforms**.*

Do you have your server set to a static (or reserved) IP address on your router?

The server is set to a static private ip address 192.168.1.1  and I have that IP translated to a public IP address via iptables in 16.04 and had added the same rules in 18.04 in firewalld. However checking firewalld the rules were somehow deleted. But I think it should still work. The router should route all traffic from the private IP address to the Internet. 

When I telnet into the new server on port 25, I get no response at all. The old server responds properly with a greeting.

---

### Post by rsteinmetz70112 on 2018-08-04
I found the solution. I had used a ufw command instear of firewalld to open the firewall.

The correct commands are

```
firewall-cmd --permanent --add-service=smtp
firewall-cmd --reload
firewall-cmd --list-all
```

---


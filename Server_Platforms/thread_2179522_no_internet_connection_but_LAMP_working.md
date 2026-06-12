---
title: "no internet connection but LAMP working"
date: 2013-10-08
forum: Server Platforms
---

### Post by Jikax on 2013-10-08
I got a working server running on ubuntu 12.04.
I can access through ssh,ftp and http just fine.
Both from LAN and WAN.

But i cannot access the internet when I'm working on the server itself.
"sudo apt-get update" gives me could not find errors.
a ping to google.com gives me no results.
Also a ping to another lan machine gives me no results.
A ping from another lan machine to the the server also gives me timeout error.
But when i enter the same ip in a browser i just get the normal expected website.

I also cannot ping any address when i am connected via ssh, which does work just fine.

The server is behind a router with dhcp enabled and with a virtual server setup. 
port 80,21 and 22 are forwarded to the server's static ip.

any idea what i did wrong?

---

### Post by Lars Noodén on 2013-10-08
Did you crank down the packet filter too much?  What does UFW or iptables say?

```

sudo ufw status

```

---

### Post by SeijiSensei on 2013-10-09
Some ISPs block inbound traffic on ports 80 and 25 to enforce the usual "no servers" rule on residential connections.  If you turn off port forwarding for port 80 and look at your router from a remote location with a web browser, what happens?

---

### Post by Jikax on 2013-10-11
It gave me this: 

@ubuntu-server:/var/www$ sudo ufw status
WARN: Dubbel profiel 'Dovecot POP3', laatst gevonden wordt gebruikt
WARN: Dubbel profiel 'Dovecot Secure POP3', laatst gevonden wordt gebruikt
WARN: Dubbel profiel 'Dovecot IMAP', laatst gevonden wordt gebruikt
WARN: Dubbel profiel 'Dovecot Secure IMAP', laatst gevonden wordt gebruikt
Status: inactief

---


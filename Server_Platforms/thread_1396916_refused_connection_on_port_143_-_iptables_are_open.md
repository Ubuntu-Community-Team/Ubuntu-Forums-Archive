---
title: "refused connection on port 143 - iptables are open"
date: 2010-02-02
forum: Server Platforms
---

### Post by R.Bucky on 2010-02-02
I am configuring an internal only IMAP server for archival emails. I am absolutely baffled why my connection is being refused. UFW is disabled and IPTABLES has a rule to allow all connections on 143 and 993. When I telnet this response is given:
```
telnet localhost 143
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```
Even nmap shows the port closed. Here is my iptables rule:
[HTML]-A ufw-user-input -p udp -m udp --dport 143 -j ACCEPT [/HTML]
Help a guy out?

---

### Post by terazen on 2010-02-02
Your services are started?

---

### Post by R.Bucky on 2010-02-02
Yes, postfix and dovecot services are running; I just double-checked.

---

### Post by Rich78 on 2010-02-02
You did save the new iptables rules?

/etc/init.d/iptables save

Did you restart the services after changing the iptables?

---

### Post by greenstream on 2012-12-10
Hi all, 
Im configuring mail server with postfix+dovecot on ubuntu 12.04
my netstat -tap don't show port 143 is listenning, only port 25 is listenning. So I cannot browse imap mails using thunderbird client app - connection is refused.
I opened port 143 at gateway/router
I tried to open with firewall
> sudo iptables -A INPUT -p tcp --dport 143 -j ACCEPT
but it 's still nothing happen.

Please help,
Thank you!

I restarted after each changing anything
I set > listen = *,[::] on dovecot, too
and > protocols = imap

---

### Post by greenstream on 2012-12-11
> **greenstream said:**
> Hi all, 
Im configuring mail server with postfix+dovecot on ubuntu 12.04
my netstat -tap don't show port 143 is listenning, only port 25 is listenning. So I cannot browse imap mails using thunderbird client app - connection is refused.
I opened port 143 at gateway/router
I tried to open with firewall

but it 's still nothing happen.

Please help,
Thank you!

I restarted after each changing anything
I set  on dovecot, too
and
sorry, I found my problem. 
Dovecot service start failed b.c config file is wrong.
/etc/init.d/dovecot status show dovecot is stop/waiting.

---


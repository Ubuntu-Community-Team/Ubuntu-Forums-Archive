---
title: "mail server can only send - not receive mail"
date: 2012-01-14
forum: Server Platforms
---

### Post by kingair_six on 2012-01-14
hey folks,

recently I have been trying to reconfigure my server so as to provide an email-system for my business and customers (currently using 2 different domains). I used the following manual which (though in German) should give you an idea of what I was trying to do. [http://wiki.nefarius.at/linux/der_perfekte_mail-server]("http://wiki.nefarius.at/linux/der_perfekte_mail-server")

basically: using postfix/dovecot with postfix admin and mysql to provide a versatile setup so I can easily add/manage mail addresses. 

the problem: webmail works for sending emails, yet I cannot connect to the server via thunderbird (or any other mail prog.) also, I cannot receive mails, even though I do not get "mailer daemon" errors when trying to send to it.

any ideas? I am completely clueless, as I am not in any way experienced in setting up mail services (yeah, please do not tell me to drop it 'cause I am not qualified, everybody has to try new things eventually).

thx for any input:)

kingair_six

---

### Post by HermanAB on 2012-01-15
Do you have a server account with your ISP?  If not, then they will block port 25.
Do you have a Domain Name registered and a DNS entry with A, MX and PTR definitions?

---

### Post by kingair_six on 2012-01-15
the server is running in a datacenter, rented from a well-known German hosting company, so everything does check out - actually, my previous mail setup worked.

---

### Post by SeijiSensei on 2012-01-16
Check the configurations for your servers and make sure that the daemons are not bound to the localhost interface (127.0.0.1).  Many daemons listen only to localhost by default for security reasons.  

If the commands 

telnet localhost 25
telnet localhost 110
telnet localhost 143

(smtp, pop3, and imap respectively) all work, but their equivalents replacing "localhost" with your external address all fail, the servers are bound to the localhost interface.  You'll need to edit their configurations to listen on the public IP address as well.

---

### Post by jsra on 2012-01-16
Hi,
these two outputs could help solving the problem. Are you sure that no firewall or something is blocking you?
```
netstat -aunt
```
```
cat /var/log/mail.log
```

---

### Post by dchen on 2012-08-03
> **SeijiSensei said:**
> Check the configurations for your servers and make sure that the daemons are not bound to the localhost interface (127.0.0.1).  Many daemons listen only to localhost by default for security reasons.  

If the commands 

telnet localhost 25
telnet localhost 110
telnet localhost 143

(smtp, pop3, and imap respectively) all work, but their equivalents replacing "localhost" with your external address all fail, the servers are bound to the localhost interface.  You'll need to edit their configurations to listen on the public IP address as well.

Can you more detail about or examples of how to "You'll need to edit their configurations to listen on the public IP address as well" ? I might fall into the same situation that CAN'T receive mail in server from external but outgoing mails (internal or external) were fine.  thx.

---

### Post by SeijiSensei on 2012-08-03
The moderators usually prefer that you start a new thread.  In the meantime, read [this](http://www.postfix.org/BASIC_CONFIGURATION_README.html#inet_interfaces).

---


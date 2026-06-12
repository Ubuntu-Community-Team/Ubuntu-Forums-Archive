---
title: "Seeking advice on setup Evolution"
date: 2007-11-14
forum: Server Platforms
---

### Post by satimis on 2007-11-14
Hi folks,


Ubuntu 7.04 desktop


I'm now configuring Evolution to download mails on my own mail server (under testing).  I'll use ISP's mail server sending mails.  My mail server has not been fully configured.  Now it can receive mails.  I haven't setup "send mail" yet.  However mails can be sent via telnet on the mail server.


Mail Server
OS - Ubuntu 7.04 server amd64
Postfix 2.3.8
ethernet IP - 192.168.0.10

Workstation
ethernet IP -192.168.0.11


Please shed me some light on following points to complete "Evolution Setup Assistant" ;

Receiving Email
Server Type - POP ?
Configuration -> Server [What shall I put in this box] ?

Sending Email
Server Type - SMTP ?
Server Configuration -> Server [What shall I enter on this box]

Authentication
Type - login ??? [Check for Supported Type]


TIA


B.R.
satimis

---

### Post by ddrichardson on 2007-11-15
The address of the mail server, either the IP address 192.168.0.10 or it's DNS name. Click "Check supported types" next, then select which ever aren't crossed out.

---

### Post by satimis on 2007-11-15
> **ddrichardson said:**
> The address of the mail server, either the IP address 192.168.0.10 or it's DNS name. Click "Check supported types" next, then select which ever aren't crossed out.
Thanks for your advice.


$ hostname
mail

$ hostname -f
mail.satimis.com

Shall I use just "mail" or the full name "mail.satimis.com"?


Besides, the mail server and the workstation are connected via router. Do I need adding the NIC IP address of the mail server after the hostname?


Furthermore can the workstation send mails via the mail server directly without using ISP's mail server? If YES, please advise what settings shall I use? Thanks.

The mail server can send mails with telnet command without going through ISP's mail server.


I'm not very clear here.  On the mail server to read mails on user-A's Maildir I need to login user-A with its password. On workstation whether it is the same. To read user-A's mail I need to login with its password? It is not necessary creating an user-A a/c on workstation.


TIA


Edit:


Problem solved.


Evolution setting:-

1)
via mail server on Internet

Outgoing/Incoming
mail.satimis.com


2)
via mail server on Intranet
Outgoing/Incoming
192.168.0.10

(the NIC IP address)


Previously I was confused by ISP's settings:-

Incoming;
pop.isp.com

Outgoing;
smtp.isp.com

I was playing around on that base.


I suppose they have 2 mail servers, Outgoing and Incoming, with hostname as pop.isp.com and smtp.isp.com respectively???  


Thanks


B.R.
satimis

---


---
title: "postfix can some look at my main.cf  and help me out"
date: 2009-02-05
forum: Server Platforms
---

### Post by sfuller on 2009-02-05
cant sent mail outside domain
smtpd_tls_cert_file = /etc/ssl/serts/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/serts/ssl-cert-snakeoil.pem
smtpd_use_tls=yes
myhostname = mail.example.net
alias_maps = hash:/stc/aliases
moorigin = example.net
mydestination = mail.example.net, localhost.example.net, , localhost, example.net

relayhost = 
mynetworks = 127.0.0.0/8, 173.10.47.***/29
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_recipients_restrictions = permit_mynetworks
smpt_tls_security_level = may
smptd_tls_security_level = may
smtpd_tls_loglevel = 1

i have the static defaulf gatway address for mynetwork in the mynetworks= 

in the log i get this
mail posfix/smtpd[9680]:NOQUEUE: reject: RCPT from unknown[10.1.10.11] 554 5.7.1 <sfuller@example.com> relay access denied; from <sfuller@example.net> to =<katrina@comcast.net> proto=ESMTP helo=<katrinafd0cc48>

this is hapening when trying to send mail outside of the network from alaptop from behind the static ip of the  gateway and my mail client is outlook 2003

---

### Post by gombadi on 2009-02-05
> 
mydestination = mail.example.net, localhost.example.net, , localhost, example.net
mynetworks = 127.0.0.0/8, 173.10.47.***/29


and

> 
RCPT from unknown[10.1.10.11] 554 5.7.1 <sfuller@example.com> relay access denied; from <sfuller@example.net> to =<katrina@comcast.net>


The log message tells me that postfix had a connection from 10.1.10.11. That ip range is not in its mynetworks list so it will only deliver email to domains in the mydestination list.

The email postfix received was from [email]sfuller@example.net[/email] and was going to [email]katrina@comcast.net[/email]. As comcast.net is not in the mydestinations list postfix knows it has to relay messages to get to the destination. It looks at the source 10.1.10.11 and says that ip range is not in mynetworks so it correctly says Relay access denied.

My guess is that you external ip address is in the 173.10.x.y range and your internal network is using 10.x.y.z ip addresses. If that is the case the you need to change the 173.10.47.***/29 in mynetworks to 10.1.10.0/24 or whatever your network is and try again.

---

### Post by sfuller on 2009-02-05
> **gombadi said:**
> and



The log message tells me that postfix had a connection from 10.1.10.11. That ip range is not in its mynetworks list so it will only deliver email to domains in the mydestination list.

The email postfix received was from [email]sfuller@example.net[/email] and was going to [email]katrina@comcast.net[/email]. As comcast.net is not in the mydestinations list postfix knows it has to relay messages to get to the destination. It looks at the source 10.1.10.11 and says that ip range is not in mynetworks so it correctly says Relay access denied.

My guess is that you external ip address is in the 173.10.x.y range and your internal network is using 10.x.y.z ip addresses. If that is the case the you need to change the 173.10.47.***/29 in mynetworks to 10.1.10.0/24 or whatever your network is and try again.

thank you it makes sense know but i still dont understand how the ip is come up 10.1.10.1 i have comcast with a four port gateway  the mail server is in one port of the gateway the rest of the net work is hooked to a linksys router the router is handing out interal address 192.168.1.100/50 so where is the 10.1.10.0 coming from i whent on one of the computers in one the net work and whent to the whatsmyip.com and i get the address of the static gate way does ? so i guessing i gos to the router passes though the router get to the gateway and redirects to the server never maks it to the net to get the static ip of the gateway

---

### Post by sfuller on 2009-02-06
thank you gombadi it know work my comcast gateway was reassigning ip after it got pass my linksys router 

you are the man!!

---


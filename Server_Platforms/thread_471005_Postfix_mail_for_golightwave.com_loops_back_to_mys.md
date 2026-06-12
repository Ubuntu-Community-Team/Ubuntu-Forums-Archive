---
title: "Postfix: mail for golightwave.com loops back to myself"
date: 2007-06-11
forum: Server Platforms
---

### Post by vmikalinis on 2007-06-11
Hi All, 

I'm hoping someone has dealt with this before,  my email server works perfectly except with this one domain.  Noone can email them.  The server is postfix/cyrus/spamassasin/mysql.  I'm not sure if this domain can be whitelisted somehow or if that is the problem.  Someone please help. 

I get the message:

Final-Recipient: rfc822; [email]info@golightwave.com[/email]
Action: failed
Status: 5.0.0
Diagnostic-Code: X-Postfix; mail for golightwave.com loops back to myself


The mail log gives a very similar message.

---

### Post by Mr. C. on 2007-06-12
Is this your domain?

If so, show output of postconf -n .

If not, this would be their configuration problem.  Their MX records show:

$ host golightwave.com                   
golightwave.com has address 209.35.250.41
golightwave.com mail is handled by 20 mail.golightwave.com.
golightwave.com mail is handled by 10 mail.lightwavemanagement.com.

mail.lightwavemanagement.com is NXDOMAIN, so they are likely using unlisting as an anti-spam technique.

MrC

---

### Post by vmikalinis on 2007-06-12
It's strange because it's like the email never even goes out, the user immediately has the error in the mailbox when they click send.  Yes the problem is when we send emails to another company " golightwave.com" , everyone else is fine.  

Here is the output of postconf  -n:

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
header_checks = regexp:/etc/postfix/header_checks
mailbox_size_limit = 0
mailbox_transport = cyrus
message_size_limit = 20480000
mydestination = persephone, thisdomain, localhost.localdomain, localhost,     domain.net, otherdomain.com, anotherdomain.com, anotherdomain.com,     anotherdomain.net **(changed for security)**
myhostname = another.net **(changed for security)**
mynetworks = 127.0.0.0/8 10.0.0.0/24
recipient_delimiter = +
relayhost =
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = hash:/etc/postfix/access,   check_client_access hash:/etc/postfix/rbl-whitelist,    permit_mynetworks,         reject_unauth_pipelining,        reject_rbl_client zen.spamhaus.org,       reject_unauth_destination
smtpd_recipient_restrictions = permit_mynetworks,        reject_non_fqdn_sender,        reject_non_fqdn_recipient,        reject_unauth_pipelining,        reject_unauth_destination
smtpd_sender_restrictions = hash:/etc/postfix/access-sender,        reject_unauth_pipelining,        reject_non_fqdn_sender,        reject_non_fqdn_recipient,        reject_invalid_hostname
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual.cf



This was set up by the former network admin and it is also hosting a few websites as you can see.  I was assuming that I need to add golightwave.com to some "allowed" list somewhere but I'm not sure.  This server has been working for like 2 years so it's not a new config.  I have been here 2 months and this is the first problem I have seen.

---

### Post by vmikalinis on 2007-06-12
If I do an nslookup for golightwave.com , I get 

root :/etc # nslookup golightwave.com


Server:         127.0.0.1
Address:        127.0.0.1#53

Non-authoritative answer:
Name:   golightwave.com
Address: 209.35.250.41

---

### Post by MJN on 2007-06-12
To clarify a few things you are saying golightwave.com is nothing to do with you? That is, you don't handle its mail or anything? They are purely an independent third party? And you're not 71.40.141.26 (the A record of one of their MX records)?
 
(By the way, it makes diagnosis much more difficult when you obfuscate your domains, not least given that all too often the error is in the config which then gets hidden!)
 
Mathew

---

### Post by vmikalinis on 2007-06-12
ok here is the full postconf -n  and yes they are an outside company having nothing to do with us.  Just our user wanting to send them an email.  It never gets out , immediately bounces.

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
header_checks = regexp:/etc/postfix/header_checks
mailbox_size_limit = 0
mailbox_transport = cyrus
message_size_limit = 20480000

mynetworks = 127.0.0.0/8 10.0.0.0/24
recipient_delimiter = +
relayhost =
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = hash:/etc/postfix/access,   check_client_access hash:/etc/postfix/rbl-whitelist,    permit_mynetworks,         reject_unauth_pipelining,        reject_rbl_client zen.spamhaus.org,       reject_unauth_destination
smtpd_recipient_restrictions = permit_mynetworks,        reject_non_fqdn_sender,        reject_non_fqdn_recipient,        reject_unauth_pipelining,        reject_unauth_destination
smtpd_sender_restrictions = hash:/etc/postfix/access-sender,        reject_unauth_pipelining,        reject_non_fqdn_sender,        reject_non_fqdn_recipient,        reject_invalid_hostname
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual.cf





It's strange, it is my understanding that the error indicates golightwave.com is being resolved as 127.0.0.1, but no other domain is having this problem.  Is the firewall possibly dissallowing or something?

---

### Post by MJN on 2007-06-12
Hmm... And you get the same DNS response (from **dig golightwave.com mx**) as the rest of us?
 
```

<<>> DiG 9.2.3 <<>> @dns1.menandmice.com golightwave.com MX  
;; global options: printcmd 
;; Got answer: 
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37971 
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 4, ADDITIONAL: 1 
 
;; QUESTION SECTION: 
;golightwave.com. IN MX 
 
;; ANSWER SECTION: 
golightwave.com. 452 IN MX 20 mail.golightwave.com.   
golightwave.com. 452 IN MX 10 mail.lightwavemanagement.com.   
 
;; AUTHORITY SECTION: 
golightwave.com. 83252 IN NS ns2.mydomain.com.   
golightwave.com. 83252 IN NS ns3.mydomain.com.   
golightwave.com. 83252 IN NS ns4.mydomain.com.   
golightwave.com. 83252 IN NS ns1.mydomain.com.   
 
;; ADDITIONAL SECTION: 
mail.golightwave.com. 452 IN A 71.40.141.26   
 
;; Query time: 213 msec 
;; SERVER: 217.151.171.7#53(dns1.menandmice.com) 
;; WHEN: Tue Jun 12 14:45:58 2007 
;; MSG SIZE rcvd: 192
```
 
..and from **dig mail.lightwavemanagement.com A**
 
```

<<>> DiG 9.2.3 <<>> @dns1.menandmice.com mail.lightwavemanagement.com A  
;; global options: printcmd 
;; Got answer: 
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 39118 
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0 
 
;; QUESTION SECTION: 
;mail.lightwavemanagement.com. IN A 
 
;; AUTHORITY SECTION: 
com. 900 IN SOA a.gtld-servers.net. nstld.verisign-grs.com. 1181659404 1800 900 604800 900   
 
;; Query time: 286 msec 
;; SERVER: 217.151.171.7#53(dns1.menandmice.com) 
;; WHEN: Tue Jun 12 14:49:52 2007 
;; MSG SIZE rcvd: 119
```
 
I'm scraping the barrel now... Maybe wait for Mr C's return... ;)
 
Mathew

---

### Post by vmikalinis on 2007-06-12
Here is mine:

; <<>> DiG 9.2.4 <<>> golightwave.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47379
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 4

;; QUESTION SECTION:
;golightwave.com.               IN      A

;; ANSWER SECTION:
golightwave.com.        3600    IN      A       209.35.250.41

;; AUTHORITY SECTION:
golightwave.com.        2659    IN      NS      ns1.mydomain.com.
golightwave.com.        2659    IN      NS      ns2.mydomain.com.
golightwave.com.        2659    IN      NS      ns3.mydomain.com.
golightwave.com.        2659    IN      NS      ns4.mydomain.com.

;; ADDITIONAL SECTION:
ns1.mydomain.com.       59963   IN      A       64.94.117.213
ns2.mydomain.com.       59963   IN      A       64.94.31.67
ns3.mydomain.com.       59963   IN      A       66.150.161.137
ns4.mydomain.com.       59963   IN      A       63.251.83.74

;; Query time: 47 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Jun 12 10:50:25 2007
;; MSG SIZE  rcvd: 209

---

### Post by MJN on 2007-06-12
You missed the **MX** option (also try the second command that I edited in)
 
Mathew

---

### Post by vmikalinis on 2007-06-12
; <<>> DiG 9.2.4 <<>> golightwave.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45638
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 4, ADDITIONAL: 5

;; QUESTION SECTION:
;golightwave.com.               IN      MX

;; ANSWER SECTION:
golightwave.com.        3600    IN      MX      20 mail.golightwave.com.
golightwave.com.        3600    IN      MX      10 mail.lightwavemanagement.com.

;; AUTHORITY SECTION:
golightwave.com.        1392    IN      NS      ns1.mydomain.com.
golightwave.com.        1392    IN      NS      ns2.mydomain.com.
golightwave.com.        1392    IN      NS      ns3.mydomain.com.
golightwave.com.        1392    IN      NS      ns4.mydomain.com.

;; ADDITIONAL SECTION:
mail.golightwave.com.   3600    IN      A       71.40.141.26
ns1.mydomain.com.       58696   IN      A       64.94.117.213
ns2.mydomain.com.       58696   IN      A       64.94.31.67
ns3.mydomain.com.       58696   IN      A       66.150.161.137
ns4.mydomain.com.       58696   IN      A       63.251.83.74

;; Query time: 58 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Jun 12 11:11:32 2007
;; MSG SIZE  rcvd: 271


**and **


root@persephone:/etc # dig mail.lightwavemanagement.com A

; <<>> DiG 9.2.4 <<>> mail.lightwavemanagement.com A
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 17204
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.lightwavemanagement.com.  IN      A

;; AUTHORITY SECTION:
com.                    900     IN      SOA     a.gtld-servers.net. nstld.verisign-grs.com. 1181660996 1800 900 604800 900

;; Query time: 309 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Jun 12 11:12:46 2007
;; MSG SIZE  rcvd: 122

---

### Post by vmikalinis on 2007-06-12
Hi and thanks to everyone that was helping me troubleshoot this,  

I've sent two test emails and it now seems to be working.  I'm not sure what changed.  Is it possible that the "digs" could have added something to dns?  I wish I knew why it was working in case the issue comes up in the future, but I'm glad that it's fixed.

---

### Post by Mr. C. on 2007-06-12
No, they changed their DNS configuration and fixed their problem:

host golightwave.com
golightwave.com has address 209.35.250.41
golightwave.com mail is handled by 10 mail.golightwave.com.

Your DNS servers updated themselves once their cache entries expired (controlled by golightwave's DNS servers).

MrC

---

### Post by MJN on 2007-06-12
Do you know why the NXDOMAIN of the now-deleted MX record would've produced the 'mail loops back to myself' error?

Mathew

---

### Post by Mr. C. on 2007-06-12
I connected to their site last night.  The machine announced itself as mail.lightwavemanagement.com.

When a mail server attempts to send mail to an MX, it does so using the higest priority MX.  If it finds that the MX is its own hostname, or results in a loop, that error message results.  This can happen when the mail server is not made aware of its own name for either a virtual or local domain.

MrC

---

### Post by MJN on 2007-06-12
But in this case mail.lightwavemanagement.com is not the posters hostname, or have I misunderstood?

Mathew

---

### Post by Mr. C. on 2007-06-12
The golightwave server accepted the email.  Then it bounced back a failure DSN, as it was unable to deliver the mail.

It would be more instructive if the OP posted postfix's initial delivery and the DSN log entries.

MrC

---

### Post by MJN on 2007-06-12
Ah, okay, I see. The OP mentioned the error happened immediately suggesting (to me at least) a local issue but I guess things were just happening very quickly.

Thanks for the info.

Mathew

---


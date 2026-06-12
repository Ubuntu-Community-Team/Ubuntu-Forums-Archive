---
title: "POSTFIX :  myhostname = smtp.$mydomain ?"
date: 2016-09-04
forum: Server Platforms
---

### Post by dmlinux on 2016-09-04
Hello
I have a Ubuntu 16.04 LTS server with several IPs and several sites (domains)

I want to send (SMTP) emails as :


[LIST]
[*]mail from domain1.be :  IP 1 : smtp.domain1.be
[*]mail from domain2.com : IP 2 : smtp.domain2.com
[*]...
[/LIST]

It's ok for the IP : each domain send email from its own IP.

But I don't succeed to have the 

**Received: from smtp.domain1.be ([178.nn.nn.69])**    :   it's NOT possible.  :confused:


I can send all the domains from  ct1234.misson.ovh (the server name)
but I want that the mail come from  smtp.domain1.be ... or smtp.domain2.com ...


**I try several postfix conf : main.cf :**


```
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
# myhostname = localhost.localdomain   ... not accepted : spam for Live.com, Hotmail, Gmail
# myhostname = smtp.$mydomain   ...  error :  $mydomain is empty
myhostname = ct1234.misson.ovh   ... ok, but all emails domains come from the same ct1234.misson.ovh 
# myhostname = smtp.domain1.be    ... ok, but all domains send mail coming from  domain1 !
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $myhostname, localdomain, localhost, localhost.localdomain, localhost
relayhost =

```

How can I do this ? :confused:
Is it possible to have automatically this 

**myhostname = smtp.$mydomain**     ... with the **$mydomain** variable taking the correct value ?


Thanks  :)
Didier

---


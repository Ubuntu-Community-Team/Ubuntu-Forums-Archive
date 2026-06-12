---
title: "Sendmail send mail through Exchange 2003?"
date: 2006-12-11
forum: Server Platforms
---

### Post by General Moskovich on 2006-12-11
My main box run's 6.0.6 and Sendmail 8.13.5.20060308. My company uses exchange and I want to configure sendmail to send all mail (reports from Bugzilla, Wiki, etc...) through Exchange 2003. The address of my company's exchange server is:

https://owa.<COMPANY>.com/exchange  

What is the best way to configure this?

Thanks in advance for the help!

-Sean

---

### Post by chrisfay on 2006-12-11
Use a 'relayhost' and configute SMTP/SASL to auth with the exchange server. I use this method to route all my outgoing mail from my mail server through my ISP's server to circumvent dynamic IP blacklisting.

I use Postfix so not sure exactly how to do it on Sendmail.

---

### Post by General Moskovich on 2006-12-11
I've removed sendmail and installed postfix. I've added the "relayhost = mail.ispserver.com" line to "/etc/postfix/main.cf". Restarted postfix, but things still don't seem to be working. 

I don't know if my company's Exchange server allows for SMTP access like this. I can check mail in Evolution using the following settings:

Exchange server: [https://owa.fic.com.tw/exchange](https://owa.fic.com.tw/exchange)

I need to have the DAV requires SSL box checked. And enter my account, domain, and password. Can I do this in main.cf, too?

Thanks!

-Sean

---

### Post by General Moskovich on 2006-12-11
Here's my mail.log file, BTW.

```

Dec 12 09:04:51 localhost postfix/pickup[5601]: 37F15330229: uid=1000 from=<mosk
o>
Dec 12 09:04:51 localhost postfix/cleanup[5659]: 37F15330229: message-id=<200612
12010451.37F15330229@localhost.localdomain>
Dec 12 09:04:51 localhost postfix/qmgr[5602]: 37F15330229: from=<mosko@fic.com.t
w>, size=320, nrcpt=1 (queue active)
Dec 12 09:04:51 localhost postfix/local[5661]: 37F15330229: to=<sean_mosko@fic.c
om.tw>, relay=local, delay=0, status=bounced (unknown user: "sean_mosko")
Dec 12 09:04:51 localhost postfix/cleanup[5659]: 4521B330227: message-id=<200612
12010451.4521B330227@localhost.localdomain>
Dec 12 09:04:51 localhost postfix/qmgr[5602]: 4521B330227: from=<>, size=2006, n
rcpt=1 (queue active)
Dec 12 09:04:51 localhost postfix/qmgr[5602]: 37F15330229: removed
Dec 12 09:04:51 localhost postfix/local[5661]: 4521B330227: to=<mosko@fic.com.tw
>, relay=local, delay=0, status=sent (delivered to command: procmail -a "$EXTENS
ION")
Dec 12 09:04:51 localhost postfix/qmgr[5602]: 4521B330227: removed

```

---

### Post by chrisfay on 2006-12-11
You need to put your access credentials for the Exchange server in a db file and 'postmap' it. The Exchange server obviously won't allow just anyone to relay mail through their system which is why the logs you posted show your relayed mail bouncing.

Also, not sure if it makes a difference, but I thought the relayhost directive was supposed to be in the format:

```
relayhost = [smtp.comcast.net]
``` 
not 
```
relayhost = "smtp.comcast.net"
```

As a reference, here is the portion of my main.cf file that pertains to the relayhost option:

```
####### SMTP sasl for authenticating and relaying through Comcasts servers ###########
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options=
```

The *hash:/etc/postfix/sasl_passwd* is responsible for storing the smtp.server.tld, username and password to auth with the relayhost.

To create the hash file, you need to create the file:
```
/etc/postfix/sasl_passwd
```
Then insert your credentials to access the Exchange server.

The format for storing the credentials is as follows:
```
smtp.relayhost.tld username:password
```

Once that file is created, convert it into a db file by running:
```
sudo postmap /etc/postfix/sasl_passwd
```

Then add the directive into main.cf:
```
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
```

Don't forget to restart Postfix after the changes:

```
sudo /etc/init.d/postfix restart
```

---

### Post by General Moskovich on 2006-12-12
Everything is working very nicely now. Thanks a lot for the help!

---

### Post by chrisfay on 2006-12-12
Np

---


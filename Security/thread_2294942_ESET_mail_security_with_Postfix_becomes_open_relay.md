---
title: "ESET mail security with Postfix becomes open relay :-("
date: 2015-09-14
forum: Security
---

### Post by thuizt on 2015-09-14
Hello experts,

We installed ESET Mail Security on a Ubuntu server with Postfix to control the amount of spam being delivered.
The Postfix config posted below
Postfix is listening on port 2525
ESET listens on 25 check for spam etc and forwards to postfix on 2525

Outgoing mail is sent by postfix to the smart smtphost of the provider.

This seemed to be working fine until they found out and we realised what we had done..... 

ESET is forwarding everthing to postfix with a spam tag if it is declared so.
Postfix receives the mail. As it comes from localhost it is secure so it nicely sends it out to the smtphost.

We created a open Relay. As I am not a postfix expert I thought it wise to ask for advice here.

Thanks for reading.



main.cf

```
myhostname = server
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost
relayhost = smtp.provider.something
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
message_size_limit = 25600000
virtual_mailbox_domains = domain_1 domain_2
virtual_mailbox_maps = ldap:/etc/postfix/users.cf
virtual_alias_maps = ldap:/etc/postfix/aliases.cf
virtual_transport = tothemailserver
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
```

---

### Post by CharlesA on 2015-09-14
Are you sure you have postfix set up as an open relay?

I do not see any config here saying it is running off port 2525.

---

### Post by lisati on 2015-09-14
> **CharlesA said:**
> Are you sure you have postfix set up as an open relay?

I do not see any config here saying it is running off port 2525.

It has been a while since I've run Postfix. Could the relevant setting be in master.cf instead?

---

### Post by SeijiSensei on 2015-09-14
There are many effective open-source anti-spam tools available to you that are probably just as powerful as ESET and are free to use. I prefer [MailScanner]("https://www.mailscanner.info/") myself.

Like Charles, I don't think ESET is using port 2525 but just using localhost.  In the configuration you posted only traffic on 127.0.0.1 is accepted.

Before continuing, you should read [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html) and also at least [http://www.postfix.org/postconf.5.html#smtpd_relay_restrictions](http://www.postfix.org/postconf.5.html#smtpd_relay_restrictions).  

I'm not exactly sure I understand the problem.  Are you saying that if a message from [email]random_spammer@yahoo.com[/email] is sent to your server with a To: address of [email]unsuspecting_target@gmail.com[/email], your server will forward that message to GMail?  That's what it means to be an open relay.  That doesn't seem like the situation you are describing, but maybe I missed something.

Have you run your server through the various tests at mxtoolbox.com?

---

### Post by CharlesA on 2015-09-14
> **lisati said:**
> It has been a while since I've run Postfix. Could the relevant setting be in master.cf instead?

Possible. That would be where you set postfix to listen on a specific port or specific IP and other IP specific stuff like SSL certs or whatnot.

> **SeijiSensei said:**
> 
Like Charles, I don't think ESET is using port 2525 but just using localhost.  In the configuration you posted only traffic on 127.0.0.1 is accepted.

Before continuing, you should read [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html) and also at least [http://www.postfix.org/postconf.5.html#smtpd_relay_restrictions](http://www.postfix.org/postconf.5.html#smtpd_relay_restrictions).  

I'm not exactly sure I understand the problem.  Are you saying that if a message from [email]random_spammer@yahoo.com[/email] is sent to your server with a To: address of [email]unsuspecting_target@gmail.com[/email], your server will forward that message to GMail?  That's what it means to be an open relay.  That doesn't seem like the situation you are describing, but maybe I missed something.

Have you run your server through the various tests at mxtoolbox.com?

Kinda in the same boat as Seiji. I don't have enough info to make any sort of guess on how it is set up, but it does look like postfix is set to accept anything from 127.0.0.1 or localhost, would would prevent it from being used as an open relay. We'd need more info to be sure, though.

I also vouch for mxroute. I don't know if it can scan a SMTP server that isn't running off port 25 or 587, though.

---

### Post by thuizt on 2015-09-15
Hello,

Indeed, Postfix runs on port 2525 as is set in master.cf

```
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
2525      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
```


So what happens:

Mail from outside is delivered to ESET who does no domain check, so no relay denied messages. It scans the mail and nicely forwards the message with a SPAM tag to postfix.
Postfix receives the message from localhost (ESET) and believes the mail is secure so passes it on. Domain mail to the mailserver. Not domain mail (SPAM) outside to the smarthost: smtp.provider.ext. Et voila an open relay.

The issue is that ESET does not do any domain check, not only mail for the local domains is accepted, but allows everything. 

Thanks for your answers.

---

### Post by CharlesA on 2015-09-15
You would need to configure that in ESET, not postfix then.

---


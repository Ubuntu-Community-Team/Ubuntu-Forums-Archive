---
title: "postfix, subdomains and mydestination"
date: 2011-03-30
forum: Server Platforms
---

### Post by Mozai on 2011-03-30
I've one mailhub 'E' for all my hosts named something.domain.tld, and it holds all the mailboxes.  I've told the other machines ('N' and 'H') not to deliver any mail locally, just pass it to 'E' right away.  The idea is for mail on host 'N' sent to an unqualified 'username' will be passed to host 'E' addressed for 'username@N.domain.tld', and to the local mailbox on host 'E' for 'username'.

When it gets to host 'E', postfix tries to pass it back to the host it came from.  I'm perplexed because I'm certain I told 'E' that it is the destination for any mail ending in @something.domain.tld.

On machine 'N':
Mar 30 21:58:38 N sSMTP[32704]: Sent mail for [email]kroot@N.mozai.com[/email] (221 2.0.0 Bye) uid=0 username=root outbytes=356

On machine 'E':
Mar 30 14:34:15 E postfix/smtpd[30478]: 0D447AB004C: client=N.mozai.com[109.169.27.112]
Mar 30 14:34:16 E postfix/cleanup[30481]: 0D447AB004C: message-id=<>
Mar 30 14:34:16 E postfix/qmgr[27885]: 0D447AB004C: from=<kroot@N.mozai.com>, size=445, nrcpt=1 (queue active)
Mar 30 14:34:16 E postfix/smtp[30554]: 0D447AB004C: to=<kmoses@N.mozai.com>, relay=none, delay=2.1, delays=1.7/0/0.45/0, dsn=4.4.1, status=deferred (connect to N.mozai.com[109.169.27.112]:25: Connection refused)

My relevant postfix configuration settings are:
```
$ postconf mydomain mydestination relay_domains
mydomain = mozai.com
mydestination = $myhostname, $mydomain, /etc/postfix/mydestination
relay_domains = $mydestination, /etc/postfix/relay_domains
$ echo $(cat /etc/postfix/mydestination)
mozai.com .mozai.com 
```

According to 'man 5 postconf' : *"...all Postfix features  are expected  to  require  explicit  ".domain.tld"  style patterns when you really want to match subdomains."*  So the ".mozai.com" should've worked, right?

Just in case, I added 'mydestination' to 'parent_domain_matches_subdomains' and tried again.  According to 'man 5 postconf' that should've allowed "mozai.com" in mydestination to also match "N.mozai.com".

```
$ postconf parent_domain_matches_subdomains
 parent_domain_matches_subdomains =  debug_peer_list,
 fast_flush_domains,mynetworks,permit_mx_backup_networks,
 qmqpd_authorized_clients,smtpd_access_maps,mydestination
$ sudo /etc/init.d/postfix restart
 * Stopping Postfix Mail Transport Agent postfix
   ...done.
 * Starting Postfix Mail Transport Agent postfix
   ...done.
$ date
Wed Mar 30 15:00:54 EDT 2011
$ sudo postqueue -f
$ sudo tail /var/log/mail.log
Mar 30 15:00:59 E postfix/smtp[9267]: 0D447AB004C: 
 to=<kmoses@N.mozai.com>, relay=none, delay=1605, delays=1604/0/0.44/0, 
 dsn=4.4.1, status=deferred (connect to N.mozai.com[109.169.27.112]:25: 
 Connection refused)
```

... it still believes it is not the destination for N.mozai.com and it's trying to hand it back to the machine the message came from.

What am I doing wrong here?

---

### Post by SeijiSensei on 2011-03-30
```
Mar 30 14:34:16 E postfix/smtp[30554]: 0D447AB004C: to=<kmoses@N.mozai.com>, relay=none, delay=2.1, delays=1.7/0/0.45/0, dsn=4.4.1, status=deferred (connect to N.mozai.com[109.169.27.112]:25: Connection refused)
```

If you want N.mozai.com to accept inbound mail, it has to be running its own copy of Postfix configured to accept mail for that domain.

---

### Post by Mozai on 2011-03-30
> **SeijiSensei said:**
> 
If you want N.mozai.com to accept inbound mail, it has to be running its own copy of Postfix configured to accept mail for that domain.

Seems I was unclear.  I'll edit the original
> The idea is for mail on host 'N' sent to an unqualified 'username' will be passed to host 'E' addressed for 'username@N.domain.tld', and to the local mailbox **[COLOR="Red"]ON host 'E'[/COLOR]** for 'username'.

---

### Post by Mozai on 2011-03-30
Yeah, so let me try explaining my expectation again, since it seems I went into too much detail at first.

On host 'N':
```
  kroot@N:~$ echo "pounce message" |mail kmoses 
```

On host 'E':
```
  You have new mail!
  kmoses@E:~$ mail
    1  From: kroot@N.mozai.com
       To: kmoses@N.mozai.com
       Subject: (none)
       
       pounce message
  kmoses@E~$
```

I've told postfix on 'E' to include "mozai.com" and ".mozai.com" in the mydestination setting.  According to 'man 5 postconf' that means that a domain part like 'N.mozai.com' should count as a domain name in the mydestination setting.  Instead, postfix believes that 'N.mozai.com' is not one of the local destinations, and it's trying to send the mail to 'N.mozai.com'.

Actually, this raises another weird thing: if you do a DNS lookup for the MX record of 'N.mozai.com', you get no answer.  I expect postfix smtpd would lookup the MX record for 'mozai.com.' (and 'com.' and '.') in that case... but the MX record for 'mozai.com.' is "mail.mozai.com", *not* 'N.mozai.com'.  So postfix is doing two things unexpected here.

---

### Post by SeijiSensei on 2011-03-31
The standard (see part 5 of [RFC2821]("http://www.ietf.org/rfc/rfc2821.txt")) is to treat the "domain part" of the address as a hostname if there is no MX record matching that domain part.  By that rule, Postfix sends mail directly to n.mozai.com since there's no MX record.

I don't use Postfix but surely there must be a method to tell it to accept mail for n.mozai.com as local beyond simply the ".mozai.com" method that seems not to work for you.  In sendmail this is a trivial task; you just add all the names you want sendmail to consider local to /etc/mail/local-host-names and you're done.

---

### Post by Mozai on 2011-03-31
> **SeijiSensei said:**
> The standard (see part 5 of [RFC2821]("http://www.ietf.org/rfc/rfc2821.txt")) is to treat the "domain part" of the address as a hostname if there is no MX record matching that domain part.

Ah, so I made an incorrect assumption; I will alter my expectations accordingly.  This makes my question about subdomains and configuring Postfix even more necessary.

> **SeijiSensei said:**
> I don't use Postfix...

They why on Earth are you writing on a thread asking how to use Postfix?

> **SeijiSensei said:**
> ... but surely there must be a method to tell it to accept mail for n.mozai.com as local beyond simply the ".mozai.com" method that seems not to work for you.

I can explicitly state 'N.mozai.com' in the 'mydestination' configuration setting.  It is equally "trivial" as you suggest it is with sendmail.

However, this doesn't solve the problems of: (a) how to get this MTA to treat all subdomains of explictly defined local domains as local domains and (b) when I follow the instructions in 'man 5 postconf' I am not getting the behaviour from postfix that is described in 'man 5 postconf'.

---


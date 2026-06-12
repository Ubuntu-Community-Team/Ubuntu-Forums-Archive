---
title: "Postfix + &quot;550-Verification failed&quot;"
date: 2008-03-29
forum: Server Platforms
---

### Post by dimitryb on 2008-03-29
Well, after 2 days of trying to get this to work, I give up and I hope you guys can help me.

I seem to have everything working, TLS, SALS, etc. I have courier-imap that works well too.

I can receive emails fine and I can send email fine to gmail, yahoo, etc. but NOT all servers. From some servers I get:
```

host SOME_DOMAIN.com[SOME_IP] said:
    550-Verification failed for <noreply@arrivalalert.com> 550-No Such User
    Here 550 Sender verify failed (in reply to RCPT TO command)

```

Domain name is '**arrivalalert.com**' and DNS config SEEMS to be proper, though I'm fairly new to this.

**/etc/postfix/main.cf**
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.arrivalalert.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.arrivalalert.com, localhost.arrivalalet.com, localhost.localdomain, localhost, arrivalalert.com
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
mailbox_command =

```

**/etc/hosts**
```

127.0.0.1       localhost localhost.localdomain
209.20.64.86    mail.arrivalalert.com mail

```

**telnet localhost 25**
```

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mail.arrivalalert.com ESMTP Postfix (Ubuntu)
ehlo localhost
250-mail.arrivalalert.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```

**dig arrivalalert.com mx**
```

; <<>> DiG 9.4.1-P1 <<>> arrivalalert.com mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11855
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;arrivalalert.com.		IN	MX

;; ANSWER SECTION:
arrivalalert.com.	3596	IN	MX	0 mail.arrivalalert.com.

;; Query time: 2 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sat Mar 29 17:08:53 2008
;; MSG SIZE  rcvd: 55

```

**dig -x 209.20.64.86**
```

; <<>> DiG 9.4.1-P1 <<>> -x 209.20.64.86
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 14766
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;86.64.20.209.in-addr.arpa.	IN	PTR

;; ANSWER SECTION:
86.64.20.209.in-addr.arpa. 86400 IN	PTR	mail.arrivalalert.com.

;; Query time: 600 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sat Mar 29 17:09:41 2008
;; MSG SIZE  rcvd: 78

```

Any ideas?

Thank you so much

---

### Post by Mr. C. on 2008-03-30
Please show the complete log message - important information is missing.

This looks like sender verification.

---

### Post by dimitryb on 2008-03-30
Here's the full log from start of sending message to the bounce:

```

Mar 30 21:52:57 dimitry postfix/smtpd[7025]: connect from c-IP-ADDRESS.hsd1.ca.comcast.net[IP-ADDRESS]
Mar 30 21:52:57 dimitry postfix/smtpd[7025]: setting up TLS connection from c-IP-ADDRESS.hsd1.ca.comcast.net[IP-ADDRESS]
Mar 30 21:52:57 dimitry postfix/smtpd[7025]: TLS connection established from c-IP-ADDRESS.hsd1.ca.comcast.net[IP-ADDRESS]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Mar 30 21:52:57 dimitry postfix/smtpd[7025]: 84E251D86B2: client=c-IP-ADDRESS.hsd1.ca.comcast.net[IP-ADDRESS], sasl_method=PLAIN, sasl_username=noreply
Mar 30 21:52:57 dimitry postfix/cleanup[7029]: 84E251D86B2: message-id=<47F00BB8.9060605@arrivalalert.com>
Mar 30 21:52:57 dimitry postfix/qmgr[7005]: 84E251D86B2: from=<noreply@arrivalalert.com>, size=682, nrcpt=1 (queue active)
Mar 30 21:52:57 dimitry postfix/smtpd[7031]: connect from localhost[127.0.0.1]
Mar 30 21:52:57 dimitry postfix/smtpd[7025]: disconnect from c-IP-ADDRESS.hsd1.ca.comcast.net[IP-ADDRESS]
Mar 30 21:52:57 dimitry postfix/smtp[7030]: discarding EHLO keywords: 8BITMIME STARTTLS
Mar 30 21:52:57 dimitry postfix/smtpd[7031]: BF3901D86B3: client=c-IP-ADDRESS.hsd1.ca.comcast.net[IP-ADDRESS]
Mar 30 21:52:57 dimitry dkimproxy.out[2368]: DKIM signing - signed; message-id=<47F00BB8.9060605@arrivalalert.com>, signer=<noreply@arrivalalert.com>, from=<noreply@arrivalalert.com> 
Mar 30 21:52:57 dimitry postfix/cleanup[7029]: BF3901D86B3: message-id=<47F00BB8.9060605@arrivalalert.com>
Mar 30 21:52:57 dimitry postfix/qmgr[7005]: BF3901D86B3: from=<noreply@arrivalalert.com>, size=1643, nrcpt=1 (queue active)
Mar 30 21:52:57 dimitry postfix/smtp[7030]: 84E251D86B2: to=<email@domain.com>, relay=127.0.0.1[127.0.0.1]:10027, delay=0.39, delays=0.22/0.02/0.05/0.1, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as BF3901D86B3)
Mar 30 21:52:57 dimitry postfix/smtpd[7031]: disconnect from localhost[127.0.0.1]
Mar 30 21:52:57 dimitry postfix/qmgr[7005]: 84E251D86B2: removed
Mar 30 21:53:00 dimitry postfix/smtp[7032]: certificate verification failed for domain.com: num=18:self signed certificate
Mar 30 21:53:02 dimitry postfix/smtp[7032]: BF3901D86B3: to=<email@domain.com>, relay=domain.com[THEIR-IP-ADDRESS]:25, delay=5, delays=0.09/0.01/2.2/2.6, dsn=5.0.0, status=bounced (host domain.com[THEIR-IP-ADDRESS] said: 550-Verification failed for <noreply@arrivalalert.com> 550-No Such User Here 550 Sender verify failed (in reply to RCPT TO command))
Mar 30 21:53:02 dimitry postfix/cleanup[7029]: C16361D86B5: message-id=<20080330215302.C16361D86B5@mail.arrivalalert.com>
Mar 30 21:53:02 dimitry postfix/qmgr[7005]: C16361D86B5: from=<>, size=3740, nrcpt=1 (queue active)
Mar 30 21:53:02 dimitry postfix/bounce[7033]: BF3901D86B3: sender non-delivery notification: C16361D86B5
Mar 30 21:53:02 dimitry postfix/qmgr[7005]: BF3901D86B3: removed
Mar 30 21:53:02 dimitry postfix/local[7034]: C16361D86B5: to=<noreply@arrivalalert.com>, relay=local, delay=0.09, delays=0.03/0.01/0/0.05, dsn=2.0.0, status=sent (delivered to maildir)
Mar 30 21:53:02 dimitry postfix/qmgr[7005]: C16361D86B5: removed

```

Some interesting lines:
**dimitry postfix/smtp[7032]: certificate verification failed for domain.com: num=18:self signed certificate**

**dimitry postfix/smtp[7032]: BF3901D86B3: to=<email@domain.com>, relay=domain.com[64.22.83.117]:25, delay=5, delays=0.09/0.01/2.2/2.6, dsn=5.0.0, status=bounced (host domain.com[64.22.83.117] said: 550-Verification failed for <noreply@arrivalalert.com> 550-No Such User Here 550 Sender verify failed (in reply to RCPT TO command))**

I also tried changing ** smtpd_use_tls = yes** from **yes** to **no** as per another suggestion. Didn't help.

Thank you
Dimitry

---

### Post by dimitryb on 2008-03-30
It's worth noting that I use DKIM outgoing mail signing. Not sure if that could be an issue or not.

---

### Post by Mr. C. on 2008-03-30
So the remote server said:

```
550-No Such User Here
```

Do  you have reason to believe otherwise ?

---

### Post by dimitryb on 2008-03-30
Well, I'm testing against my friend's email which I know is a valid email address.

Perhaps his server isn't setup properly? If I use my private gmail account, I can easily send & receive mail from that same address.

I turned off DKIM proxy and same error occurs, so I know that's not causing it.

---

### Post by Mr. C. on 2008-03-30
Then you will have to ask your friend why his server is rejecting your email.  You can't send mail to servers that won't accept.

---

### Post by dimitryb on 2008-03-30
Ok, I thought it was something on my end because of ** postfix/smtp[7032]: certificate verification failed for domain.com: num=18:self signed certificate**

That appeared right before the bounce, but perhaps that's just a warning, not sure.

Why is my server expecting a cert verification?

Also, it's interesting that Gmail can deliver mail to his server, but not mine. I'd like to replicate their mail server behavior/settings.

---

### Post by Mr. C. on 2008-03-30
> Why is my server expecting a cert verification?
You have :

```
smtp_use_tls = yes
```

which means the SMTP **client** will use TLS.  But your certificate is not verified, so TLS fails.  The smtp client is used to relay mail out to another server.  So, does your friend require encryption and possibly authentication to relay through his machine?  Or are you just trying to send mail to an address for which his machine is final destination (in which case you are not relaying, just sending to final destination, and he should accept).

Earlier you said you'd changed smtp**d**_use_tls.  Note that this is the SMTP **server** ( not client, as smtp != smtpd ).  The smtpd_use_tls is when you want postfix to secure incoming clients.

---

### Post by dimitryb on 2008-03-30
Interesting. Thanks for clarifying Mr. C!

Basically, I want to require a login on my mail server so not just anyone can send emails through it (which looks like I have to set smtp**d**_use_tls to true), but don't require encryption when sending out emails (set smtp_use_tls to false?) as Im not relaying anything, I'm just sending an email for which his machine is final destination.

I'll try to with **smtp_use_tls = no** and see if that works.

---

### Post by Mr. C. on 2008-03-30
Right!

The default of smtp_use_tls is false, so just comment it out.

---

### Post by dimitryb on 2008-03-30
Unfortunately, still no go :(

Setting smtp_use_tls to 'no' removed the **certificate verification failed** message, but the mail still comes bounced.

What bothers me is "550-Verification failed for <**noreply@arrivalalert.com**> 550-No Such User Here 550 Sender verify failed (in reply to RCPT TO command))"

Their server is trying to verify that noreply@ account actually exists (which it does.. its a unix account), but my server fails to verify it? Not sure what is going on with that.

[edit] the log hasn't changed other than **certificate verification failed** line is removed and is replaced with:
**Mar 31 02:12:25 dimitry postfix/smtp[7517]: Host offered STARTTLS: [THEIR-DOMAIN.com]**

---

### Post by Mr. C. on 2008-03-30
If they are sending address verification probes during the SMTP conversation and expect success before they'll receive your email, you will have to provide verifiable addresses.

You can try to disable the verify command:

```
disable_vrfy_command = yes
```

but they may still reject.

---

### Post by dimitryb on 2008-03-31
Wow, ok, finally figured it out.

Our domain used to be hosted on the server I was trying to send an email to. We moved it to the new box, updated the DNS, but never actually deleted the account on that old hosting account (on which my buddy's other site and email (email@domain.com) are hosted).

I guess the receiving server was getting confused and was trying to verify if 'noreply' account exists on the old server. GRRRR

So sorry guys. At least I got a chance to learn what every single configuration does in Postfix! Thanks for helping me out.

---

### Post by Mr. C. on 2008-03-31
Good work.  Please prepend the subject of this thread with [Solved]:

---


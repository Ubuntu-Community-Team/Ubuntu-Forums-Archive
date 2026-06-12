---
title: "[SOLVED] I need help configuring postfix to send mail to gmail smtp"
date: 2007-07-23
forum: Server Platforms
---

### Post by Warren Watts on 2007-07-23
All I want to do is something simple: I have a Perl script that takes data from a web form, structures the data into an email, and sends me the email.  The Perl script is written, it works, no problem.

My problem is configuring postfix to send the mail to gmail's smtp server.  I just can't make it work.  Gmail's server keeps bouncing the mail back, saying that I am not providing authentication.

I'm almost positive that my problems are due to a general lack of knowledge regarding the proper configuration of postfix.  Basically, I don't know what values to use for some of the lines in  /etc/postfix/main.cf

My ISP only provides me with a dynamic IP, so I am using a dynamic DNS service to provide my domain name.
the domain provided by the dynamic DNS servce is XXXXXXX.servehttp.com.

here is the output from **postconf -n** **(the BOLD text with the ???? is where I need help!)**
> alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = localhost.localdomain, , localhost
myhostname = **????? WHAT SHOULD I PUT HERE?**
mynetworks = 127.0.0.0/8
myorigin =  **????? WHAT SHOULD I PUT HERE?**
recipient_delimiter = +
relayhost = [smtp.gmail.com]:587
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options =
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom


Here is my /etc/postfix/sasl_passwd file:
> 
[smtp.gmail.com]:587    [email]account@gmail.com[/email] : password



here is my /etc/postfix/transport file:
> 
*       smtp:[smtp.gmail.com]:587



here is a sample from the /var/log/maillog:
> 
Jul 22 14:34:00 Ubuntu postfix/pickup[18363]: 036A8115F78: uid=1000 from=<warren>
Jul 22 14:34:00 Ubuntu postfix/cleanup[18371]: 036A8115F78: message-id=<20070722183400.036A8115F78@XXX.XXX.com>
Jul 22 14:34:00 Ubuntu postfix/qmgr[18364]: 036A8115F78: from=<warren@xxx.com>, size=376, nrcpt=1 (queue active)
Jul 22 14:34:00 Ubuntu postfix/smtp[18373]: 036A8115F78: to=<kxxx@xxx.com>, delay=smtp.gmail.com[66.249.83.109]:587, delay=0.58, delays=0.05/0/0.48/0.05, dsn=5.5.1, status=bounced (host smtp.gmail.com[66.249.83.109] said: 530 5.5.1 Authentication Required i36sm9717388wxd (in reply to MAIL FROM command))
Jul 22 14:34:00 Ubuntu postfix/cleanup[18371]: 99D05115F7A: message-id=<20070722183400.99D05115F7A@xxx.xxx>
Jul 22 14:34:00 Ubuntu postfix/qmgr[18364]: 99D05115F7A: from=<>, size=2182, nrcpt=1 (queue active)
Jul 22 14:34:00 Ubuntu postfix/bounce[18375]: 036A8115F78: sender non-delivery notification: 99D05115F7A
Jul 22 14:34:00 Ubuntu postfix/qmgr[18364]: 036A8115F78: removed
Jul 22 14:34:01 Ubuntu postfix/smtp[18373]: 99D05115F7A: to=<warren@xxx.xxx>,  delay=smtp.gmail.com[66.249.83.111]:587,  delay=0.54, delays=0.01/0/0.48/0.04, dsn=5.5.1, status=bounced (host smtp.gmail.com[66.249.83.111] said: 530 5.5.1 Authentication Required h8sm5154170wxd (in reply to MAIL FROM command))
Jul 22 14:34:01 Ubuntu postfix/qmgr[18364]: 99D05115F7A: removed


I have all the proper certificates, and SASL and TLS are working, I tested postfix with telnet.  HELP!!!!

---

### Post by Mr. C. on 2007-07-23
Please review my post here: [http://ubuntuforums.org/showthread.php?t=501160&highlight=mrc+tls](http://ubuntuforums.org/showthread.php?t=501160&highlight=mrc+tls)

You need to reset your expections - what you are trying to do is not simple.  Mail servers require a great deal of knowledge, and advanced configurations are non-trivial.

Spend some time learning what the logs are telling you when there is a failure, and how the postfix mail system works in general.

You cannot test authentication over TLS using telnet - this cannot verify your client TLS is working.

myhostname should be ... the name of your mail host, as would be in your MX record for your domain.

myorigin is basically the domain name tacked onto local email addresses for local deliveries.  It is myhostname by default.

These are all documented in man 5 postconf.  Take some time learning the mail system.

MrC

---

### Post by Warren Watts on 2007-07-23
> **Mr. C. said:**
> 
You need to reset your expections - what you are trying to do is not simple.  Mail servers require a great deal of knowledge, and configuration advanced setups is non-trivial.
Spend some time learning what the logs are telling you where there is a failure, and how the postfix mail system works in general.


 Oh, believe me, I am well aware of the complexity!  I have been working on this for two days solid now.  

> **Mr. C. said:**
> 
You cannot test authentication over TLS using telnet - this cannot verify your client TLS is working.


  What I mean is that I was able to determine that TLS was installed, and started properly.

> **Mr. C. said:**
> 
myhostname should be ... the name of your mail host, as would be in your MX record for your domain.


  I don't HAVE an MX record.  because I don't have a domain.  I got my domain thru a dynamic DNS service - NoIP.com....

> **Mr. C. said:**
> 
myorigin is basically the domain name tacked onto local email addresses for local deliveries.  It is myhostname by default.

These are all documented in man 5 postconf.  Take some time learning the mail system.

MrC

After having spent the last two days setting this up, reading countless HOW-TO's and documentation, I feel like I have a fair grasp of the basics.  What I really need is someone who has a similar configuration to help me fill in the blanks.  

I appreciate your help and fast response, but telling me to RTFM isn't exactly constructive.

I'm not having TLS difficulties as near as i can tell.  I resolved those issues already.  You can see form the maillog that there aren't any certificate errors.

---

### Post by Mr. C. on 2007-07-23
Hmmm... "All I want to do is something simple:" and "Oh, believe me, I am well aware of the complexity!" seem quite disjoint to me... nonetheless.

Nobody can just fill in the blanks for you, because we are not there at your box verifying what does and doesn't work.  Therefore, you need to provide *evidence* of what works and what doesn't.  I'm sure you believe that all is installed, and is working fine., but I stopped believing people's "It works... trust me" responses long ago.

Your postfix log is telling us one thing... the remote server is denying access because the "Authentication Required" has not been established.  In fact, your smtp server got to the MAIL FROM dialog, and did not try to authenticate or establish a TLS connection.

Since there is not a trace of any TLS activity in your log messages, you need to increase your smtp_tls_loglevel to show what is failing, or that the TLS dialog is even starting.  AUTH won't happen until TLS is established.

You said you had a domain ("the domain provided by the dynamic DNS servce is XXXXXXX.servehttp.com") and you say you don't ("I don't HAVE an MX record. because I don't have a domain.").  I don't know what you have and don't have. 

Your focus on those two parameters in main.cf are not the issue.

I completely disagree with you regarding documentation reading.  The documentation that has been worked on and refined for years is critical to building a mail server.  If you want a cookbook recipe, keep searching until you find one that suits your needs and tastes.  If you want to learn how to make it work, ask constructive questions and start learning how to read basic documentation.  Then follow-up with specific questions that you do not understand regarding that documentation.

MrC

---

### Post by Warren Watts on 2007-07-23
OK, OK, so maybe I was a little quick to take offense at your suggestions...  I apologize.

When I said I wanted to do something simple, I meant that at its core, sending an email is a pretty simple thing.  I didn't mean that setting up an email server was simple.

I agree that one does not learn how to do something complex without reading some documentation.  But, cut a Linux newbie some slack here, I only cut the Micro$oft ball and chain off my ankle a few months ago.  I'm coming from an OS where the manual that came with it explains the difference between a single click and a double-click, and doesn't go much deeper than that. 

I DID do a little research/reading after your first post, and got the MX record concept under my belt.  Thank you for your help.

I have increased the TLS logging level to 3 (should it be higher?) and here is what I get in the maillog:
> Jul 23 01:15:54 Ubuntu postfix/pickup[2365]: 90639115F78: uid=1000 from=<warren>
Jul 23 01:15:54 Ubuntu postfix/cleanup[2373]: 90639115F78: message-id=<20070723051554.90639115F78@servehttp.com>
Jul 23 01:15:54 Ubuntu postfix/qmgr[2366]: 90639115F78: from=<warren@servehttp.com>, size=376, nrcpt=1 (queue active)
Jul 23 01:15:54 Ubuntu postfix/tlsmgr[2376]: open smtpd TLS cache btree:/var/spool/postfix/smtpd_scache
Jul 23 01:15:54 Ubuntu postfix/tlsmgr[2376]: tlsmgr_cache_run_event: start TLS smtpd session cache cleanup
Jul 23 01:15:55 Ubuntu postfix/smtp[2375]: 90639115F78: to=<kingbeetle_66@yahoo.com>, relay=smtp.gmail.com[64.233.167.109]:587, delay=0.5, delays=0.12/0.09/0.26/0.03, dsn=5.5.1, status=bounced (host smtp.gmail.com[64.233.167.109] said: 530 5.5.1 Authentication Required f6sm9441524pyh (in reply to MAIL FROM command))
Jul 23 01:15:55 Ubuntu postfix/cleanup[2373]: 13785115F7A: message-id=<20070723051555.13785115F7A@servehttp.com>
Jul 23 01:15:55 Ubuntu postfix/qmgr[2366]: 13785115F7A: from=<>, size=2211, nrcpt=1 (queue active)
Jul 23 01:15:55 Ubuntu postfix/bounce[2377]: 90639115F78: sender non-delivery notification: 13785115F7A
Jul 23 01:15:55 Ubuntu postfix/qmgr[2366]: 90639115F78: removed
Jul 23 01:15:55 Ubuntu postfix/smtp[2375]: 13785115F7A: to=<warren@servehttp.com>, relay=smtp.gmail.com[64.233.167.109]:587, delay=0.31, delays=0.01/0/0.26/0.03, dsn=5.5.1, status=bounced (host smtp.gmail.com[64.233.167.109] said: 530 5.5.1 Authentication Required v15sm9522533pyh (in reply to MAIL FROM command))
Jul 23 01:15:55 Ubuntu postfix/qmgr[2366]: 13785115F7A: removed



I really do appreciate any help you can provide.

Warren

---

### Post by kvonb on 2007-07-23
I don't know much, but is it possible to use somebody else's mail server?

Surely you would simply send the email to your gmail account from your own email server, rather than trying to access gmail's server directly?

It would be blocked from external access, surely?

I would suggest setting up your own email server (as I did), it's quite easy and it does work with a dyndns free domain name, that's how mine is working.

Plus it might also be your ISP or router blocking email servers, some do.

Here are some good threads:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html)
[http://ubuntuforums.org/showthread.php?t=185913&highlight=mail+server](http://ubuntuforums.org/showthread.php?t=185913&highlight=mail+server)

Yeah I know, more reading!

I use dovecot and postfix with "Maildir" format, and also SquirrelMail for web access :).

---

### Post by Warren Watts on 2007-07-23
I don't really need a full blown mail server; all I want to do is send emails in response to a completed form on a web page.  

Setting up my own mail server would probably be the best solution, I agree.  But considering my level of expertise, I'm not sure I can get ALL of the pieces happily working together.  

Look at the problems I have had just getting an MTA with SSL Authentication working!  Now you are suggesting I add a whole new layer of complexity to the equation?  #-o  Whew!  

I have based all me efforts so far on a couple of guides I found:

[http://souptonuts.sourceforge.net/postfix_tutorial.html](http://souptonuts.sourceforge.net/postfix_tutorial.html)
[http://prantran.blogspot.com/search/label/relayhost](http://prantran.blogspot.com/search/label/relayhost)

My ISP does indeed block port 25, that's why I am trying to use gmail's server on port 587.  
(BTW, I have enabled all the appropriate ports on the router, but it was a worthy suggestion, and something I could have overlooked)

---

### Post by Mr. C. on 2007-07-23
There is nothing in your log messages to indicate that TLS is being used.
```

smtp_use_tls = yes

```
is necessary, but *not* sufficient.

Your smtp_tls_CAfile must point to a ca-bundle.crt or directory containing the required certificates to verify gmail via its CA.  It will likely be in /usr/share/ssl/certs, but you can run:

```
locate ca-bundle.crt
```

to find it.

You have to add your own root CA cert to the bundle:

cat /path/to/your/democert/cacert.pem >> /path/to/found/ca-bundle.crt

```
smtp_tls_loglevel = 2 
```

is sufficient and postfix reload.

Examine log output afterwards.

MrC

---

### Post by Warren Watts on 2007-07-23
Ok, I appended my cacert.pem onto ca-certificates.cat
changed main.cf to reflect change: 
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
and set the log level to 2:
smtp_tls_loglevel = 2

here is the maillog:

> Jul 23 16:54:50 Ubuntu postfix/master[16775]: reload configuration /etc/postfix
Jul 23 16:54:51 Ubuntu postfix/master[16775]: terminating on signal 15
Jul 23 16:54:52 Ubuntu postfix/master[17067]: daemon started -- version 2.3.8, configuration /etc/postfix
Jul 23 16:54:52 Ubuntu postfix/pickup[17068]: EE1B7115F78: uid=1000 from=<warren>
Jul 23 16:54:53 Ubuntu postfix/cleanup[17077]: EE1B7115F78: message-id=<20070723205452.EE1B7115F78@servehttp.com>
Jul 23 16:54:53 Ubuntu postfix/qmgr[17069]: EE1B7115F78: from=<warren@servehttp.com>, size=423, nrcpt=1 (queue active)
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: initializing the client-side TLS engine
Jul 23 16:54:53 Ubuntu postfix/tlsmgr[17080]: open smtpd TLS cache btree:/var/spool/postfix/smtpd_scache
Jul 23 16:54:53 Ubuntu postfix/tlsmgr[17080]: open smtp TLS cache btree:/var/spool/postfix/smtp_scache
Jul 23 16:54:53 Ubuntu postfix/tlsmgr[17080]: tlsmgr_cache_run_event: start TLS smtpd session cache cleanup
Jul 23 16:54:53 Ubuntu postfix/tlsmgr[17080]: tlsmgr_cache_run_event: start TLS smtp session cache cleanup
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: setting up TLS connection to smtp.gmail.com
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: looking for session smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL in smtp cache
Jul 23 16:54:53 Ubuntu postfix/tlsmgr[17080]: lookup smtp session id=smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:before/connect initialization
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv2/v3 write client hello A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv2/v3 read server hello A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read server hello A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read server hello A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 read server hello A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read server certificate A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read server certificate A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: certificate verification depth=1 subject=/C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: verify return: 1
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: certificate verification depth=0 subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: verify return: 1
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 read server certificate A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read server key exchange A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read server key exchange A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 read server done A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 write client key exchange A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 write change cipher spec A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 write finished A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 flush data
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read finished A
Jul 23 16:54:53 Ubuntu last message repeated 3 times
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 read finished A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: save session smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL to smtp cache
Jul 23 16:54:53 Ubuntu postfix/tlsmgr[17080]: put smtp session id=smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL [data 992 bytes]
Jul 23 16:54:53 Ubuntu postfix/tlsmgr[17080]: write smtp TLS cache entry smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL: time=1185224093 [data 992 bytes]
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: Verified: subject_CN=smtp.gmail.com, issuer=Thawte Premium Server CA
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: TLS connection established to smtp.gmail.com: TLSv1 with cipher DES-CBC3-SHA (168/168 bits)
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: EE1B7115F78: to=<kingbeetle_66@yahoo.com>, relay=smtp.gmail.com[64.233.167.109]:587, delay=0.74, delays=0.16/0.17/0.38/0.03, dsn=5.5.1, status=bounced (host smtp.gmail.com[64.233.167.109] said: 530 5.5.1 Authentication Required n44sm10809916pyh (in reply to MAIL FROM command))
Jul 23 16:54:53 Ubuntu postfix/cleanup[17077]: A3A7B115F7A: message-id=<20070723205453.A3A7B115F7A@servehttp.com>
Jul 23 16:54:53 Ubuntu postfix/qmgr[17069]: A3A7B115F7A: from=<>, size=2262, nrcpt=1 (queue active)
Jul 23 16:54:53 Ubuntu postfix/bounce[17083]: EE1B7115F78: sender non-delivery notification: A3A7B115F7A
Jul 23 16:54:53 Ubuntu postfix/qmgr[17069]: EE1B7115F78: removed
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: setting up TLS connection to smtp.gmail.com
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: looking for session smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL in smtp cache
Jul 23 16:54:53 Ubuntu postfix/tlsmgr[17080]: lookup smtp session id=smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL
Jul 23 16:54:53 Ubuntu postfix/tlsmgr[17080]: read smtp TLS cache entry smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL: time=1185224093 [data 992 bytes]
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: reloaded session smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL from smtp cache
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:before/connect initialization
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 write client hello A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read server hello A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read server hello A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 read server hello A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read server certificate A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read server certificate A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: certificate verification depth=1 subject=/C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: verify return: 1
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: certificate verification depth=0 subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: verify return: 1
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 read server certificate A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read server key exchange A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read server key exchange A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 read server done A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 write client key exchange A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 write change cipher spec A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 write finished A
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 flush data
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: SSL_connect:error in SSLv3 read finished A
Jul 23 16:54:54 Ubuntu last message repeated 3 times
Jul 23 16:54:54 Ubuntu postfix/smtp[17079]: SSL_connect:SSLv3 read finished A
Jul 23 16:54:54 Ubuntu postfix/smtp[17079]: save session smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL to smtp cache
Jul 23 16:54:54 Ubuntu postfix/tlsmgr[17080]: put smtp session id=smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL [data 992 bytes]
Jul 23 16:54:54 Ubuntu postfix/tlsmgr[17080]: write smtp TLS cache entry smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL: time=1185224094 [data 992 bytes]
Jul 23 16:54:54 Ubuntu postfix/smtp[17079]: Verified: subject_CN=smtp.gmail.com, issuer=Thawte Premium Server CA
Jul 23 16:54:54 Ubuntu postfix/smtp[17079]: TLS connection established to smtp.gmail.com: TLSv1 with cipher DES-CBC3-SHA (168/168 bits)
Jul 23 16:54:54 Ubuntu postfix/smtp[17079]: A3A7B115F7A: to=<warren@servehttp.com>, relay=smtp.gmail.com[64.233.167.109]:587, delay=0.41, delays=0.01/0.01/0.36/0.03, dsn=5.5.1, status=bounced (host smtp.gmail.com[64.233.167.109] said: 530 5.5.1 Authentication Required f6sm10746469pyh (in reply to MAIL FROM command))
Jul 23 16:54:54 Ubuntu postfix/qmgr[17069]: A3A7B115F7A: removed

Ok, I see some errors, but what do they mean?

---

### Post by Mr. C. on 2007-07-23
> **Warren Watts said:**
> Ok, I appended my cacert.pem onto ca-certificates.cat
changed main.cf to reflect change: 
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
and set the log level to 2:
smtp_tls_loglevel = 2
...
Ok, I see some errors, but what do they mean?

Ok, much better!  Now you are getting somewhere.  The errors are SSL trying to negotiate the correct protocol.  Ultimately, this is the important log line:


> 
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: TLS connection established to smtp.gmail.com: TLSv1 with cipher DES-CBC3-SHA (168/168 bits)

It says you *have* established the TLS connection.  This is the break through you needed.

Now, the next line indicates the next failure:

> 
Jul 23 16:54:53 Ubuntu postfix/smtp[17079]: EE1B7115F78: to=<kingbeetle_66@yahoo.com>, relay=smtp.gmail.com[64.233.167.109]:587, delay=0.74, delays=0.16/0.17/0.38/0.03, dsn=5.5.1, status=bounced (host smtp.gmail.com[64.233.167.109] said: 530 5.5.1 Authentication Required n44sm10809916pyh (in reply to MAIL FROM command))

Your server is not sending the SMTP AUTH command.  Why?  Because you haven't configured it to do so, as you did not copy the configuration accurately from the HowTo you used.  From man 5 postconf, we see:

> smtp_sasl_auth_enable (default: no)
       Enable SASL authentication in the Postfix SMTP client.  By default, the
       Postfix SMTP client uses no authentication.


So, you need to enable
   
```
**smtp**_sasl_auth_enable = yes
```

You have the server sasl auth enabled (**smtpd**_sasl_auth_enable), which is necessary to allow your MUA's to connect to your server.

It is exactly this type of error that makes following HowTo recipes so problematic: without understanding what is being configured you simply cannot figure out what is broken.  It is much better to configure one item at a time, and test that it works!

MrC

---

### Post by Warren Watts on 2007-07-23
Well, I am getting closer... :roll:

Now it says I don't have a worthy mech.....

> Jul 23 18:13:08 Ubuntu postfix/master[5435]: reload configuration /etc/postfix
Jul 23 18:13:09 Ubuntu postfix/master[5435]: terminating on signal 15
Jul 23 18:13:10 Ubuntu postfix/master[6020]: daemon started -- version 2.3.8, configuration /etc/postfix
Jul 23 18:13:11 Ubuntu postfix/pickup[6025]: 48C42115F9D: uid=1000 from=<warren>
Jul 23 18:13:11 Ubuntu postfix/cleanup[6030]: 48C42115F9D: message-id=<20070723221311.48C42115F9D@servehttp.com>
Jul 23 18:13:11 Ubuntu postfix/qmgr[6026]: 48C42115F9D: from=<warren@servehttp.com>, size=423, nrcpt=1 (queue active)
Jul 23 18:13:11 Ubuntu postfix/smtp[6032]: initializing the client-side TLS engine
Jul 23 18:13:11 Ubuntu postfix/tlsmgr[6033]: open smtpd TLS cache btree:/var/spool/postfix/smtpd_scache
Jul 23 18:13:11 Ubuntu postfix/tlsmgr[6033]: open smtp TLS cache btree:/var/spool/postfix/smtp_scache
Jul 23 18:13:11 Ubuntu postfix/tlsmgr[6033]: tlsmgr_cache_run_event: start TLS smtpd session cache cleanup
Jul 23 18:13:11 Ubuntu postfix/tlsmgr[6033]: tlsmgr_cache_run_event: start TLS smtp session cache cleanup
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: setting up TLS connection to smtp.gmail.com
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: looking for session smtp:64.233.167.111:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL in smtp cache
Jul 23 18:13:26 Ubuntu postfix/tlsmgr[6033]: lookup smtp session id=smtp:64.233.167.111:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:before/connect initialization
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv2/v3 write client hello A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv2/v3 read server hello A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read server hello A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read server hello A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 read server hello A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read server certificate A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read server certificate A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: certificate verification depth=1 subject=/C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: verify return: 1
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: certificate verification depth=0 subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: verify return: 1
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 read server certificate A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read server key exchange A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read server key exchange A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 read server done A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 write client key exchange A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 write change cipher spec A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 write finished A
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 flush data
Jul 23 18:13:26 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read finished A
Jul 23 18:13:27 Ubuntu last message repeated 3 times
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 read finished A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: save session smtp:64.233.167.111:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL to smtp cache
Jul 23 18:13:27 Ubuntu postfix/tlsmgr[6033]: put smtp session id=smtp:64.233.167.111:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL [data 992 bytes]
Jul 23 18:13:27 Ubuntu postfix/tlsmgr[6033]: write smtp TLS cache entry smtp:64.233.167.111:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL: time=1185228807 [data 992 bytes]
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: Verified: subject_CN=smtp.gmail.com, issuer=Thawte Premium Server CA
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: TLS connection established to smtp.gmail.com: TLSv1 with cipher DES-CBC3-SHA (168/168 bits)
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: warning: SASL authentication failure: No worthy mechs found
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: 48C42115F9D: SASL authentication failed; cannot authenticate to server smtp.gmail.com[64.233.167.111]: no mechanism available
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: setting up TLS connection to smtp.gmail.com
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: looking for session smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL in smtp cache
Jul 23 18:13:27 Ubuntu postfix/tlsmgr[6033]: lookup smtp session id=smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:before/connect initialization
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv2/v3 write client hello A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv2/v3 read server hello A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read server hello A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read server hello A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 read server hello A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read server certificate A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read server certificate A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: certificate verification depth=1 subject=/C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: verify return: 1
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: certificate verification depth=0 subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: verify return: 1
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 read server certificate A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read server key exchange A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read server key exchange A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 read server done A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 write client key exchange A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 write change cipher spec A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 write finished A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 flush data
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:error in SSLv3 read finished A
Jul 23 18:13:27 Ubuntu last message repeated 3 times
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: SSL_connect:SSLv3 read finished A
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: save session smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL to smtp cache
Jul 23 18:13:27 Ubuntu postfix/tlsmgr[6033]: put smtp session id=smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL [data 992 bytes]
Jul 23 18:13:27 Ubuntu postfix/tlsmgr[6033]: write smtp TLS cache entry smtp:64.233.167.109:587:mx.google.com&p=SSLv3,TLSv1&c=ALL:!EXPORT:!LOW:+RC4:@STRENGTH:!eNULL: time=1185228807 [data 992 bytes]
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: Verified: subject_CN=smtp.gmail.com, issuer=Thawte Premium Server CA
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: TLS connection established to smtp.gmail.com: TLSv1 with cipher DES-CBC3-SHA (168/168 bits)
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: warning: SASL authentication failure: No worthy mechs found
Jul 23 18:13:27 Ubuntu postfix/smtp[6032]: 48C42115F9D: to=<kingbeetle_66@yahoo.com>, relay=smtp.gmail.com[64.233.167.109]:587, delay=17, delays=0.23/0.17/16/0, dsn=4.7.0, status=deferred (SASL authentication failed; cannot authenticate to server smtp.gmail.com[64.233.167.109]: no mechanism available)

I tried to research that to see what it meant, but to no avail...  

May I call on you again for your knowledgeable assistance, Mr C.?

And thanks again for your patience...

---

### Post by Mr. C. on 2007-07-23
I think your HowTo tells you exactly what the problem is.  Search it for :

cannot SASL authenticate

What verison of SASL do you have ?

MrC

---

### Post by Warren Watts on 2007-07-23
I am using cyrus-sasl-2.1.22.

This whole thing is slowly driving me insane.....

---

### Post by Mr. C. on 2007-07-23
Understood - its not for the faint of heart.

What sasl library does ldd show in use for your smtp command ?

```
ldd /usr/libexec/postfix/smtp
```

MrC

---

### Post by Mr. C. on 2007-07-23
Additionally, try saslfinger to help provide diagnostic output:

[http://postfix.state-of-mind.de/patrick.koetter/saslfinger/](http://postfix.state-of-mind.de/patrick.koetter/saslfinger/)

You want client mode (-c).

MrC

---

### Post by Mr. C. on 2007-07-23
After pointing out that you missed some parameters from the HowTo, I expected that you'd check each and every one to see if others are missing... and there is.

You are missing:

```
smtp_sasl_security_options = noanonymous
```

The default option is noplaintext, noanonymous, which means that you will not allow plaintext passwords, which gmail requires over the TLS connection.  The setting in the guide overrides that default to disallow only anonymous SASL auth.

There are other security implications that you should learn about once you get your server up and running.  Consider purchasing The Book of Postfix.

MrC

---

### Post by Warren Watts on 2007-07-23
Mr. C:

  Thanks to your infinite patience and help, I finally got it configured properly and working.  I really, really couldn't have done it without you!

It has been quite a learning experience, let me tell you!

So again, thank you, and a general thank you to the entire Ubuntu Forum Community for being there, and being a valuable resource to everyone!!!!!

Woo Hoo!

---

### Post by Mr. C. on 2007-07-23
Glad to hear of your success.  Best of luck.

Cheers,
MrC

---

### Post by Oen386 on 2007-10-01
I am trying this myself, I hope it works. :)

---


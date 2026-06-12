---
title: "Postfix"
date: 2012-04-11
forum: Server Platforms
---

### Post by otherethe on 2012-04-11
Hello I'm having problems with my squirrelmail, It seems like my problem is in Postfix I've followed all of this [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) but no help when I try and send a email with Squirrel Mail I get this error Message not sent. Server replied:  Requested action aborted: error in processing
451 4.3.5 Server configuration error

Here is my /etc/postfix/main.cf

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

myhostname = server1.localhost.com
mydomain= mydomain.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, localhost.$mydomain, $mydomain
smtpd_banner = $myhostname ESMTP Mailserver
mailbox_size_limit = 0
message_size_limit = 10240000
smtpd_helo_required = yes
smtpd_helo_restrictions = reject_invalid_hostname
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_address
smtpd_client_restrictions = reject_invalid_hostname, reject_rbl_client relays.o rdb.org
strict_rfc821_envelopes = yes
home_mailbox = Maildir/

# TLS
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_enforce_tls = no
smtpd_tls_auth_only = no

# SASL (Simple Authentication and Security Layer)
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = 
smtp_sasl_auth_enable = no
broken_sasl_auth_clients = yes

mailbox_command = 
recipient_delimiter = +

mynetworks = 127.0.0.0/8
relayhost = 
inet_interfaces = all
inet_protocols = all
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom 
```

---

### Post by otherethe on 2012-04-11
Alright so I can send email now but I cant get it I've tried user@ip from a web based email server says it sends but I never get it on my cpu

---

### Post by otherethe on 2012-04-11
No body can help me? I can send emails but I can't receive them

---

### Post by lisati on 2012-04-11
*Thread moved to **Server Platforms**.*

Which guide did you use to install Squirrelmail? Are you able to post the last few entries from your mail log?

---

### Post by webservervideos on 2012-04-12
reject_rbl_client relays.o rdb.org   

that looks odd. 

smtpd_ssl_local.... is empty?



check your mail logs.  look for postfix spouting an error about something...

---

### Post by lisati on 2012-04-12
> **webservervideos said:**
> [COLOR="Red"]reject_rbl_client relays.o rdb.org [/COLOR]  

that looks odd. 

smtpd_ssl_local.... is empty?



check your mail logs.  look for postfix spouting an error about something...

Looks like a spurious space to me. +1 for checking the logs.

---

### Post by otherethe on 2012-04-12
I didn't find anything about Spouting I can how ever send mail to name@localhost now how ever but I can't send mail to name@127.0.0.1 and that does not make very much sense to me Here is the last few lines in my mail.log file

```
 postfix/smtpd: bad command startup -- throttling
Apr 12 18:59:09 othere-MS-7522 postfix/smtpd[13016]: fatal: parameter "smtpd_recipient_restrictions": specify at least one working instance of: check_relay_domains, reject_unauth_destination, reject, defer or defer_if_permit
Apr 12 18:59:10 othere-MS-7522 postfix/master[2023]: warning: process /usr/lib/postfix/smtpd pid 13016 exit status 1
Apr 12 18:59:10 othere-MS-7522 postfix/master[2023]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling 
```

---

### Post by lisati on 2012-04-12
> **otherethe said:**
> I didn't find anything about Spouting I can how ever send mail to name@localhost now how ever but I can't send mail to name@127.0.0.1 and that does not make very much sense to me Here is the last few lines in my mail.log file

```
 postfix/smtpd: bad command startup -- throttling
Apr 12 18:59:09 othere-MS-7522 postfix/smtpd[13016]: fatal: parameter "smtpd_recipient_restrictions": specify at least one working instance of: check_relay_domains, reject_unauth_destination, reject, defer or defer_if_permit
Apr 12 18:59:10 othere-MS-7522 postfix/master[2023]: warning: process /usr/lib/postfix/smtpd pid 13016 exit status 1
Apr 12 18:59:10 othere-MS-7522 postfix/master[2023]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling 
```

Forget about the kind of spouting that collects rainwater. There is an error in the part of main.cf which says:
```
reject_rbl_client relays.o rdb.org
```

It contains a space that shouldn't be there, which is why postfix is complaining ("spouting an error") about "smtpd_recipient_restrictions" It should be:
```
reject_rbl_client relays.ordb.org
```

---

### Post by otherethe on 2012-04-12
> **lisati said:**
> Forget about the kind of spouting that collects rainwater. There is an error in the part of main.cf which says:
```
reject_rbl_client relays.o rdb.org
```It contains a space that shouldn't be there, which is why postfix is complaining ("spouting an error") about "smtpd_recipient_restrictions" It should be:
```
reject_rbl_client relays.ordb.org
```


Just fixed the space restarted postfix tried to send a email to name@127.0.0.1 didn't get it also tried to send a mail to name@ip didn't get it

---

### Post by otherethe on 2012-04-12
Ok so I just watched my mail log as i tried to send a email to my self via name@ip
heres what I got in the mail.log I changed the name and the ip to othere and ip address

```
 from=<othere@127.0.0.1>, size=606, nrcpt=1 (queue active)
Apr 12 19:32:34 othere-MS-7522 postfix/error[4603]: 509E55E05D9: to=<othere@IP address>, relay=none, delay=0.35, delays=0.26/0/0/0.09, dsn=5.1.3, status=bounced (bad address syntax)
Apr 12 19:32:34 othere-MS-7522 postfix/cleanup[4597]: 9ED7F5E05DA: message-id=<20120412233234.9ED7F5E05DA@localhost>
Apr 12 19:32:34 othere-MS-7522 postfix/bounce[4604]: 509E55E05D9: sender non-delivery notification: 9ED7F5E05DA
Apr 12 19:32:34 othere-MS-7522 postfix/qmgr[3877]: 9ED7F5E05DA: from=<>, size=2317, nrcpt=1 (queue active)
Apr 12 19:32:34 othere-MS-7522 postfix/qmgr[3877]: 509E55E05D9: removed
Apr 12 19:32:34 othere-MS-7522 postfix/error[4603]: 9ED7F5E05DA: to=<othere@127.0.0.1>, relay=none, delay=0.27, delays=0.18/0/0/0.09, dsn=5.1.3, status=bounced (bad address syntax)
Apr 12 19:32:34 othere-MS-7522 postfix/qmgr[3877]: 9ED7F5E05DA: removed 
```

---

### Post by SeijiSensei on 2012-04-12
You need to send to name@[127.0.0.1] if you want to use an IP address as the domain part.

---

### Post by otherethe on 2012-04-13
> **SeijiSensei said:**
> You need to send to name@[127.0.0.1] if you want to use an IP address as the domain part.

alright so that worked to send mail to my self but if i try it from say gmail it doesn't send the mail gmail says this 

The address "othere@[ip address]" in the "To" field was not  recognized. Please make sure that all addresses are properly formed.

---

### Post by SeijiSensei on 2012-04-13
That's a gmail issue.  I'm not surprised they don't support IP-based pseudo-domains.

---

### Post by lisati on 2012-04-13
> **otherethe said:**
> alright so that worked to send mail to my self but if i try it from say gmail it doesn't send the mail gmail says this 

The address "othere@[ip address]" in the "To" field was not  recognized. Please make sure that all addresses are properly formed.

gmail could be expecting the email addresses in the form *others@gmail.com* like you would use when using webmail or an email client.

---

### Post by SeijiSensei on 2012-04-13
He has the IP address in the To: field.  In principle, that should work, as it's defined in [RFC 2821]("http://tools.ietf.org/html/rfc2821#section-4.1.3").  Sadly, these days conforming to RFCs isn't as common as it once was because of spamming.  

Just as a test, I sent myself an email from a Linux server I maintain to my own inbound SMTP server using that server's IP address.  It appeared in my inbox with my username and the server's FQDN replacing the [IP] pseudo-domain.  Both these machines are running sendmail.

I'd guess it's more of a defense on Google's part against spammers sending thousands of messages to [email]user@[ip.addr.of.target[/email]].

---

### Post by otherethe on 2012-04-13
> **SeijiSensei said:**
> He has the IP address in the To: field.  In principle, that should work.

Just as a test, I sent myself an email from a Linux server I maintain to my own inbound SMTP server using that server's IP address.  It appeared in my inbox with my username and the server's FQDN replacing the [IP] pseudo-domain.  Both these machines are running sendmail.

I'd guess it's more of a defense on Google's part against spammers sending thousands of messages to [email]user@[ip.addr.of.target[/email]].
I just tried to send my self a email from [http://www.sendanonymousemail.net/send.php](http://www.sendanonymousemail.net/send.php)
It says it sent but I never got it can you try and send a email to this address to see if I get it?


othere@[ip address]
I'll pm the info if you gonna do it

---

### Post by SeijiSensei on 2012-04-13
I get "stat=Deferred: Connection reset by [75.106.165.143]".  

If I telnet to port 25 at that address, I get a connection but no response from the Postfix daemon.  It just hangs rather than giving me a  "banner" confirming that the server is listening and awaiting SMTP commands like this:

```
220 mail.example.com ESMTP Sendmail 8.13.8/8.13.8; Fri, 13 Apr 2012 17:31:19 -0400
```

This is the banner from standard sendmail; the Postfix banner has slightly different text, as I recall, but I should still get a "220" response.

---

### Post by otherethe on 2012-04-13
> **SeijiSensei said:**
> I get "stat=Deferred: Connection reset by [75.106.165.143]".  Either the port is closed or Postfix isn't listening.

If I telnet to port 25 at that address, I get a connection but no response from the MTA daemon.  It just hangs after confirming the connection.  I should get a "banner" confirming that the server is listening and awaiting SMTP commands.
I seen were you were trying to connect at first My firewall was blocking it but once i seen you trying to connect I opened the port thats how come you could telnet to it It's also why it was blocked at first sorry about that

---

### Post by SeijiSensei on 2012-04-13
> **otherethe said:**
> I seen were you were trying to connect at first My firewall was blocking it but once i seen you trying to connect I opened the port thats how come you could telnet to it It's also why it was blocked at first sorry about that

I get the same result.  I can connect but it hangs.

---

### Post by otherethe on 2012-04-13
> **SeijiSensei said:**
> I get the same result.  I can connect but it hangs.
I find that very odd I may have screwed something up because my telnet localhost 25 is hanging as well I'm going to try a reboot to see if it fix that

---

### Post by otherethe on 2012-04-13
> **otherethe said:**
> I find that very odd I may have screwed something up because my telnet localhost 25 is hanging as well I'm going to try a reboot to see if it fix that
I think I fixed it I rebooted and it still hung up so I edited the config files I can now connect via localhost and ip via telnet 25 and shows the banner can you confirm??? and try to send a email now

---

### Post by otherethe on 2012-04-14
> **otherethe said:**
> I think I fixed it I rebooted and it still hung up so I edited the config files I can now connect via localhost and ip via telnet 25 and shows the banner can you confirm??? and try to send a email now
alright I found a few websites who send email with no dns look up and it sent to me the [ ] is really all I needed that and to reconfigure postfix i messed it up pretty bad trying to twink it lmfao I'm not sure how to close these so ;0

---


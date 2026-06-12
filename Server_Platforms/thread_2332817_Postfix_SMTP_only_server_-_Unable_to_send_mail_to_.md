---
title: "Postfix SMTP only server - Unable to send mail to own domain"
date: 2016-08-04
forum: Server Platforms
---

### Post by chris-lech on 2016-08-04
Sorry for the post if in the wrong area...

Hopefully I can get a little help with the issue I am facing. I'm running the latest Postfix version on Ubuntu Server and having issues with the /etc/postfix/[main.cf]("http://main.cf/") configuration for the purpose of have a simple SMTP only server(not to receive mail). 

I am using telnet to server locally and have tested externally to the server and let's me in all ok. But when I try to send mail back to the domain it is hosted on, it fails with connection refused. 

Emailing out to all other external domains work.. for example I am doing this when testing to send email to my own domain: 

HELO [mydomain.co.uk]("http://mydomain.co.uk/") 
MAIL FROM: [EMAIL="me@mydomain.co.uk"]me@mydomain.co.uk[/EMAIL] 
RCPT TO: [EMAIL="support@mydomain.co.uk"]support@mydomain.co.uk[/EMAIL] 
DATA 
Subject: some text 
some text 
. 

Output of /var/log/mail.log is: 

Aug  4 12:45:20 ubuntu postfix/master[2710]: daemon started -- version 2.11.0, configuration /etc/postfix 
Aug  4 12:45:30 ubuntu postfix/smtpd[2718]: connect from localhost[::1] 
Aug  4 12:45:51 ubuntu postfix/smtpd[2718]: A36451A0B36: client=localhost[::1] 
Aug  4 12:46:01 ubuntu postfix/cleanup[2721]: A36451A0B36: message-id=<20160804114551.A36451A0B36@smtp.mydomain.co.uk.$ 
Aug  4 12:46:01 ubuntu postfix/qmgr[2714]: A36451A0B36: from=<[EMAIL="me@mydomain.co.uk"]me@mydomain.co.uk[/EMAIL]>, size=352, nrcpt=1 (que$ 
Aug  4 12:46:01 ubuntu postfix/smtp[2722]: connect to mydomain[.co.uk]("http://idnonline.co.uk/")[192.168.2.253]:25: Connection refused 
Aug  4 12:46:01 ubuntu postfix/smtp[2722]: connect to [mydomain.co.uk]("http://idnonline.co.uk/")[192.168.2.251]:25: Connection refused 
Aug  4 12:46:01 ubuntu postfix/smtp[2722]: A36451A0B36: to=<[EMAIL="support@mydomain.co.uk"]support@mydomain.co.uk[/EMAIL]>, relay=none, delay=18, delay$ 
Aug  4 12:46:16 ubuntu postfix/smtpd[2718]: disconnect from localhost[::1] 


Here is the output of /etc/postfix/[main.cf]("http://main.cf/") : 

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

readme_directory = no 

# TLS parameters 
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem 
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key 
smtpd_use_tls=yes 
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache 
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache 

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for 
# information on enabling SSL in the smtp client. 

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination 
myhostname = [smtp.]("http://smtp.idnonline.co.uk/")mydomain.co.uk
alias_maps = hash:/etc/aliases 
alias_database = hash:/etc/aliases 
myorigin = /etc/mailname 
mydestination = 
relayhost = 
mynetworks = [127.0.0.0/8]("http://127.0.0.0/8") [::ffff:127.0.0.0]/104 [::1]/128 
mailbox_size_limit = 0 
recipient_delimiter = + 
inet_interfaces = loopback-only 
inet_protocols = all 
local_recipient_maps = 

Ports are open on the router. 

The reason I need to send mail back is because we have external client that need a basic SMTP server to send notification emails to our [EMAIL="monitor@mydomain.co.uk"]monitor@mydomain.co.uk[/EMAIL] mailbox. 

Any help appreciated. 










[FONT=Arial][/FONT]
[FONT=Arial][/FONT][FONT=Arial][/FONT]

---

### Post by Graham_Willis on 2016-08-05
Which is the case:

1. You have two machines, server1 and server2, on server1 you have SMTP server that you described in your post, but the domain's delegated to server2. If that's the case to which server does MX record of mydomain.co.uk point to?
2. The domain mydomain.co.uk is on the same server as SMTP server that you described in your post.

Also, from what you wrote I understand that the problem occurs when you're sending mails from mydomain.co.uk from your SMTP server to mydomain.co.uk - is that correct?

Now, the logs that you presented suggest that your server isn't even able to connect to a SMTP port of the destination server. Does telnet procedure confirm that it's the case? For me it's striking that in logs we can see that it tries to connect to the destination server using an IP local to your network (192.168.2.253). Is it expected? Does SMTP daemon listen on this address at all? Second, it's common to block the port 25 these days, so it's also something worth looking more closely.

---

### Post by chris-lech on 2016-08-08
Hi

Thanks for the response. I have a virtual Ubuntu server running, the aim is to just have it as an outgoing SMTP server. We have the domain mail.mydomain.co.uk MX records pointing at our MS Exchange 2010 server for receiving and sending mail pointing at one of our public IP addresses. I don't want to touch this and we need to set a new basic SMTP server just for sending out notifications(which is the purpose of the Ubuntu SMTP server)

So, from a customer server the RAID notification email uses the above Ubuntu server, outgoingsmtp.mydomain.co.uk and sends the notification to [email]monitor@mydomain.co.uk[/email].

I hope that makes sense to anyone! The reason being is that the SMTP server that our customers use are soon going to stop working, so we need to replace it with something else.

---

### Post by chris-lech on 2016-08-08
> **Graham_Willis said:**
> 
Also, from what you wrote I understand that the problem occurs when you're sending mails from mydomain.co.uk from your SMTP server to mydomain.co.uk - is that correct?

Now, the logs that you presented suggest that your server isn't even able to connect to a SMTP port of the destination server. Does telnet procedure confirm that it's the case? For me it's striking that in logs we can see that it tries to connect to the destination server using an IP local to your network (192.168.2.253). Is it expected? Does SMTP daemon listen on this address at all? Second, it's common to block the port 25 these days, so it's also something worth looking more closely.


TO answer these questions, for example if I telnet localhost 25 then:

```
HELO mydomain.co.uk
MAIL FROM: chris.lech@mydomain.co.uk
RCPT TO: support@mydomain.co.uk
DATA
SUBJECT: This a test email
Main text
.

```

It then say's it's queued and looks all ok.

But as in the logs above the connection is refused on 192.168.2.253 which is our internal domain controller? Which I don't understand why this is being contacted! May DNS on the DC? Not sure, I'll check.

Perhaps it is also blocked, I will ask the ISP.

Thanks.

---

### Post by Graham_Willis on 2016-08-08
It's a bit strange to me, in my opinion once you successfully telneted to the port 25, it should either deliver the message or return the info what has gone wrong. What you're describing suggests that your mail server's (the one that you telneted) acting as a relay. Is it desired? What's the output of **dig mydomain.co.uk** **MX **? The most relevant part is what nameserver's contacted, but check if **dig mydomain.co.uk A** , **dig *mxserver* A **also return the expected results (look for both the nameserver being contacted and the IP). Try to change the IP addresses seen by your mail server of both mydomain.co.uk and the MX domain of mydomain.co.uk to the intended ones using **/etc/hosts** file. Does it bring any changes? Can you set DNS servers that your SMTP server use to a public DNS server for just a while and check (but be sure to flush DNS cache of that new mail server earlier) if it changes anything? Also useful may be tracking network traffic with tcpdump, it may help to establish what's going on. Another thing that comes to my mind is to try to telnet to the port 587 instead of 25.

---

### Post by SeijiSensei on 2016-08-09
You don't have anything specified in the "mydestination" field.  To accept mail for [email]someone@mydomain.co.uk[/email], you need at least
```

mydestination = mydomain.co.uk

```
You may want other names there as well.  Read [http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination](http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination).  You probably want example 2, a domain-wide mail server:
```

mydestination = $myhostname localhost.$mydomain localhost $mydomain

```

---


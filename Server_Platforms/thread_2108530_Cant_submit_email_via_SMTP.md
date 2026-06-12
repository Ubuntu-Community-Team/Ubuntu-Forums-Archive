---
title: "Cant submit email via SMTP"
date: 2013-01-24
forum: Server Platforms
---

### Post by Ayuniverse on 2013-01-24
Hi,

I run a web server based on Ubuntu 12.04. I have installed and configured Postfix + Courier. I can receive my emails sent from other domains, but I can't manage to make SMTP works.

When I try to send an email via my server using Thunderbird (port 587, SASL), it asks for my password (only the first time), and then I get the most interesting error message of all time :

> The message could not be sent using SMTP server mail.mydomain.com for an unknown reason                      When I look at my mail.log, I only see this :

> Jan 24 02:50:23 user postfix/smtpd[17749]: connect from CPE002401cd0a51-CM0014e8b60462.cpe.net.cable.rogers.com[174.116.235.177]
Jan 24 02:50:27 user postfix/smtpd[17749]: disconnect from  CPE002401cd0a51-CM0014e8b60462.cpe.net.cable.rogers.com[174.116.235.177]                      Any idea why it doesn't work ? 

Port 587 is open in ufw.

If you can help me, thank you !

Btw, I found this in my syslog :

> Jan 24 02:50:23 user named[3448]: client 127.0.0.1#33804: query (cache)  'CPE002401cd0a51-CM0014e8b60462.cpe.net.cable.rogers.com/A/IN' **denied**
Jan 24 02:50:23 user named[3448]: client 127.0.0.1#60301: query (cache)  'CPE002401cd0a51-CM0014e8b60462.cpe.net.cable.rogers.com/A/IN' **denied**Don't know if it's helpful !

---

### Post by SeijiSensei on 2013-01-24
Are you trying to send mail to that Rogers address?  If so, they are probably blocking inbound traffic on port 25 to enforce a no-servers rule.  (It sounds to me like your port 587 connection is to the web server.  When the message is sent to the Rogers address, it should be arriving on port 25.)  Most residential connections have such a rule in their terms of service.

But just to make sure, is port 25 open on the Rogers connection?  What happens if you try "telnet 174.116.235.177 25" from the web server?  I'll bet you cannot connect.  Neither can I.  Either you have it blocked, or Rogers is blocking it.

---

### Post by Ayuniverse on 2013-01-24
Hi and thank you for your answer.

This Rogers address is mine, the one from which I'm trying to send the email.

---

### Post by SeijiSensei on 2013-01-24
> **Ayuniverse said:**
> Hi and thank you for your answer.

This Rogers address is mine, the one from which I'm trying to send the email.

If you are trying to send a message to a remote server, then they are probably blocking outbound email connections.  As a test try "telnet name.of.remote.server 25" or "telnet name.of.remote.server 587" to see if you can connect to those ports at all.  You can use alt1.gmail-smtp-in.l.google.com for testing if you like.

---

### Post by Ayuniverse on 2013-01-24
I can connect to 587 port, not 25.

> 
250-name.of.remote.server 
250-PIPELINING
250-SIZE 10485760
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN


---

### Post by Ayuniverse on 2013-01-26
up ?

---

### Post by SeijiSensei on 2013-01-26
Does the "mynetworks" directive in Postfix's main.cf file include 127.0.0.0/8 as a permitted network?

I suggest reading [this document](http://www.postfix.org/BASIC_CONFIGURATION_README.html) on how to configure Postfix.  Pay special attention to the section entitled "What clients to relay mail from".

---

### Post by Ayuniverse on 2013-01-27
> **SeijiSensei said:**
> Does the "mynetworks" directive in Postfix's main.cf file include 127.0.0.0/8 as a permitted network?

yes it does.

---


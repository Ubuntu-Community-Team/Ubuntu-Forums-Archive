---
title: "Postfix SMTP email server works with STARTTLS but not TLS"
date: 2014-01-16
forum: Security
---

### Post by Matthew_Snyder on 2014-01-16
I am wondering if anyone here has any experience with mail servers.  I have created my own mail server with my own registered domain, and overall it works fairly well.  I use a courier pop3 server for incoming mail, and it works fine with TLS or SSL.  My outgoing mail however will not work with TLS or SSL.  With Thunderbird I can send and receive mail just fine with the outgoing server set to STARTTLS, but when I switch to the TLS/SSL setting the outgoing mail fails to send.

The mail client just hangs forever trying to contact the server.  My mail.log only says that connection is successful, and nothing else.  When I finally tell the send mail operation to cancel because it obviously isn't working, the mail.log just says client disconnected.

Does anyone know why a STARTTLS setting would work but TLS/SSL setting wouldn't?

Any help is appreciated.

---

### Post by TheFu on 2014-01-16
Details?  That would be exact configurations and exact log messages. Which ports are being used for each connection might be helpful too. [http://www.postfix.org/TLS_README.html](http://www.postfix.org/TLS_README.html) explains how to turn up the logging to get more data, if needed.

I'd also ask if there some reason that STARTTLS is not good enough for your needs?

---

### Post by CharlesA on 2014-01-16
> **TheFu said:**
> 
I'd also ask if there some reason that STARTTLS is not good enough for your needs?

I'm curious as well. My mail server uses TLS for Dovecot, but STARTTLS for postfix and I think that's fine as far as security goes. As long as the password isn't being sent in plain text, you should be fine.

---

### Post by TheFu on 2014-01-16
I thought that STARTTLS was a way to have either cleartext or TLS encryption on the same port.  So without STARTTLS, then 2 ports would need to be advertised for TLS encrypted traffic between email servers. Don't know off the top of my head how to accomplish that without a transport map for every server - perhaps I'm missing something?  For clients-to-server connections, it is common to send SMTPS traffic over port 465 and IMAPS traffic over port 993.  Checking my /etc/services file ... looks like server-to-server SSL encrypted SMTP uses 465 too.  So, if that port isn't open to the WAN traffic ... that could be it?

---

### Post by CharlesA on 2014-01-16
> **TheFu said:**
> I thought that STARTTLS was a way to have either cleartext or TLS encryption on the same port.  So without STARTTLS, then 2 ports would need to be advertised for TLS encrypted traffic between email servers. Don't know off the top of my head how to accomplish that without a transport map for every server - perhaps I'm missing something?  For clients-to-server connections, it is common to send SMTPS traffic over port 465 and IMAPS traffic over port 993.  Checking my /etc/services file ... looks like server-to-server SSL encrypted SMTP uses 465 too.  So, if that port isn't open to the WAN traffic ... that could be it?

I have mine set to listen for SMTP connections on port 25 and port 587 (submission port). Port 25 is used for server-to-server mail transfer while port 587 is used for client connections.

Not sure about the whole TLS vs STARTTLS thing, but I found [this page]("http://rene.bz/setting-smtp-authentication-over-tls-postfix/") in my history and I've got my server set up to use STARTTLS on port 587 and port 25, when I tested it with telnet.

[Linode tutorial]("https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql") ftw, apparently.

---

### Post by s-stefanov on 2014-12-08
Took me a while to figure this one out. In master.cf put a** -o smtpd_tls_wrappermode=yes** for the service on which you want "true" TLS. STARTTLS must be avoided by all means as attackers can use it to force the clients to submit their passwords in cleartext.

---


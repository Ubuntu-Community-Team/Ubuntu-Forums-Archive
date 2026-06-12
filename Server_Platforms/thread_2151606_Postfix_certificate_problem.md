---
title: "Postfix certificate problem"
date: 2013-06-05
forum: Server Platforms
---

### Post by zee on 2013-06-05
Hello,
  I'm setting up a mail server that would relay email to the ISP's SMTP server, but the problem I'm facing is that the SMTP server uses STARTTLS for authentication and I have no idea how to import the certificate into the system. If I use the ISP's SMTP server in Thunderbird I have to manually accept the ISP's SMTP server certificate. I expect I must do the same but via the command line. How?

  If I try to send an email using sendmail, I get the following error in /var/log/mail.log:
Jun  5 17:07:45 erwin postfix/smtp[18908]: certificate verification failed for isp.server[IP address]:587: untrusted issuer /CN=s3-cas02
Jun  5 17:07:45 erwin postfix/smtp[18908]: Untrusted TLS connection established isp.server[IP address]:587: TLSv1 with cipher AES128-SHA (128/128 bits)
Jun  5 17:07:45 erwin postfix/smtp[18908]: E12D51E3090: to=<user@email.com>, relay=isp.server[IP address]:587, delay=5831, delays=5830/0.23/0.1/0, dsn=4.7.5, status=deferred (Server certificate not trusted)

NB: I replaced the actual values with isp.server, IP address, [email]user@email.com[/email].

  How do I fix this? I'm using Postfix in Ubuntu 12.04.

Thanks in advance,
zee

---

### Post by linuxtechguy on 2013-06-05
Maybe your isp doesnt support ssl.

---

### Post by zee on 2013-06-05
Hi,
  I don't think SSL is not the problem as the ISP is not using it.
  
  The settings ISP's for SMTP I use in Thunderbird are:
name: smtp.server.name
port: 587
connection security: STARTTLS (other choices include None and SSL/TLS).
authentication method: Normal password

---

### Post by zee on 2013-06-10
I fixed the issue by exporting the certificate from Thunderbird, then I copied it to /etc/ssl/certs/. Afterwards I ran update-ca-certificates and copied the resulting CRT file to /var/spool/postfix/certs/.

Then I edited the /etc/postfix/main.cf by adding the following lines:
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_tls_security_level=may

---


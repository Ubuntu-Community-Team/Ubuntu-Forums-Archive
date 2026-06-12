---
title: "Is it still possible to smtp relay through gmail?"
date: 2012-03-11
forum: Server Platforms
---

### Post by kevdog on 2012-03-11
I've tried various tutorials around the web in order to smtp relay through gmail using TLS,creating self signed certificate, etc.  All I ever received in the logs was something like this:

relay=gmail-smtp-in.l.google.com[209.85.225.27]:25, delay=1.3, delays=0.04/0/0.49/0.78, dsn=5.7.1, status=bounced (host gmail-smtp-in.l.google.com[209.85.225.27] said: 550-5.7.1 [xxx.xxx.xxx.xxx] The IP you're using to send mail is not authorized to 550-5.7.1 send email directly to our servers. Please use the SMTP relay at your 550-5.7.1 service provider instead. Learn more at 550 5.7.1 [http://support.google.com/mail/bin/answer.py?answer=10336](http://support.google.com/mail/bin/answer.py?answer=10336) wm4si10830874igb.53 (in reply to end of DATA command))

I'm just wondering if this feature has been disabled?

---

### Post by CharlesA on 2012-03-12
Yes it's still possible. What SMTP server are you using? I've had success with Postfix and Exim and I believe that using Postfix is more secure, as exim required me having the gmail password sitting there in clear text.

---

### Post by kevdog on 2012-03-12
Charles 

Thanks for getting back to me.  I was trying for TLS over port 587 but it wasn't working.  It could be my postfix setup for sure.

I know that port 465 using SSL does in fact work -- I found this out after writing the post.  I'm trying to write my main.cf file for this setup.  I'd really like to do TLS, however if this doesn't work I'm going to have to fall back on SSL.

---

### Post by CharlesA on 2012-03-12
Easy.

Purge postfix and reinstall it, create a sasl_passwd in /etc/postfix, and hash it then add this to the end of main.cf:

```
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
# Secure channel TLS with exact nexthop name match.
smtp_tls_security_level = secure
smtp_tls_mandatory_protocols = TLSv1
smtp_tls_mandatory_ciphers = high
smtp_tls_secure_cert_match = nexthop
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
relayhost = smtp.gmail.com:587

```

Restart postfix and you should be good to go.

I used the same steps to get it up on CentOS, but had to modify the code to point to where Ubuntu stores its SSL certs.

See [here]("http://charlesa.net/tutorials/centos/centosgmail.php") for more-or-less step-by-step directions, just replace yum with apt-get.

---

### Post by kevdog on 2012-03-14
Thanks for advice... Your recommendations really worked.

---

### Post by CharlesA on 2012-03-14
Glad it worked out for you. :)

---


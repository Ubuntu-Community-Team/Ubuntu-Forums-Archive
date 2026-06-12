---
title: "Viewing Old Certificate in e-mail"
date: 2009-03-31
forum: Server Platforms
---

### Post by taberski on 2009-03-31
I finally got around to installing and e-mail server using Postfix and Dovecot.  I'm now at the point where I can send and receive e-mail via 'mutt' from a shell and also send and receive e-mail via Thunderbird on a Windows based machine.

I have a static IP and domain name (which works) and am currently using POP3 protocol using TLS (if available).

I believe that I have set up the certificates correctly (following the various server related "how-to's" and the certificates in /etc/ssl/certs and /etc/ssl/private have recent dates.  I also seems to have /etc/postfix/main.cf configured correctly to use these.

When I run Thunderbird, I get a "Server Certificate Expired" warning.  The certificate is dated back when I originally installed Ubuntu (6.06LTS) 2 years ago!

My question is, where would this seemingly "rogue" certificate reside, which package is accessing it and how can I convince the server to point to the one I recently created?

Thank you,

Kevin

---

### Post by kvizz on 2009-03-31
have you reloaded your mail server after changing your main.cf, do you have these lines in main.cf:
smptpd_tls_cert_file =
smtpd_tls_key_file = 
and they are pointing to your new keys?

---

### Post by taberski on 2009-03-31
Yes to all - I just can't see where the server is getting the older certificates.  Is there typically a default set somewhere other than /etc/ssl that would be used if main.cf is not configured correctly?

---

### Post by kvizz on 2009-04-01
might be dovecot is not using new certificates?
check [http://wiki.dovecot.org/SSL/DovecotConfiguration](http://wiki.dovecot.org/SSL/DovecotConfiguration)

---

### Post by taberski on 2009-04-01
OK - that seemed to help.  I had been holding off on enabling SSL in Dovecot because I had thought this was different (or in addition to) TLS and only used with pop3s or imaps (which I still plan to try).  Plus I was a bit thrown by the "snakeoil" certificate and key.

So now my question is, how (or why) are there certificates in both Postfix and Dovecot and what are the differences/interactions between TLS and SSL?

I still would like to know where Postfix/Dovecot found the old/original certificates.

There is much to learn!

Thank you,

Kevin

---


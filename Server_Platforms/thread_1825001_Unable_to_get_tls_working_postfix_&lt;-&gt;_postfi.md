---
title: "Unable to get tls working postfix &lt;-&gt; postfix, permit_tls_clientcerts not working?"
date: 2011-08-14
forum: Server Platforms
---

### Post by azzid on 2011-08-14
I have two servers, one properly on the internet (static ip and so forth) and one on a run of the mill broadband connection.

The later one is not allowed to make connections to port 25 on the internet, so my goal is to set the first one up as a relay for the second one.

I've managed to send a few e-mails by addressing them to local accounts on the machine on the internet, so I believe that my relay settings are fine.

What I seem unable to achieve is to have the internetmachine work as an open relay for the machine at home provided only that the machine at home presents itself with a tls certificate.

I've been able to create certificates, and I've been able to send mails even after the internetserver started asking for me to STARTTLS.

The smtp listener in master.cf on the relay is configured like so:
```

submission inet n       -       -       -       -       smtpd
  -o smtpd_tls_security_level=encrypt
  -o smtpd_tls_ask_ccert=yes
  -o relay_clientcerts=hash:/etc/postfix/clientcerts
  -o smtpd_recipient_restrictions=permit_tls_clientcerts,reject_unauth_destination

```

I've created the clientcerts and calculated the thumbprint for the certificate on the connecting server. I've also run postmap on the file and reloaded postfix.

I've configured the server at home like so:
```
smtp_use_tls=yes
smtp_tls_key_file=/etc/postfix/mailkey.pem
smtp_tls_cert_file=/etc/postfix/mail_signed_cert.pem
smtp_tls_CAfile=/etc/postfix/cacert.pem

```

I believe that should make it present its certificate when connecting.

I thought permit_tls_clientcerts would make the connecting machine trused and hence relay anything from it, but it does not seem to work.

Any help is appreciated.

---

### Post by azzid on 2011-08-26
Figured it out.

There is a good setting to help troubleshoot this.

I put the following in the servers main.cf:
```
smtpd_tls_loglevel=1
```

After that I found the fingerprint my "client" use to identify itself. It was not the one I had in my clientcerts.

I updated my clientcerts, ran postmap on it and reloaded postfix.

Now everything is working.

---


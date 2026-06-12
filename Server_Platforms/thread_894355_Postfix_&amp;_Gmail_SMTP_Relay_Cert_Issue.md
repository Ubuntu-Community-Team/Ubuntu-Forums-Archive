---
title: "Postfix &amp; Gmail SMTP Relay Cert Issue"
date: 2008-08-19
forum: Server Platforms
---

### Post by adam35413 on 2008-08-19
I use Postfix configured to send through Gmail's smtp relay for all of my email needs on my server.  This was configured correctly and working fine till a couple days ago.  When I attempt to send emails now, I get the following message:

```
Aug 19 07:50:58 ubuntu-server postfix/qmgr[6840]: 4D88D27C42E: from=<root@myserver.com>, size=351, nrcpt=1 (queue active)

Aug 19 07:50:59 ubuntu-server postfix/smtp[17369]: setting up TLS connection to smtp.gmail.com[72.14.205.109]:587
Aug 19 07:50:59 ubuntu-server postfix/smtp[17369]: certificate verification failed for smtp.gmail.com[72.14.205.109]:587: untrusted issuer /C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
Aug 19 07:50:59 ubuntu-server postfix/smtp[17369]: Untrusted TLS connection established to smtp.gmail.com[72.14.205.109]:587: TLSv1 with cipher RC4-MD5 (128/128 bits)
Aug 19 07:50:59 ubuntu-server postfix/smtp[17369]: 4D88D27C42E: Server certificate not trusted

```

This is extremely strange however because I changed the CA cert to Equifax back in July when Gmail switched away from Thawte.  I have changed the CA cert in cacert.pem several times today, but whenever I check the mail logs it stays on the Thawte Permium Server certificate.  Does anyone know what could be going on?

---

### Post by MJN on 2008-08-19
The CA, Thawte, is the signing authority for GMail's certificate - not yours. The verification is failing (but still continuing) because you do not trust Thawte (or this particular root of theirs). From what you have said it sound slike GMail have gone back to using a Thawte certificate (or at least this particular machine you're connecting to does).
 
You need to add Thawte's CA certificate (downloadable from them) to your CAcert.pem file.
 
Mathew

---

### Post by adam35413 on 2008-08-19
I put the Thawte Premium Server CA in my cacert.pem file in place of the Equifax cert.  Others might want to be aware of the change in gmail's smtp cert structure.

---

### Post by haximusprime on 2009-03-08
I know this thread is kind of old, but I'm having the same problem, and I was wondering if anyone can tell me more or less 'step by step' how to fix it. 

```

Mar  8 12:49:38 localhost postfix/master[7415]: terminating on signal 15
Mar  8 12:49:46 localhost postfix/master[7563]: daemon started -- version 2.5.5, configuration /etc/postfix
Mar  8 12:50:00 localhost postfix/pickup[7569]: E28184AC2B3: uid=1000 from=<nick>
Mar  8 12:50:01 localhost postfix/cleanup[7582]: E28184AC2B3: message-id=<20090308165000.GA7571@posthumous.ath.cx>
Mar  8 12:50:01 localhost postfix/qmgr[7570]: E28184AC2B3: from=<nick@posthumous.ath.cx>, size=435, nrcpt=1 (queue active)
Mar  8 12:50:02 localhost postfix/smtp[7584]: certificate verification failed for smtp.gmail.com[209.85.147.109]:587: untrusted issuer /C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
Mar  8 12:50:03 localhost postfix/smtp[7584]: E28184AC2B3: to=<doublebirdstrike@aim.com>, relay=smtp.gmail.com[209.85.147.109]:587, delay=2.9, delays=0.37/0.51/1.4/0.59, dsn=2.0.0, status=sent (250 2.0.0 OK 1236531003 n33sm3195352wag.53)
Mar  8 12:50:03 localhost postfix/qmgr[7570]: E28184AC2B3: removed
Mar  8 12:53:46 localhost in.qpopper[7596]: (v4.0.9) Servicing request from "yw-out-2526.google.com" at 74.125.46.32 [pop_init.c:1408]
Mar  8 12:53:46 localhost in.qpopper[7596]: (null) at yw-out-2526.google.com (74.125.46.32): -ERR POP EOF or I/O Error [popper.c:828]
Mar  8 12:53:46 localhost in.qpopper[7597]: (v4.0.9) Servicing request from "yw-out-2526.google.com" at 74.125.46.35 [pop_init.c:1408]
Mar  8 12:53:46 localhost in.qpopper[7597]: Unable to open bulletin directory '/var/spool/popbull': No such file or directory (2) [pop_bull.c:386]
Mar  8 12:53:46 localhost in.qpopper[7597]: (v4.0.9) POP login by user "nick" at (yw-out-2526.google.com) 74.125.46.35 [pop_log.c:244]
Mar  8 12:54:32 localhost postfix/pickup[7569]: 2EA134AC2B3: uid=1000 from=<nick>

```

thanks in advance :)

---

### Post by MJN on 2009-03-08
Try the following:

1. Go to [http://www.thawte.com/roots/](http://www.thawte.com/roots/) and download Thawte's root CA certificates

2. Unzip the files with unzip <file.zip>

3. Convert the desired CA cert with [B]openssl x509 -inform der -in ThawtePremiumServerCA.cer -out ThawtePremiumServerCA.pem

[/B]4. (Easiest way) Append their certificate to the end of the file containing yours (referenced by your smtp_tls_cafile directive) e.g. **cat ThawtePremiumServerCA.pem >> yourfile.pem**
    or, (Neater way) create a file explicitly for CA certs (e.g. **cp ThawtePremiumServerCA.pem cacerts.pem**) and reference this with **smtp_tls_CAfile = cacerts.pem**

Note that Postfix is only warning about failed verification, it is still delivering the mail though.

Mathew

---

### Post by haximusprime on 2009-03-08
I did that, as per a tutorial I was reading, I did it as your #4, the easiest way.

Since it works, and I'm not running any sort of business or whatever, does it really matter that the verification isn't working? Is it best to just leave it alone?

thanks. :)

---

### Post by MJN on 2009-03-09
On a practical level I wouldn't worry about it. Certificate security services for SMTP are very rarely used (compared to the HTTP world) and, if anything, is often used only for the encryption aspect (and not authentication) which you've still got. Hence, you're not missing out on much - if anything.
 
Mathew

---


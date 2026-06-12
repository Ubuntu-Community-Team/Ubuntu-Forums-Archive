---
title: "Email Server SSL Certs installation StartSSL Postfix/Dovecot"
date: 2010-08-29
forum: Server Platforms
---

### Post by Lukas1 on 2010-08-29
Hi,
I have a Jaunty server set up that I built as an all in one email/webserver/etc. The email server has self signed certificates and because of that (I believe) some domains that I should be receiving mails from are not coming in. I currently do not have TLS or SSL set up and I think that if those are working that I will not miss emails anymore. I just signed up an account with StartSSL , which is a free CA Cert company online. I have a cert file, but I am confused on what to do with it now. It's a .p12 file but I think I can generate other file types through the control panel of StartSSL. Any suggestions? 

Thank you

Lukas

---

### Post by Bachstelze on 2010-08-29
> **Lukas1 said:**
> 
The email server has self signed certificates and because of that (I believe) some domains that I should be receiving mails from are not coming in.

Nope, that's not because of the self-signed certificate. E-mail largely predates SSL, so having any kind of SSL certificate is not a requisite for an email server.

---

### Post by Lukas1 on 2010-08-30
I understand that but then why would certain domains be unable to connect and deliver my mail? Most emails go through, but from what I can tell some people cannot send me mail from their corporate email accounts.

---

### Post by Bachstelze on 2010-08-30
> **Lukas1 said:**
> I understand that but then why would certain domains be unable to connect and deliver my mail? Most emails go through, but from what I can tell some people cannot send me mail from their corporate email accounts.

No idea, check your logs but it's definitely not because of the SSL certificate.

---

### Post by Lukas1 on 2010-09-01
I'd appreciate any other comments besides a one liner about how my idea won't work. Thank you

---

### Post by sh1ny on 2010-09-01
Paste some logs of emails that you are NOT receiving and you'll get some comments. Any actual configs displayed will also be nice. All in all Bachstelze here is right, you don't need commercial  ( or even startssl ) certificates to be able to receive emails. You can send/receive using the self-signed , self-generated certificates that come with any distro.

---

### Post by Lukas1 on 2010-09-09
OK, I'll try to see what I can get from my server this afternoon. I did notice some funny business last time I looked at my mail logs.

---

### Post by Lukas1 on 2010-09-10
Sep 10 22:08:14 bigdog deliver(bigdog): msgid=<20100910120206.8847947C063@mail.globalcapeesh.com>: save failed to INBOX: Internal error occurred. Refer to server log for more information. [2010-09-10 22:08:14]
Sep 10 22:08:14 bigdog postfix/local[3761]: 8847947C063: to=<bigdog@globalcapeesh.com>, orig_to=<root@globalcapeesh.com>, relay=local, delay=54368, delays=54364/4.4/0/0.04, dsn=4.3.0, status=deferred (temporary failure)

It looks like its running some messed up script


Sep 10 20:57:06 bigdog postfix/local[21957]: 07FEA47C054: to=<bigdog@globalcapeesh.com>, orig_to=<root@globalcapeesh.com>, relay=local, delay=378717, delays=378716/1.2/0/0.04, dsn=4.3.0, status=deferred (temporary failure)
Sep 10 20:57:06 bigdog postfix/local[21924]: 2F8A447C10C: to=<bigdog@globalcapeesh.com>, orig_to=<root>, relay=local, delay=128402, delays=128401/1.2/0/0.04, dsn=4.3.0, status=deferred (temporary failure)



Sep 10 20:57:05 bigdog deliver(bigdog): msgid=<20100909121704.38EDD47C199@mail.globalcapeesh.com>: save failed to INBOX: Internal error occurred. Refer to server log for more information. [2010-09-10 20:57:05]
Sep 10 20:57:05 bigdog postfix/local[21932]: 38EDD47C199: to=<bigdog@globalcapeesh.com>, orig_to=<root>, relay=local, delay=135601, delays=135601/0.24/0/0.02, dsn=4.3.0, status=deferred (temporary failure)
Sep 10 20:57:05 bigdog deliver(bigdog): mkdir(/home/bigdog/Maildir/cur) failed: Permission denied (euid=1000(bigdog) egid=1000(bigdog) missing +w perm: /home/bigdog)
Sep 10 20:57:05 bigdog deliver(bigdog): msgid=<20100909001704.005E947C10B@mail.globalcapeesh.com>: save failed to INBOX: Internal error occurred. Refer to server log for more information. [2010-09-10 20:57:05]



These are just examples from mail.log I don't know what to make of it. Thank you for your thoughts.

Lukas

---


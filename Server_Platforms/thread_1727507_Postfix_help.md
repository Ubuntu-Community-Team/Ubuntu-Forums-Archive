---
title: "Postfix help"
date: 2011-04-12
forum: Server Platforms
---

### Post by teaker1s on 2011-04-12
Have a sever running and can send plain unencrypted emails via wordpress, the link below doesn't seem to work correctly on maverick for encryption tls or ssl.

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Can anyone suggest a better more upto date link to get Encryption working please.

---

### Post by elico on 2011-04-13
i have a full ISPmail like config.
[http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)

what is the problem that you are having using the ubuntu manual?

---

### Post by teaker1s on 2011-04-13
Hi

Generate certificates to be used for TLS encryption and/or certificate Authentication:

```
touch smtpd.key
chmod 600 smtpd.key
openssl genrsa 1024 > smtpd.key
openssl req -new -key smtpd.key -x509 -days 3650 -out smtpd.crt # has prompts
openssl req -new -x509 -extensions v3_ca -keyout cakey.pem -out cacert.pem -days 3650 # has prompts
sudo mv smtpd.key /etc/ssl/private/
sudo mv smtpd.crt /etc/ssl/certs/
[B]sudo mv cakey.pem /etc/ssl/private/
sudo mv cacert.pem /etc/ssl/certs/[/B]
```

Are not found and instead of

```
250-STARTTLS
250-AUTH

```

mine responds

> 250-server1.example.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

When I try to send with encryption I get a socket error and no host from wordpress. Plain emails send fine so I believe it is the postfix guide on docs that needs updating.

Thanks

---

### Post by elico on 2011-04-13
and what is your main.cf file looks like?
this is the main reason.. cause the cert it-self seems to be ok.

you do get:
250-STARTTLS
so should be able to use tls.
just make sure you did the right setup on the client.
mine is
> 250-cccc.localdomain
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN


and this is what it supppose to do.

and this one is from and ISP
> 
250-mxout.XXXXXX
250-8BITMIME
250-PIPELINING
250-CHUNKING
250-DSN
250-ENHANCEDSTATUSCODES
250-HELP
250-XLOOP 1ACD1B852A0296B6927366303314E0F3
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=LOGIN PLAIN
250-ETRN
250-NO-SOLICITING
250 SIZE 5120000

---

### Post by teaker1s on 2011-04-14
Thanks for reply, things a bit hectic at the moment-I'll go through the guide you have posted and recheck when I get some quiet time in next few days.

:D

---

